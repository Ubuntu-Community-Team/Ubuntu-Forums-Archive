---
title: "Problems signing in over VNC"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by nloding on 2008-01-20
I'm new to Linux and trying to remote into my Ubuntu box from XP.  I've enabled the remote desktop in the Preferences, and I can connect remotely from my Windows XP laptop just fine, but only if I've logged into the Ubuntu PC already.  I installed some updates and it told me to restart Ubuntu, so I did, and I was never able to log back in via VNC.  I had to go to the local workstation first, log in with that keyboard, then I was able to VNC in.

I have Googled and searched the forums but haven't found an answer: can this be fixed?  I assume the VNC service isn't starting until the user logs in; can it be started sooner so I can remote in regardless of whether the PC has been logged into before?

I understand the desktop "sessions" or whatever they're called -- my mind just went blank.  But I guess I don't understand why I can't sign with VNC without signing in locally first.  Like I said, I'm new to Linux and looking for some starter assistance.

---

### Post by nloding on 2008-01-21
Thought I might give this a bump ... I've still not found anything about VNC before logging in locally.  What am I missing?

---

### Post by nloding on 2008-01-21
OK, no one seems to be replying here, but I'm still out there researching.  A little more research and I found a line I apparently didn't read or didn't register my first time reading the help.ubuntu.com VNC article.  Can I only use a desktop session I haven't signed into locally yet with tightvncserver?  The default VNC server (vino) doesn't support this?

Tomorrow I will install and configure tightvncserver.  Am I on the right track at least?

---

### Post by stjeanl1 on 2008-01-23
Well, I'm trying to connect from my XP SP2 desktop to my Ubuntu 7.10 desktop using either VNC Viewer or TightVNC and the only way I can achieve this is by checking the "Ask you for confirmation" checkbox in Remote Desktop Preferences and yes, I need too be logged in as well to the desktop in order to VNC in.  

I'm new to linux as well and I think the Remote Desktop feature may not be like Windows Terminal Services.  Unless of course when you connect, you're connected at the console level instead of a terminal session.

I was looking at upgrading the version of VNC or something on the ubuntu desktop, maybe that would help...

Luc

---

### Post by nloding on 2008-01-24
I installed tightvncserver per the help.ubuntu.com article, and it works great, except the fonts and colors.  It's all kinds of messed up.  I'm going to go through the tutorial again in case I missed something.

stjeanl1 -- install tightvnc and configure it per this article: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)   I am able to log in without an active desktop session, but again, my colors and fonts are wrong, so ... I dunno.

---

### Post by stjeanl1 on 2008-01-24
Thanks, I'll look at it when I have a chace.

Thanks agian.

---

