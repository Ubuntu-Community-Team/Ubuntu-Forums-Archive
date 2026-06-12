---
title: "[SOLVED] Wicd and auto-login"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by SpongeBob SquarePants on 2008-04-08
Just a quick question. I currently use the bog standard "network manager" bundled with Ubuntu, and it works just fine. Obviously, the having to type in your password to access your network every time Ubuntu starts up is slightly annoying. So I was wondering. Does Wicd also prompt for a password on startup, when using the auto-login feature?

---

### Post by kpkeerthi on 2008-04-08
No. You need to just configure it with your wireless passkey and enable 'Auto-Login' under its 'Preferences' menu once. And add wicd to auto start at login.

---

### Post by SpongeBob SquarePants on 2008-04-08
> **kpkeerthi said:**
> No. You need to just configure it with your wireless passkey and enable 'Auto-Login' under its 'Preferences' menu once. And add wicd to auto start at login.

Thanks a lot. I might give that  a try this afternoon then. 

Much obliged to you.

---

### Post by keforex on 2008-05-08
Why is this marked as SOLVED? It's not. Wicd does not connect automatically when ubuntu 8.04 starts. I always have to go there and click on "connect" before I can browse the internet. Annoying!

---

### Post by keforex on 2008-05-08
Ok, NOW it's solved. I found out that on Wicd 1.4.2 you need to expand the Wired Network arrow button, put a check on "Use as Default Profile" and then go to Preferences and check the option "Use default profile on wired autoconnect". [SOLVED] Internet is alive at boot up.

---

