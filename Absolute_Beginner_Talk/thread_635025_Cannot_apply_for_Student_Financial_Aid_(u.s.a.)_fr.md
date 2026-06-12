---
title: "Cannot apply for Student Financial Aid (u.s.a.) from Linux?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Unstuck on 2007-12-08
A friend just tried applying for Financial Aid on the FAFSA website; after several failed attempts to log in, she called them for advice and was told she cannot log in from a Linux machine.  This makes no sense to me, and sounds like a line from someone who is trying to get their customer off the phone.  Has anyone else encountered this problem on FAFSA?

---

### Post by PmDematagoda on 2007-12-08
Why don't you ask your friend to try using the [User Agent Switcher for Firefox]("https://addons.mozilla.org/en-US/firefox/addon/59") or [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page")?

---

### Post by Unstuck on 2007-12-08
Thank you very much, User Switch Agent allowed us to work around the problem.

[Here]("http://www.fafsa.ed.gov/FOTWWebApp/beforebrowser_req.jsp?APPTYPE=F") are the site's requirements.  Any idea why Firefox 2.0.11 didn't work?

---

### Post by niteshifter on 2007-12-08
> Any idea why Firefox 2.0.11 didn't work?

Part of M$ plan of Global World Domination. :twisted:

Ok, seriously: When a web browser (aka "client") connects to a web server before the requested file is sent to the client there's a handshake-like process. What moves from client to server is a package of info called the HTTP Reqest Header which contains, among other things, a string of text that identifies the browser type and the client's OS. That string of text is what the FF User Agent Switcher modified for you.

---

