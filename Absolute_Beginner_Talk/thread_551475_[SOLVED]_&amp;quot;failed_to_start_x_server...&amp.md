---
title: "[SOLVED] &amp;quot;failed to start x server...&amp;quot;"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by gbc65 on 2007-09-14
is this the right place to post issues? if so here i go... 
my machine specs (follow the link)[http://209.167.114.38/support/TechSupport/productcontents/satellite/PSPA3C-JR500E.htm](http://209.167.114.38/support/TechSupport/productcontents/satellite/PSPA3C-JR500E.htm) 
dl'd ubuntu 1.4 , burned to disc, ran live disc- no problem, played with it and decided to install it.
 
now the problem: upon rebooting the freshly installed os i get the dreaded "failed to start x server...". now i'm not new to forums, i know how to use the search function, but every solution to this problem says "run the command sudo dpkg-reconfigure -phigh xserver-xorg after login, then you should get the blue screen and follow the commands."
 
well i just get a prompt exactly like the one i typed the sudo dpk... command.
 
so, does anyone know how i can get past this? 
 
tia
gbc65

---

### Post by PriceChild on 2007-09-15
*moves and bumps*

Well all you should do afterwards is restart the x server:
```
sudo /etc/init.d/gdm restart
```

---

### Post by gbc65 on 2007-09-16
thanks Pricechild.
 
now i need to be pointed to a good tutorial on this linux stuff, 'cause there is no way i would have known to look for that as a solution. where does it say xserver can be started by telling gdm to restart??!!?( this question is rhetorical, i'll have searched this out and answered it.)
 
 
one down, untold #'s to go.
 next: same machine no sound. checked all the volume settings for any mutes, under system\preference\sound devices are all auto detect, except default mixer tracks it has my sound card identified. all tests just hang( and no sound)
 
once again, tia
gbc65

---

### Post by dwhitney67 on 2007-09-16
Please run the following command from a terminal and post the results.  That way we can all know what type of sound card you have!

[FONT="Courier New"]$ lspci[/FONT]

---

### Post by Crafty Kisses on 2007-09-16
> **gbc65 said:**
> is this the right place to post issues? if so here i go... 
my machine specs (follow the link)[http://209.167.114.38/support/TechSupport/productcontents/satellite/PSPA3C-JR500E.htm](http://209.167.114.38/support/TechSupport/productcontents/satellite/PSPA3C-JR500E.htm) 
dl'd ubuntu 1.4 , burned to disc, ran live disc- no problem, played with it and decided to install it.
 
now the problem: upon rebooting the freshly installed os i get the dreaded "failed to start x server...". now i'm not new to forums, i know how to use the search function, but every solution to this problem says "run the command sudo dpkg-reconfigure -phigh xserver-xorg after login, then you should get the blue screen and follow the commands."
 
well i just get a prompt exactly like the one i typed the sudo dpk... command.
 
so, does anyone know how i can get past this? 
 
tia
gbc65

You'd probably have to reconfigure your X server.

---

### Post by gbc65 on 2007-09-16
Dwhitney67: this is what i get
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

``` 
also the specs of my laptop are in the link in my first post of this thread( if that would help you help me!)

Codename:
> You'd probably have to reconfigure your X server.
right now that is like telling me to find a cure for cancer to fix my cough.
i know enough to know that i DON'T KNOW enough to fix this myself. what i need is not only the solution, but also to be told where to get instruction on how to implement the solution.

thanks and appreciation for your responses
gbc65

---

### Post by DM was on fire! on 2007-09-16
**sudo dpkg-reconfigure xserver**

...I think. XD
All you need to know after that is stuff about your hardware. :)

---

### Post by Jawsman on 2007-09-16
I had the same problem with Serverx, and dint' realize I had to restart it... I was trying different things from 2:00am to 3:00am until I surrendered and went to sleep... Now, I woke up and it was all functioning perfectly!

(note: I had also run dpkg-reconfigure -phigh xserver-xorg thing)

---

### Post by dwhitney67 on 2007-09-16
> **gbc65 said:**
> Dwhitney67: this is what i get
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

``` 

It's very odd that your audio device is not working.  I have a Dell Inpiron E1505 with the same audio chip-set (although mine is rev 01) and it works fine.  It is my understanding that you are running Ubuntu 7.04.  Is that correct?

By the way, I am running the Linux Kernel 2.6.20-16-generic, which provides the drivers for the Intel audio chip-set.

You can compare this version with yours by running:

[FONT="Courier New"]$ uname -r[/FONT]

---

### Post by gbc65 on 2007-09-16
Dwhitney67: 
the same linux kernel is running on my machine.
i am running ubuntu ultimate 1.4 ( with the upgrade)
 
i will attempt again to check all my volume controls to eliminate a possible blonde moment! and search the forums, once again for any similar sound issues.
 
thanks for hanging in there on this one!
 
Jawsman:
i experienced the same thing, although i didn't hang in there THAT long.
 
gbc65

---

### Post by gbc65 on 2007-09-17
just an update. i found thread  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
i believe i followed all the steps, but still no sound. there must be something so basic that i'm missing. i'm giving up for the night.
gbc65

---

### Post by corevette on 2007-09-17
For the record, the next version of Ubuntu (Gutsy Gibbon) features a bullet proof X-server
So eventually the crashes will disappear
[https://wiki.ubuntu.com/BulletProofX](https://wiki.ubuntu.com/BulletProofX)

---

### Post by dwhitney67 on 2007-09-17
> **gbc65 said:**
> just an update. i found thread  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
i believe i followed all the steps, but still no sound. there must be something so basic that i'm missing. i'm giving up for the night.
gbc65

I keep on seeing folks reply to your original X-server problem, which I believe you have resolved.  I think you will get greater exposure (and help) for the issue you are having with the audio device if you create a new thread.

Btw, don't forget to set this thread to "SOLVED" if you decide heed my suggestion.  Select "**Thread Tools -> Solved**" (or something similar to that.)

---

