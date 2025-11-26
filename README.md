# Smart Office Dashboard 🏢

A comprehensive conference room utilization and analytics platform built for **Dewey, Cheatham & Howe Law Firm**. This Next.js application demonstrates enterprise-grade IoT sensor data processing, real-time monitoring, and advanced analytics capabilities using Supabase as the backend.

For more information, please refer to the [FEATURES.md](FEATURES.md) file.

## 📋 Prerequisites

- **Node.js 18+**
- **npm/yarn/pnpm**
- **Supabase account** with project setup
- **Environment variables** (see configuration below)

## 🌊 pgflow Workflow Engine

This project includes [pgflow](https://pgflow.dev), a workflow engine for Supabase that helps with background jobs and queue processing. See [PGFLOW.md](./PGFLOW.md) for local development setup and examples.

## 🚀 Deploy Quick Start

### Step 1: Create a GitHub Repository

1. **Fork this repository** on GitHub [![Fork](https://img.shields.io/github/forks/supabase/smart-office-demo?style=social)](https://github.com/supabase/smart-office-demo/fork)

2. **Clone and Install your fork** locally:

   ```bash
   git clone https://github.com/YOUR_USERNAME/smart-office-demo.git
   cd smart-office-demo
   npm install
   ```

### Step 2: Create a Supabase project

1. **Go to [supabase.com](https://supabase.com)** and sign up/login
2. **Click "New Project"**
3. **Choose your organization** and enter project details
4. **Wait for the project to be created** (takes a few minutes)

### Step 3: Link and Deploy to Supabase

1. Do **Supabase Link** from your terminal:

   ```bash
   npx supabase link --project-ref YOUR_PROJECT_REF
   ```

> Find your project ref in the Supabase dashboard URL

2. **Environment Configuration**

   ```bash
   # Configure your Supabase project specific variables
   cp .env.example .env.local

   # add a functions .env.local file, add an OPENAI_API_KEY to it
   cp supabase/functions/.env.example supabase/functions/.env
   ```

3. Push **migrations and seed data**:

   ```bash
   npx supabase db push
   ```

### Step 4: Add vault secrets

In the SQL Editor of your project, run:

```sql
-- pg_net environment secrets
select vault.create_secret('https://[PROJECT-REF].supabase.co', 'supabase_url');
select vault.create_secret('[PROJECT-ANON-KEY]', 'supabase_anon_key');
```

### Step 5: Deploy Supabase Functions

1. Run in **your terminal** the following command:

```bash
npx supabase functions deploy
```

2. Deploy the **secrets** in your `.env` file

```bash
npx supabase secrets set --env-file supabase/functions/.env

```

### Step 6: Deploy to Vercel

1. Update your [next.config.ts](next.config.ts#L20) file to match your project ref:

```diff
- hostname: "jtaqjclnmyyfpsayscvl.supabase.co",
+ hostname: "[PROJECT-REF].supabase.co",
```

2. Go to **[vercel.com](https://vercel.com)** and sign up/login
3. Click **"New Project"**
4. **Import** your GitHub repository
5. Add these **Environment Variables**:

   ```bash
   NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
   SUPABASE_SERVICE_ROLE_KEY=your_service_role_key
   OPENAI_API_KEY=your_openai_api_key
   NEXT_PUBLIC_UNSPLASH_ACCESS_KEY=your_unsplash_access_key
   ```

6. Vercel will auto-detect Next.js - **click "Deploy"**

### Step 8: Generate demo data

1. Run the following command to **generate rooms, users, tickets and associated images**

   ```bash
   npm run generate:all
   ```

**That's it!** Your Smart Office Dashboard is now live on Vercel with a hosted Supabase backend.
For pgflow workflows in production, see [Deploy to Supabase.com](https://www.pgflow.dev/how-to/deploy-to-supabasecom/).

## 🤝 Contributing

1. Fork the repository [![Fork](https://img.shields.io/github/forks/supabase/smart-office-demo?style=social)](https://github.com/supabase/smart-office-demo/fork)
2. Create feature branches (`feature/analytics-enhancement`)
3. Follow TypeScript best practices
4. Add tests for new features
5. Submit pull request with detailed description

## 📄 License

MIT License - see LICENSE file for details

## 🏢 About Dewey, Cheatham & Howe

This application is built for the fictional law firm "Dewey, Cheatham & Howe," serving as a sophisticated demonstration of modern office technology solutions. The firm's 57 conference rooms across multiple floors provide an ideal scenario for showcasing enterprise-scale IoT monitoring and analytics capabilities.

---

**Built with ❤️ for enterprise IoT demonstrations**
**Showcasing: Next.js 15, Supabase, Analytics Buckets, Real-time Data Processing**
