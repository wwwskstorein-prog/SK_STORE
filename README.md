# SK STORE Website

A responsive Bengali/English website starter for SK STORE with:
- Mobile-friendly landing page and service cards
- Bengali ↔ English language switch
- Government updates section
- Age calculator, browser-based photo resize, typing/copy tool, external PDF tools link
- WhatsApp contact form
- Phone OTP login UI with Firebase Phone Authentication integration points
- Admin panel starter UI and local draft-saving example

## Important: what works immediately
Open `index.html` in a modern browser or deploy the folder to static hosting to preview the site. Service cards, language switch, age calculator, image resizing, copy tool and WhatsApp message form work without a database. The OTP login is intentionally disabled until Firebase is configured. The admin panel is a starter UI, not yet connected to a live database.

## Enable phone OTP
1. Create a Firebase project at https://console.firebase.google.com/
2. Add a Web App and copy its Firebase configuration.
3. Copy `firebase-config.example.js` to `firebase-config.js` and fill in the values.
4. In Firebase Console → Authentication → Sign-in method, enable **Phone**.
5. In Authentication settings, configure authorized domains for the hosting domain.
6. Serve/deploy the site over HTTPS (localhost is normally allowed for development). Do not rely on opening the file directly from disk for production auth.
7. Add SMS region policy / test phone numbers as appropriate in Firebase settings.

Firebase web config is designed to be public; never put service-account keys or other private server credentials in frontend files.

## Important admin security
The current admin UI deliberately does not grant admin access just because someone logged in with OTP. For a real admin panel:
- Use Firebase Admin SDK in a trusted server environment to assign a custom claim such as `admin: true` to the verified administrator UID.
- Check the ID token custom claim in the app.
- Protect Firestore/Storage with security rules that require `request.auth.token.admin == true`.
- Store updates/services in Firestore and implement read/write UI.
- Never secure admin access only by hiding a button or comparing a phone number in frontend JavaScript.

## Suggested deployment
For a quick static preview, GitHub Pages is free and simple. For this site with OTP and future Firestore features, Firebase Hosting is a practical fit. Use the official Firebase Hosting documentation: https://firebase.google.com/docs/hosting

## Customize before publishing
- WhatsApp number is currently set to `9732001899` (international link uses India country code 91).
- Location is set to Jalangi, Murshidabad, West Bengal.
- Replace sample government update cards with verified, current notices.
- Review the Aadhaar service wording so it only advertises services you are authorized to provide.
- Add privacy policy and terms before collecting any customer data.
- This project does not currently collect or save customer applications on a server.
