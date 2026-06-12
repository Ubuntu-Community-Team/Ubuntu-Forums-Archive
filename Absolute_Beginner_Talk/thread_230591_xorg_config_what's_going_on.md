---
title: "xorg config what's going on???"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by griff01 on 2006-08-06
Hi

I'm new to linux - and persevering with the basic set-up of my laptop but can't afford to spend much more time on it...it's make or break this weekend and back to Windows this evening if I can't get this sorted.(I think the spirit of this forum is excellent and even if I don't get this to work I'll certainly be back in the future when I've got more time).

Problem:

I can't get my native screen resolution of 1280x768 to stick.

Did a dance of joy yesterday when, after running 915resolution and  

sudo dpkg-reconfigure xserver-xorg

1280x768 appeared on the drop down resolution menu. Used it all day but, when I booted up this morning I was back to 1024x768!

Why would that option appear, then be gone on the next startup?

Maybe it's something I've done with the 915resolution file? should I clean this out and start again? (if so how?) 

Any suggestions gratefully received.

Cheers

Griff

---

### Post by PingunZ on 2006-08-06
do ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
select with SPACEBAR
close with enter
reboot or restart X

---

### Post by griff01 on 2006-08-06
OK - here goes.....

---

### Post by griff01 on 2006-08-06
Nope - took me back to 1024x768

Bizarelley whilst waiting for a response to my original post I re-ran
sudo dpkg-reconfigure xserver-xorg

About half-way through it took me to a terminal type screen (with a script ending ...'tty' and a login prompt. THis timed out and went through to the Ubuntu log-in/ I then had the higher resolution.

Lost it again when I ran the sudo command you suggested.

All very bizarre!

Will try again and see what I get this time!!

Cheers

Griff

---

