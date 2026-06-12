---
title: "I can't change the screen resolution to 1280x1024"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by garitd on 2006-08-25
Ok heres the deal.  I've tried everything I can think of and I've asked around and looked around and so now im here.

I have the latest Unbuntu with Gnome.  I have an Nvidia 5200 video card.

What ive tried:

I made a password for root with passwd root in the terminal.  I su to root then I go nano /etc/X11/xorg.conf

I change the resolution for the default monitor (the one that says depth 24) to include all the resolutions that I want.  (I made a few attempts and one of two things happen...) Either I reboot and it gives me errors and doesnt boot.  Or it boots and I go to change the resolution in the system preferences and it doesnt have any of the choices I added.  Or once It gave me less choices and the best i could get was 800x600.. that was suprising.. lol

anyway.. what could it be?  I would love any help?  ps i've been using ubuntu for like a week.  lol

Thanks
G

---

### Post by Engnome on 2006-08-25
Tried running "sudo dgkg-reconfigure xserver-xorg" and selecting your resolution?

---

### Post by orb9220 on 2006-08-25
Also have you installed the nvidia drivers the default drivers only go to 1024 I believe.

---

### Post by confused57 on 2006-08-25
I have a Nvidia GeForce XFX5500 and use the "nv" driver, no problems with 1280 X 1024 on a 19" LCD.

As mentioned earlier, use:
```
sudo dpkg-reconfigure xserver-xorg
```
At the first screen, select "no" for autodetect your video settings, then you can probably just select the default values for everything, except your video driver & resolutions you want to use.

---

### Post by garitd on 2006-08-27
Yes I have tried the reconfigure xserver-xorg but it still comes out the same.  So.. is it easy to download and install the newest nvidia driver?  please tell me there is an easy command in the terminal.

thanks

---

### Post by Kobalt on 2006-08-27
Hi,

Have you restarted X after you ran "sudo dpkg-reconfigure xserver-xorg" ? If not, to it with Ctrl+Alt+Backspace. 

Ps: Also make sure to have selected the resolutions you want avaliable with the spacebar?

Cheerios !

---

### Post by _simon_ on 2006-08-27
I did it by adding 1280 x 1024 to Xorg then installing the nvidia drivers.

I couldn't get above 1024x768 on the nv drivers.

[http://www.ubuntuforums.org/showthread.php?t=139264&highlight=nvidia+testers](http://www.ubuntuforums.org/showthread.php?t=139264&highlight=nvidia+testers)

You can install step by step or use a script.

---

### Post by garitd on 2006-08-27
You guys so totally rule!  I changed the xorg.conf file a million times.. but it did nothing untill I installed the nvidia glx driver then changes the xorg.conf again from nv to nvidia.. and i restart x and wha bam! been trying to get it working for a few days now!  Im so excited.  Thanks for all the help!

-G-

---

### Post by Kobalt on 2006-08-27
You're welcome, we rule... Life is great then :rolleyes: 

Cheerios !

---

