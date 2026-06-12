---
title: "Another Noob, What is &quot;~$&quot; Please help!"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by klcm0102 on 2006-07-01
I'd love to try Ubuntu, and I have burned several copies and verified the burns, yet after installation Ubuntu will not fire up.
I installed it on a Dell Inspiron 1000 with 512 mg ram, 30 gb hd. No problems during install other than it didn't like my wireless network, but upon attempting to load I get as far as entering my username & password then I get a command prompt with "myusername@ubuntu:~$"
What the heck is that?
Is this OS not made for laptops? I'd really love to learn this so I can ditch windows!

---

### Post by %hMa@?b&lt;C on 2006-07-01
sudo dpkg-reconfigure xserver-xorg
choose the right driver (ati card, ATI driver, nVIDIA card, VESA driver)

---

### Post by AirRaven on 2006-07-01
[QUOTE=klcm0102]I'd love to try Ubuntu, and I have burned several copies and verified the burns, yet after installation Ubuntu will not fire up.
I installed it on a Dell Inspiron 1000 with 512 mg ram, 30 gb hd. No problems during install other than it didn't like my wireless network, but upon attempting to load I get as far as entering my username & password then I get a command prompt with "myusername@ubuntu:~$"
What the heck is that?
Is this OS not made for laptops? I'd really love to learn this so I can ditch windows![/QUOTE]
It's just booted you into the command prompt for some bizarre reason.

Are you sure you did the correct install? The desktop install- not the server install.

Did you get the right Install CD?

In any case, try typing "sudo gdm".

---

### Post by stychman on 2006-07-01
My guess is that you downloaded the server install not the desktop install.  The server install does not give you any kind of graphical interface.  I started a thread [here]("http://www.ubuntuforums.org/showthread.php?t=206782") about how to get to a graphical interface after doing a server install. A lot of people have done this.

---

