---
title: "Can't get basic VNC functionality to work..."
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by sd_smoker on 2007-12-27
I want to VNC into one PC running Ubunty from another running XP, both in my LAN. I'm just using the built-in VNC server in Ubuntu (with no password). I tried logging in from XP using both VNC Viewer and TightVNC. When I tried it with my user logged in to Ubuntu I get an empty black screen. When I try it without a user logged in I just get a "connection failed" message. What am I missing here?

---

### Post by toddward on 2007-12-28
sd_smoker--

In Ubuntu, go to System -> Preferences -> Remote Desktop.

Under **Sharing**, make sure both check boxes are checked.

Under **Security** uncheck 'Ask you for confirmation'.

I'd suggest keeping a password.

---

### Post by sd_smoker on 2007-12-28
Thanks. It turned out it was a problem on my work computer. I disabled the built-in firewall that is part of my VPN client and it worked.

Regarding the password, is that important even if I don't ever enable port forwarding on my router? I only intend to use VNC over my LAN. My thinking is that if someone hacks through the router, I've got bigger problems than VNC.

Also, can anyone confirm that VNC only works when you are logged in to a desktop? Is there some way to have the server running even while I'm not logged into my desktop?

---

### Post by sd_smoker on 2007-12-28
One more question, is there a way to configure the VNC server to allow file transfers and/or clipboard transfer? They're both enabled in the client but they don't seem to work...

---

