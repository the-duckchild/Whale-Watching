# Whale Watching

Whale Watching is a full-stack application for recording and viewing whale sightings. It provides an ASP.NET API backend and a modern front-end UI, allowing users to submit reports, search sightings, and manage users via authentication and roles.

---

## Project Structure

- **API**: ASP.NET Core API located in `/api`  
  Handles backend logic, database, authentication/authorization, RESTful endpoints.
- **UI**: Frontend app located in `/ui`  
  Built with modern JavaScript tooling (e.g., React, Vite), it interacts with the API to provide a user-friendly interface.

---

## Getting Started

### 1. Clone the Repository

```sh
git clone https://github.com/the-duckchild/Whale-Watching.git
cd Whale-Watching
```

---

## API Setup

See detailed instructions in [api/README.md](api/README.md).  
Summary:

### a. Install Dependencies

```sh
cd api
dotnet restore
```

### b. Set Up the Database

- Create a PostgreSQL role called `whale_spotting` with password `whale_spotting` in pgAdmin.
  - Assign privileges: Can login, Create databases, Inherit rights from parent roles.
- Apply migrations:
  ```sh
  dotnet ef database update
  ```

### c. Authentication & Identity

- .NET Identity set up by default (roles: `User`, `Admin`).
- Initial admin and roles are seeded when the API runs.
- User model can be extended in `UserModel.cs`.
- Use `[Authorize]` attribute for endpoints needing authentication, and `[Authorize(Roles = "Admin")]` for admin access.

### d. Running & Checking Code

```sh
dotnet run
dotnet format               # Run linter
dotnet format --verify-no-changes  # Check code style without rewriting
```

---

## UI Setup

See detailed instructions in [ui/README.md](ui/README.md).  
Summary:

### a. Install Dependencies & Run App

```sh
cd ui
npm install
npm run dev
```

### b. NPM Scripts

- `npm run dev` — Run the UI in development mode
- `npm run lint` — Run the linter
- `npm run lint-fix` — Autofix lint issues
- `npm run test` — Run tests

### c. Using the Location API (GeoNames)

- Create a [GeoNames](https://www.geonames.org) account, confirm via email.
- Enable free web services in your account settings.
- Add a `.env` file to `ui`:
  ```
  VITE_GEONAMES_USERNAMES="yourUserName"
  ```

---

## Contributing

Contributions are welcome! Please open issues or submit PRs for improvements, bugfixes, or new features.

---

## License

[MIT](LICENSE) (or your actual license here)

---

## Additional Resources

- [API Documentation](api/README.md)
- [UI Documentation](ui/README.md)
