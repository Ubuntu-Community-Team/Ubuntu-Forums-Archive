---
title: "mailserver"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Charlietje on 2007-07-10
hello,

I have several computers at home. An old one i want to use as a mailserver because i want to be able to see my mail on the different pc's.

I read the HOWTO to setup a mailserver, but they all use a domain. And I don't use a domain at home.

I just want that the old pc checks the mail on my ISP mailbox, and that I can see my mailbox via IMAP on my different pc's

Can someone help me?


Carl

---

### Post by TwistedLincoln on 2007-07-10
I was working on something similar for a while, but I never figured it out.

My thought was that I could use a POP3 client to retrieve the mail from the ISP, and then use Dovecot (an IMAP) server to serve it out over my local network.  Never did get around to actually trying it, however.

You can run a domain on your local lan without having an internet domain.   By default, I think Ubuntu uses "localdomain."  Not sure, though.

Anyway, I ended up just moving my website to a hosting provider that used IMAP, and now I just check my email on each of my machines directly using IMAP, and everything stays in sync.

That of course won't work if your ISP doesn't offer IMAP support, which most don't...

---

### Post by Charlietje on 2007-07-11
That is exactly what i want.
The local domain is an issue cause i also have XP home running that cannot login to a domain.

So... any help is welcome

Charlietje

---

### Post by kuhsay on 2007-09-27
Did you ever get this working?  I am interested in doing the same thing.

---

