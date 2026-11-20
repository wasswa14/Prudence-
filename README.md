# PRUDENCE — Records & Document Management

A responsive web application starter for registering, searching, updating and retrieving organisational records and attached documents. New accounts request access and wait for administrator approval.

## Important: online setup is required
This folder is the website source code. It is not yet published on the internet and will not save shared online data until you connect a Supabase project and deploy it.

## 1. Create the online database
1. Create a project at https://supabase.com/
2. Open **SQL Editor** in the project.
3. Open `supabase_setup.sql`, copy all its contents and run it.
4. In Supabase, open **Project Settings → API**. Copy the Project URL and the `anon` / publishable key.
5. Open `config.js` and replace the two placeholder values. Do not use a `service_role` or secret key in browser code.

## 2. Create the first administrator
1. Deploy the site (step 3), then open it and submit the registration form using the administrator's email.
2. In Supabase → SQL Editor, run the final commented statement in `supabase_setup.sql`, replacing `YOUR_EMAIL_ADDRESS` with that exact email:
   `update public.profiles set role='admin', approved=true where email='YOUR_EMAIL_ADDRESS';`
3. Sign in again. The administrator can approve later staff requests in **User approvals**.

## 3. Publish the website
1. Create an account at https://vercel.com/ or https://netlify.com/
2. Upload/deploy the contents of this folder as a static site, or put the folder in a GitHub repository and import it.
3. Use the deployed website address to access Prudence from phones and computers.

## Included
- Responsive dashboard and records list
- Registration and login using Supabase Auth
- Pending-account approval workflow
- Record create, search, view and update
- Private file uploads and time-limited download links
- Active, semi-active and archived status
- Basic dashboard counts

## Security and records-management notes
- The Supabase database policies restrict access to approved accounts.
- The file bucket is private; file links are signed and expire after five minutes.
- Keep the Supabase project URL and anon/publishable key in `config.js`; never expose a service-role key.
- Use strong passwords, enable MFA for administrators, and configure regular database backups.
- Before using real confidential, personnel, financial, legal or sensitive records, have the deployment and access policies reviewed by a qualified administrator/security professional. Add audit logging, retention schedules, version history and tested disaster recovery before production use.
- This starter does not yet provide a full immutable audit trail, bulk import, OCR, version control, or automatic retention/disposal. These should be added before treating it as a production records-management system.
