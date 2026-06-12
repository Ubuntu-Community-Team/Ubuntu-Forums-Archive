---
title: "ATI x1300 Feisty fawn"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2007-04-21
Okay! So i´m all installed, ready to go. I used the Sticky in this forum and got into X just fine. Even has my nice, high resolution!
But no 3D. Ive looked around google and these forums,  and can´t really make heads or tails out of anything. 

So, how do I get acceleration to work? Link to a guide, or some such? Thank you much!

---

### Post by blitzer on 2007-04-21
Hello Taigrr,

Bad news:  Ati/AMD is not supporting are cards anymore** see below** I have the Radeon 9200SE card.  The last proprietary driver for us was 8.28 driver which Edgy Eft used well:KS .  With Xorg 7.2 in Feisty we are out of luck with ATI :mad: 

[http://https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8.html#179310]("http://https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8.html#179310")

> Minimum System Requirements

Before attempting to install the ATI Proprietary Linux driver, the following software must be installed:

    * XOrg 6.7, 6.8, 6.9, 7.0, or 7.1; XFree86 version 4.3
    * Linux kernel 2.4 or higher
    * glibc version 2.2 or 2.3
    * POSIX Shared Memory (/dev/shm) support is required for 3D applications


Good news is:  The Open Source Drivers have fairly good 3D support which is what you installed to out of the box in Feisty.  Like you I'm waiting for a tweek guide. As of right now i'm not getting the full resources out of my card (agp 1x instead of 4x).

I hope that the [COLOR="Red"]NEW Amd/Ati[/COLOR] will give us some candy with our new Feisty and Xorg 7.2  :lolflag:

---

### Post by Taigrr on 2007-04-21
Well that's lame. What are the chances of them actualy pulling through on building a driver for Xorg 7.2? =D

But, I found one thing.

fglrxinfo doesn't say anything about ATI to me!

joe@ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


I get a strong feeling that this isn't what I want it to tell me..  :-k

Any ideas on that?

---

### Post by Taigrr on 2007-04-21
Ran through a couple diffrent guides, but came up short.

"aticonfig --initial" and "aticonfig --overlay-type=Xv" many, many times, to no avail.

Is there something i'm missing? Or do I need to modify the Xorg.conf?

---

### Post by kfehr911 on 2007-04-24
I running a Ati Radeon9800 on Feisty.  You need to download a restricted driver.  I will drop a link. It will explain better and make you life easy.P.S.  Command can be easy Cut & Paste.Cheers
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

---

### Post by DMcCann87 on 2007-04-26
That link helped a lot!  I was able to get my VisionTek Radeon X1300 up and running 3d with no lag.  I know this is a newb question, but how do you check to see how well your vid card is performing?  I'm knew to linux, so right now I don't know a whole lot.

---

### Post by Taigrr on 2007-04-27
In addition to the above question, is there a way to turn off 3D in order to extend battery life when you're not plugged in?

Thanks alot. :)

---

### Post by chrisN_uk on 2007-05-07
OK, I'm having the same problem. I've followed the guide up to :

         edit /etc/X11/xorg.conf and replace the string "ati" with "fglrx" in the "Device" section

but the file says "vesa" not ati. I changed it anyway but upon running
 
          sudo aticonfig --overlay-type=Xv

I get: 

Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfd42a3d ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d0ff5b]
aticonfig[0x805bff7]
aticonfig[0x805c2a5]
.
. (lots of hex stuff)
.
bf9cb000-bf9e0000 rw-p bf9cb000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

Any idea whats going on?

---

### Post by xcalibur32 on 2007-07-08
same bug here....

---

