---
title: "Live CD blank screen or failed X server on laptop with ATI X700"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by willd on 2006-08-07
Hi all,

I'm trying to an Ubuntu live CD distro off Linux Format in the UK, and I can't get it to work. With normal boot settings I hear music but see no picture, and Ctrl-Alt-F1 takes me to the terminal but I don't know how to do anything else from there. Using safe graphics settings results in the problem edurm talked about in this post:
[]("http://ubuntuforums.org/showthread.php?t=190133&highlight=x850")
I've tried the fixes that are given there and can't get anything to work.
Please note that I don't want to install Ubuntu yet I just want to play around with it and therefore I want to get the LiveCD to work.

If someone can help me I'd much appreciate it.

Cheers,

Will

---

### Post by headstash on 2006-08-07
Sounds like you have the common problem of your monitor being out of the frequency range of the default for the OS.  Try hitting ctrl-alt minus sign to step down the refresh rate.  This will get you to a state where you can see the desktop but you'll have to configure xserve to autodetect your monitor's settings.  Once you get to where you can see the desktop, go to a terminal and type: sudo dpkg-reconfigure xserver-xorg.  Run through the reconfiguration and reboot.  Hope that helps.

Stash

---

### Post by willd on 2006-08-08
Stash, thanks for the suggestion. I tried Ctrl-Alt with both the -_ key and the - key on the numeric pad and nothing happened. Do you or anyone else have any other suggestions please?

The laptop is a Rock Quaddra T64, Turion MT-40, ATI X700 256MB, 1Gb DDR, 17" wide screen 1440x900 LCD panel. It is the same chassis as the MSI L715, and the MS-1036 barebone. Hopefully this information will help someone figure out what I need to do!

I placed this thread in the wrong forum, as I'm not a complete n00b, just forgotten most of linux knowledge, so if a mod could please move it an appropriate forum I'd be grateful.

---

### Post by shilliard on 2006-08-08
Hi

I had to boot up the live CD using safe graphics mode (at boot prompt) with my laptop, it also has an ATI X700.

After that I was able to successfully install Ubuntu

---

### Post by willd on 2006-08-09
Thanks shilliard but that won't work for me either - I get blue screen error messages as in this post:

[http://ubuntuforums.org/showthread.php?t=190133&page=4&highlight=x850]("http://ubuntuforums.org/showthread.php?t=190133&page=4&highlight=x850")

I've tried the solutions described in that post but they don't work either :(

---

### Post by lodbergs on 2006-08-09
> **willd said:**
> Hi all,

I'm trying to an Ubuntu live CD distro off Linux Format in the UK, and I can't get it to work. With normal boot settings I hear music but see no picture, and Ctrl-Alt-F1 takes me to the terminal but I don't know how to do anything else from there.
If someone can help me I'd much appreciate it.

Cheers,

Will

I had the exact same problem as you. In the terminal type:

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv 

Giv it a try - it helped me. And I'm newbie #1 :-D 

Cheers, Søren

---

### Post by willd on 2006-08-12
Soren, thanks for the suggestion but the problem is not with an installed version of Ubuntu, it's with a livecd version, which I assume is why your suggestion didn't work. It may also be because I have no internet access available (posting this from somewhere else).

However, I did find a fix, [http://www.ubuntuforums.org/showthread.php?t=190036]("http://www.ubuntuforums.org/showthread.php?t=190036")

Putting this Option "MonitorLayout" "LVDS,Auto" in Xorg.conf worked for me.

---

