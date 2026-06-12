---
title: "any way to downgrade to 7.04?"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by 005david on 2007-11-17
srry, thread over, solved problem

---

### Post by SOULRiDER on 2007-11-17
I dont think theres any way of safely downgrading, the only way of doing so i can think of is changing the repos to the old ones but it will probably end in a disaster.

Why do you think its running much slower? Are you certain of this or you just feel like its slower?

---

### Post by 005david on 2007-11-17
youtube doesn't work, quicktime movies don't work...

firefox barely gets on the internet...


YES i'm sure it's slower, firefox used to be really fast, now i can only get on the internet with opera...

---

### Post by frank002 on 2007-11-17
If your problem is only Firefox, try disabling IPv6. I had the same problem. 
  Try this:
  gksudo gedit /etc/modprobe.d/aliases
  Find the line that reads alias net-pf-10 IPv6 and change it to 
   alias net-pf-10 off
   save and restart Firefox.

---

### Post by laidback on 2007-11-17
Read another POST the same as this, response was that there is no way back unless you have a backup of your 7.04.
I have installed 7.10 but have also kept my 7.04. I use hdd caddys so I'm able to swap hdds easily. I just keep a few old hdds that others throw out when they're upgrading. They don't need to be very large, 20Gb works really well. 
Isn't it annoying when an upgrade sets you back.

---

### Post by 005david on 2007-11-17
found and solved the problem.

i checked system monitor,
and had 100% cpu usage.  turned off about 100 sleeping tasks, and now it works like it did before i upgraded.

---

