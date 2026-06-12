---
title: "no users set up... so I can't log in"
date: 2010-08-13
forum: Apple Hardware Users
---

### Post by sherbert on 2010-08-13
I installed ubuntu on a G3 iBook using this guide: [http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal) (because its a slow a** laptop).

But anyway, here's the effed up thing... I'm almost certain that it never ever prompted me to set up a username or password. I'm almost certain because I've installed linux on a good number of different systems and I use the same exact username and password every time. But I was kind of shocked when it prompted me for a login and password and I'm thinking to myself "uhhhhh.... I didn't set up a user yet...". So I tried my usual login and nope... "Login incorrect". 

I can't do anything because I'm not logged in... and I can't use recovery mode either because its PPC or because its a Mac so there is no GRUB. 

So what can I do?

---

### Post by JustinR on 2010-08-13
You could use a Live-CD to see if there are any users in the /home directory.

You could then 'chroot' into the Ubuntu-Minimal install and add a new user.

---

### Post by sherbert on 2010-08-13
Figured it out upon some research and some issues I had before that I forgot about. I did create a user, but because of some weird thing with the system clock being off it doesn't recognize any users. So I had to go into Open Firmware, correct the time and date, and then reinstall ubuntu.

---

### Post by linuxopjemac on 2010-08-13
set the time with ntp, then you don't have that problem anymore. It has to do with a dead PRAM battery.

---

