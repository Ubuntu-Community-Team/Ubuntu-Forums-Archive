---
title: "Hotmail on Thunderbird"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by M4v3r1ck on 2007-04-11
So...I've been trying to get hotmail to work on thunderbird. I've downloaded the 2 extensions from webmail.mozdev.org (The webmail Web-Mail-1.0.17; and the hotmail extension Hotmail-1.0.23). Recreated my account using my entire e-mail address as the username and using 127.0.0.1 for the incoming/outgoing server and entered my pass upon being prompted. I came up with:

Sending of password did not succeed. Mail server 127.0.0.1 responded: Hotmail said you must pay money to have WebDAV access.

Anyone know what I'm doing wrong or how to get around that?
~M4v

EDIT: Getting same results on Evolution.

---

### Post by lamalex on 2007-04-11
It's what it sounds like, hotmail makes you pay. ditch it, switch to gmail. It's a better mail interface and google doesn't try to screw you every chance it gets. Email all your friends, say you're at gmail, and see if you can set up a redirect at hotmail. That's my advice at least :)

---

### Post by M4v3r1ck on 2007-04-11
Ah...Too bad...It's not for me though, I wouldn't mind the switch too much, but it's for someone else. Long story short, he won't switch his e-mail address. That and I just wanted to see if I could do it, and when I couldn't, I thought I'd check here. lol Thanx anyways.

---

### Post by msak007 on 2007-04-11
When I was using Thunderbird a year ago, I used to have problems frequently using the WebMail extension. It worked great when it worked, but sometimes Microsoft changed some things around and it stopped working for a couple of days until the extension got updated. I think the error you're getting indicates some sort of setup problem within the extension itself (there were several modes to select from if I recall correctly). But I've since switched to KMail (part of Kontact, I use KDE) and there were no extensions for webmail / Hotmail. I found something even better, an app called **Hotway** that runs as a service in the background - less bloat (no extra extensions to slow down Thunderbird), faster, and runs reliably. Here's a page on setting it up through Evolution (Gnome's email client), but the instructions should be the same for Thunderbird:

[http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

---

### Post by M4v3r1ck on 2007-04-11
Yeah...I already did all that. Unfortunately. And I got that same error message in Evolution...

---

### Post by msak007 on 2007-04-11
> **M4v3r1ck said:**
> Yeah...I already did all that. Unfortunately. And I got that same error message in Evolution...
Sorry, didn't know you already tried Hotway you only mentioned the Thunderbird extensions. According to some of the comments on [this]("http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html") page, it could be either due to password length (too long) or the account is too new to be accessible this way. I've had mine since the mid 90's and I've never gotten that error. I only use it when signing up for things online and such when I know I'll get junk mail though. I've since switched to GMail for my main email account and it's much easier because they allow POP access.

---

### Post by M4v3r1ck on 2007-04-11
Man...The only thing I noticed I didn't try was edit the /etc/hosts.allow file. And after that it still didn't work. The account has been active for 2-3 years and the pass is already less than 8 characters. : / Oh well. Thanx anyways though. Definately worth the shot and learning experience.

---

