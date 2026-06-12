---
title: "Best way to Remote Desktop?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Oen386 on 2007-03-12
I have figured out how to enable remote desktop, and how to connect. I am concerned about other people trying to access my remote desktop or sniff packets.

What would be the best way to secure my connection and my desktop from most attacks?

Thanks.

---

### Post by steveneddy on 2007-03-12
Turn your computer off, disconnect it from the internet and never tell anyone about this conversation.

---

### Post by Oen386 on 2007-03-12
Lol

---

### Post by Ek0nomik on 2007-03-12
I haven't dabbled around with remotely controlling Ubutu.  Not yet at least.

I know with Windows VNC programs you can specify that only specific IP or IP Ranges can connect to your session.  I would look for something like that.

---

### Post by houstonbofh on 2007-03-12
Well, first which remote desktop?  If you enabled SSH with X tunneling, install fail2ban.  If it is VNC, stop the service, install SSH and fail2ban, and SSH in to start the service. :)  You also may be able to tweak fail2ban to work with VNC failures.  You could also enable VPN on your router, and not worry as much.

---

### Post by Oen386 on 2007-03-13
I wanted to use the built in Remote Desktop application, but I wanted to enable SSH on it or something. When I read about it, it was implied that the built in application does not have any form of encryption.

---

### Post by houstonbofh on 2007-03-17
This is a bit vague.  Perhaps if you tell us what you want to do, not just how you want to do it.

---

