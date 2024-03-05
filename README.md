This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.


# App folder Routing

`app->(auth)` This is a `Routing Group for login and signup`.

`app->(root)` This too is routing group for `credits` , `profile`, `transformation`.

`app->transformation->[id]->update`  is a `Dynamic routing to go to the update page`. This means user with specific `id` can go to the update page and which is independent for other user.

`app->transformation->add->[type]` to go to addTransformationType page


## Used Clerk for user Authentication and Authorization
```bash
Install @clerk/nextjs

Set up your environment keys

Wrap your Next.js app in <ClerkProvider />

Limit access to authenticated users

Specify which routes are publicly accessible

Enable users to manage their session with <UserButton />
```


## Sidebar Components

div tag containing 

1. Link tag to Image/ logo with the link to go the `/`

2. nav tag which renders only when the use is `signedIn` this property is checked by `CLERK <SignedIn>`

    a. map over nav items via `navLinks` which is constants declared and figure out that is the current link which we are on `const isActive = link.route === pathname;`

    b. 1st ul which map on navLinks form 0-6 and 2nd ul which maps on navLinks 6-last at the end included `<UserButton afterSignOutUrl='/' showName />` from CLERK for user information and SignOut

## Lib-Action

1. user.action.ts
 
    a. its an server component

    b. Create function - (i) call for database connect.Coz the connection of DB does not persist so we have to call each an every time when we need it.Like in this case create user. But due to caching technique next time when we call for the create user it take it from the cache.

    (ii) we call User model on which we call .create method which takes user data coming from frontend.

    b. Read function - (i) call User model on which we call findOne which is a method from mongoose which check the clerkId as userId if user id is found then its reads or else throw error.


## Lib-Utils.ts file

Handles the error where it takes the error and show appropriately the error in the console log and also where it is coming from.


## types -> index.d.ts
it contains the type that what we need to provide while creating params

