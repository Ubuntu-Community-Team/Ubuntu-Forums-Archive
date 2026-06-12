---
title: "Problem with X-Server"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Natsuko640 on 2007-06-24
Okay, I've been using Xubuntu for a few months now and recently I upgraded to Feisty Fawn. Everything was fine until this morning when X-Server was disabled and I was forced to log in though Terminal. Throughout the day I checked the forum and have tried everything I've seen but it still doesn't work. Right now the output is saying,

"Fatal server error:
xf86MapVidMem: Could not mmap framebuffer (0xf0000000 ,0x0) (Invalid argument)"

I've already gone through and tried "sudo dpkg-reconfigure -phigh xserver-xorg" and restarting GDM but I still have the same problem.

Any suggestions on how to fix it?

---

### Post by Crafty Kisses on 2007-06-25
> **Natsuko640 said:**
> Okay, I've been using Xubuntu for a few months now and recently I upgraded to Feisty Fawn. Everything was fine until this morning when X-Server was disabled and I was forced to log in though Terminal. Throughout the day I checked the forum and have tried everything I've seen but it still doesn't work. Right now the output is saying,

"Fatal server error:
xf86MapVidMem: Could not mmap framebuffer (0xf0000000 ,0x0) (Invalid argument)"

I've already gone through and tried "sudo dpkg-reconfigure -phigh xserver-xorg" and restarting GDM but I still have the same problem.

Any suggestions on how to fix it?
Hmmm. this is weird, what are your specs?

---

### Post by Natsuko640 on 2007-06-25
It's an old HP Pavilion zv5201us with 192MB of RAM, 30GB HDD, Intel Celeron and (from what the sticker says) ATI mibility 9000IGP. I think that should be right.

---

### Post by Natsuko640 on 2007-06-25
I think I narrowed it down to being "/dev/input" is missing. Is there any way for me to get it back?

---

