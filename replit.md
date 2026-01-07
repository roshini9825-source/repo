# Lumina Media

## Overview

Lumina Media is a modern web application for discovering and searching audio, video, and images across multiple languages. The platform features an AI-powered video generation capability and a sleek dark-themed user interface built with React and shadcn/ui components.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React with TypeScript, using Vite as the build tool
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack React Query for server state and caching
- **UI Components**: shadcn/ui component library built on Radix UI primitives
- **Styling**: Tailwind CSS with custom dark theme configuration and CSS variables
- **Animations**: Framer Motion for smooth UI transitions

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ESM modules
- **API Design**: RESTful endpoints under `/api/*` prefix
- **Development**: Vite dev server with HMR integration for seamless development

### Data Storage
- **Database**: PostgreSQL with Drizzle ORM
- **Schema Location**: `shared/schema.ts` contains all table definitions
- **Migrations**: Drizzle Kit for schema migrations (`drizzle-kit push`)
- **Connection**: Uses `DATABASE_URL` environment variable

### Database Schema
- **users**: User accounts with id, username, and password
- **media**: Content items with title, artist, type (audio/video/image), URL, thumbnail, duration, language, and views
- **settings**: User preferences for audio quality, video quality, and enhancement options

### Project Structure
```
├── client/           # Frontend React application
│   ├── src/
│   │   ├── components/  # React components including shadcn/ui
│   │   ├── pages/       # Page components (Home, not-found)
│   │   ├── hooks/       # Custom React hooks
│   │   └── lib/         # Utilities, API functions, query client
├── server/           # Backend Express application
│   ├── routes.ts     # API route definitions
│   ├── storage.ts    # Database operations layer
│   └── db.ts         # Database connection
├── shared/           # Shared code between frontend and backend
│   └── schema.ts     # Drizzle schema definitions with Zod validation
```

### Build System
- **Development**: `npm run dev` runs Express server with Vite middleware
- **Production Build**: Custom build script bundles server with esbuild and client with Vite
- **Output**: Production files go to `dist/` directory

## External Dependencies

### Database
- **PostgreSQL**: Primary database, requires `DATABASE_URL` environment variable
- **connect-pg-simple**: Session storage in PostgreSQL

### UI Framework
- **Radix UI**: Accessible component primitives (dialog, dropdown, tabs, etc.)
- **shadcn/ui**: Pre-styled component library using Radix primitives
- **Lucide React**: Icon library

### Development Tools
- **Vite**: Frontend build tool with HMR
- **Drizzle Kit**: Database migration tooling
- **TypeScript**: Type checking across the entire codebase

### Validation
- **Zod**: Schema validation for API requests
- **drizzle-zod**: Generates Zod schemas from Drizzle table definitions