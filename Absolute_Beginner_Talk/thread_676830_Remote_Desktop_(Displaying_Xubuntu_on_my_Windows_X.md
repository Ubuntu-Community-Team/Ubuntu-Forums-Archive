---
title: "Remote Desktop (Displaying Xubuntu on my Windows XP PC.)"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by erapcla on 2008-01-24
Hi

I've just installed Xubuntu 7.10 on my ancient PC. A Dell Pentium II 133 MHz and 192MB RAM memory.
That works quite nicely and alot better than Windows XP did on that old machine.
Initially I tried to install Ubuntu, but it looked like my machine was too slow for Unbutu. So I had to settle for Xubuntu.

I would like to do the following:
Display the desktop of the Xubuntu machine on my Windows XP machine. The two machines are on the same LAN so there will be no issues with security tunnelling (via SSH) or opening any ports on my router.
I saw when I tried to get Ubuntu running (and on a few threads in this forum) that was a way on getting "Remote Desktop" started on the Xubuntu machine. Applications -> Accesories -> Remote Desktop if I remember right. However noting on the in Xubuntu.

What I woulk like help with:
What SW do I need to install on the Xubuntu machine?
Is the 192MB Ram enough to run Xubuntu, Remote Desktop and some light applications on? 
Do I need to install any SW on the Windows XP machine or is it enough with the Windows Remote Desktop SW that already exists?
 
Regards
Patrik

---

### Post by njparton on 2008-01-24
gnome (ubuntu) comes with an inbuilt vnc server called vino. I'm assuming that xcfe (xubnutu) doesn't come with anything similar.

Install vnc4server from the repositories and search for a how to to set it up.

Then install a vnc client in windows (I can recommend "xming" - google it) and configure it to connect to vnc4server (really easy).

If you're connecting via a router, remember to forward port 5900 to your xubuntu PC.

---

