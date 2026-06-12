---
title: "Ubuntu 10.04: blank screen PowerMac G5 after installation"
date: 2011-05-28
forum: Apple Hardware Users
---

### Post by chatuser on 2011-05-28
I have installed Ubuntu 10.04 PPC on my PowerMac G5 dual 1.8 GHz using the alternate CD and after reboot the screen appears blank. The video card is a NVIDIA GeForce FX 5200 Ultra.

After reading tons of posts and documentation I have found the solution to this problem, perhaps it may be useful for another users.

1. install Ubuntu using the option install_powerpc64 at "boot:" prompt

2. after reboot, boot from Ubuntu CD using the option rescue_powerpc64 at "boot:" prompt

3. choose your root partition to exec a command shell

4. update the entire system using these commands:
aptitude update
aptitude safe-upgrade

5. install the nouveau driver:
aptitude install xserver-xorg-video-nouveau

6. execute this command:
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
([https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting))

7. create a /usr/lib/X11/xorg.conf.d/xorg.conf following these instructions:
[http://rfvsite.net/pages/ppc/ubuntug5.html](http://rfvsite.net/pages/ppc/ubuntug5.html)
- don't forget replace 'Driver "nouveau"' with 'Driver "nv"'
- if you replace 'Modes "1024x768"' with 'Modes "1280x1024"' you'll get a higher resolution

8. you also can use the xorg.conf file from [http://mac.linux.be/content/xorgconf-g5-ppc-tower](http://mac.linux.be/content/xorgconf-g5-ppc-tower) but replacing 'Driver "nouveau"' with 'Driver "nv"'

You can save some work if you install openssh-server before the step 4 and follow the rest of steps using a ssh session.

Comments are welcome.

[http://img196.imageshack.us/i/pantallazoxr.png/](http://img196.imageshack.us/i/pantallazoxr.png/)

---

### Post by gomaaz on 2011-05-29
Hi there,

after long long long loooooong lookup for this problem
I am suprised finding a suggest of solution for it

PowerPC G5 Tower 2,5 GHZ, Ati Radeon here.
I install with an alternate install CD so desktop CD doesn't work (-> black screen).

I'll try it today and tell you then



Finally, it could be the first time seeing linux on my G5
Would be so awesome!

Thanks in advance

---

### Post by jchandra on 2011-08-04
Thanks for this. I was having the same problem on a G5.

However, ran into a problem using the xorg.conf specified here [http://rfvsite.net/pages/ppc/ubuntug5.htm](http://rfvsite.net/pages/ppc/ubuntug5.htm). Fixed the blank screen, but color bit-depth was way low. 

Using the xorg.conf file in /etc/X11/ as specified [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting) solved it completely for me.

Thanks again!!

---

### Post by jap85 on 2011-11-23
I followed the instructions on my G5 with the ubuntu alternate install and it works but I don't get a GUI i get a command line log in, any suggestion on what I did wrong?

---

### Post by rsavage on 2011-11-24
Graphics "fixes" are very much dependant on what kind of graphics card you have.  If I had to guess then I'd probably say you have a radeon card?  See the relevant section in this post [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .

---

### Post by jap85 on 2012-04-19
its great to know there is a way to fix this, but after the install I removed the install CD, when I put it back in and restarted I can't get it to boot from the CD it just flashes on the screen and then takes me back to the initial boot screen where you pick linux or cd.  Any suggestions on how I get the install cd to work again or how I get into the prompt?

if it matters I installed 10.04 from the alternate install disk on a power mac G5 and followed all the basic instructions exc.

---

