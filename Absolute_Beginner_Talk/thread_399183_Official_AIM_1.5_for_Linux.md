---
title: "Official AIM 1.5 for Linux"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Warpnow on 2007-04-02
brinson@brinson-desktop:/usr/local/bin$ ./aim
./aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
brinson@brinson-desktop:/usr/local/bin$  

When I try and load aim 1.5 for linux I get that...How can I fix it?

I was surprised AIM made an official version for linux. I'd prefer use it over GAIM because of their new phoneline feature.

Link to the site:
[http://www.aim.com/get_aim/linux/latest_linux.adp](http://www.aim.com/get_aim/linux/latest_linux.adp)

Anyone gotten this software working?

---

### Post by jfinkels on 2007-04-02
> **Warpnow said:**
> brinson@brinson-desktop:/usr/local/bin$ ./aim
./aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
brinson@brinson-desktop:/usr/local/bin$  

When I try and load aim 1.5 for linux I get that...How can I fix it?

I was surprised AIM made an official version for linux. I'd prefer use it over GAIM because of their new phoneline feature.

Link to the site:
[http://www.aim.com/get_aim/linux/latest_linux.adp](http://www.aim.com/get_aim/linux/latest_linux.adp)

Anyone gotten this software working?

from their FAQ
  
Q: Sometimes when I try and run AIM, AIM crashes. What should I do?
A: When you run AIM, it looks for the library libstdc++-lib6.1-1.so.2. However, the latest Debian version doesn't come with this file by default, it comes with a newer version. You need to softlinking the new file to the old filename though: ln -s /usr/lib/libstdc++-libc6.1-2.so.3 /usr/lib/libstdc++-libc6.1-1.so.2

---

### Post by rabid9797 on 2007-04-02
honestly, i wouldn't even try using aim for linux, its just such a bad program, almost no effort was put into making 1.5 for linux..i'd switch to GAIM tbh

---

### Post by jfinkels on 2007-04-02
Yep gaim is what I do. Plus if you want VoIP functionality, check out Ekiga softphone, which ships with Ubuntu! Just type *ekiga* in the terminal and you're off!

---

### Post by Warpnow on 2007-04-02
Thanks. Hah, I feel stupid. Should have read the FAQ. Though it seems that ubuntu uses 6.2-2, rather than 6.1-2, so I did:

sudo ln -s /usr/lib/libstdc++-libc6.2-2.so.3 /usr/lib/libstdc++-libc6.1-1.so.2

and it worked. heh. Linux is so exciting (Like my third day on it).

AIm offers you a free LOCAL phone number, though. Its awesome. with Ekiga all my friends would have to talk to me long distance or I'd have to pay.

---

### Post by BinaryMadman on 2007-08-08
Warpnow, how were you about to get it to work?  In other words, what installer version did you use (Debian 3+, All other OS)?  Also, did the Linux version come with AIM Phoneline afterall?  That's the main reason i would need it for, otherwise i'd just use Gaim - but Gaim/Pidgin doesn't have that feature.

---

