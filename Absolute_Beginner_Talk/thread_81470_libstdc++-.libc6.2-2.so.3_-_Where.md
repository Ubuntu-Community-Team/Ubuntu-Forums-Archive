---
title: "libstdc++-.libc6.2-2.so.3 - Where?"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by zhorty on 2005-10-24
Hello.
I'm trying to set up a VNC server, and when i'm doing ./vncserver and the syntaxes, I get this error:

vncserver: error while loading shared libraries: **libstdc++-.libc6.2-2.so.3**: cannot open shared object file: No such file or directory

So, where can I get this file, or any other solutions to fix this? I've used google, forum search function, alot of libstdc packages with apt-get, and I can't get it working. Still the same error.

I need help as soon as possible, please :)

Thanks
- Fredrik.

---

### Post by Kyral on 2005-10-24
GNOME has one built in

System -> Preferences -> Remote Desktop

---

### Post by zhorty on 2005-10-24
Aaahh, finnaly! Thanks dude.

I actually knew it, but I didn't tryed so much with the built in one.

Thanks again :)

---

### Post by JD11 on 2005-11-29
Im having similar problems to this - im trying to set my vnc password and i get the same message.  I have enabled remote desktop from the menu but it doesn't make any difference.

Any help would be appriciated!

---

### Post by adam.mech09 on 2006-03-10
I'm having the same problem, with the same error, but when trying to run a KVM program, Synergy.  

Can anybody help?

-adam

---

### Post by souki on 2006-03-20
you have to install libstdc++2.10-glibc2.2
this will install the missing library

see this thread [http://ubuntuforums.org/showthread.php?t=62629](http://ubuntuforums.org/showthread.php?t=62629)

---

