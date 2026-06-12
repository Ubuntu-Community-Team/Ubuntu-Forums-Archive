---
title: "Ubuntu Edgy on iMac Core2Duo"
date: 2007-03-12
forum: Apple Intel Users
---

### Post by bherg on 2007-03-12
Hi everyone,

I installed Ubuntu Edgy on iMac c2d (using rEFIt and lilo as boot loader). But with some issues:

1. The keyboard didn't work when I booted from Live CD to install it the first four times. I had to reboot in order to get it working.

2. Once I booted the livecd and started the installation I managed to install Ubuntu and all went smooth and I finished the process with Ubuntu installed on my iMac, so I rebooted and I had the same problems with the keyboard. I rebooted three or four times before it worked.

3. Once I booted, I just did apt-get update && apt-get -u dist-upgrade, rebooted again and the weird keyboard thing happened again. I rebooted at least 10 times and only get the keyboard working once (pressing F8 for lilo menu). Anyway, it tries to boot but it gets stuck when it finishes loading the kernel (well, Loading Ubuntu....................... ...).

I don't know what else to try... should I reinstall or something? What about the keyboard thing? Does this happened to anyone before? :(

---

### Post by cyberdork33 on 2007-03-12
I cannot navigate in grub with the keyboard on my 20" iMac. It seems that there is no keyboard support until the kernel is started. I haven't had any freezing during startup though. It does stall awhile on the initial progress bar screen, but it eventually starts up.

---

### Post by bherg on 2007-03-12
> **cyberdork33 said:**
> I cannot navigate in grub with the keyboard on my 20" iMac. It seems that there is no keyboard support until the kernel is started. I haven't had any freezing during startup though. It does stall awhile on the initial progress bar screen, but it eventually starts up.

Thanks for your reply man. I guess that's normal that the keyboard isn't working until the kernel is started (USB keyboard) but, why it worked a couple of times in Grub menu? And why I was able to show the LILO help?

BTW, it isn't loading any splash image when it loads and it seems it hangs when it finishes kernel loading. It could be a framebuffer issue or something? It seems it gets stuck but if I check if the keyboard is working (pressing CAPS lock) the light is always off, no response.

Any ideas? Pretty wierd imho.

---

### Post by cyberdork33 on 2007-03-12
The keyboard thing is just a guess on my part. I have never had the keyboard work in grub (though I have never really tried to fix it). IDK what to tell you about the freezing though, sorry!

---

### Post by bherg on 2007-03-13
Solved! 

I just booted with the LiveCD and chrooted again my Ubuntu partition. Then executed again LILO with my lilo.conf and rebooted.

Now I have it fully working with XGL+BERYL, sound, eth, bluetooth and no keyboard weird things.

Thanks anyway! :mrgreen:

---

### Post by spigolo on 2007-03-13
hi behrg, i just bought an imac c2d and i really wanted to install ubuntu on it (double boot with the original osx). did you follow a specific howto???

thanks!

---

### Post by bherg on 2007-03-13
> **spigolo said:**
> hi behrg, i just bought an imac c2d and i really wanted to install ubuntu on it (double boot with the original osx). did you follow a specific howto???

thanks!

Hi man. Yup, but it's in Spanish :(

[http://underblg.blogspot.com/2006/09/como-instalar-ubuntu-dapper-x86-en-un.html](http://underblg.blogspot.com/2006/09/como-instalar-ubuntu-dapper-x86-en-un.html)

If you want me to translate it or smthg, just tell me.

---

### Post by zAo on 2007-03-13
Hi, I want to install Ubuntu on my C2D iMac too. Does the wireless work without ndiswrapper?

---

### Post by bherg on 2007-03-13
> **zAo said:**
> Hi, I want to install Ubuntu on my C2D iMac too. Does the wireless work without ndiswrapper?

I didn't try it yet. but I can take a look and do some feedback about it. I'm thinking about translate the HOWTO too, maybe tonight if I have enough time.

I'll keep ya posted.

---

### Post by cyberdork33 on 2007-03-13
No, you have to get the driver out of the bootcamp CD, and use ndiswrapper...

P.S. I don't know what's different, but my keyboard seems to work in grub now.

This is a good howto for the macbook:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

There is another howto for an iMac that I can't find, but it basically says follow this guide with a couple of changes. (Most likely wifi being one)

---

### Post by AnthonyJK@gmail.com on 2007-03-14
I have the exact same problem, but how do you chroot the partition?

sudo chroot /mnt/ubuntu /bin/bash

?

Thanks!

---

### Post by cyberdork33 on 2007-03-14
> **AnthonyJK@gmail.com said:**
> I have the exact same problem, but how do you chroot the partition?

sudo chroot /mnt/ubuntu /bin/bash

?

Thanks!

booting pretty much any live CD, you can mount the hard drive partitions and use chroot to enter your installed system. Your command looks correct if your ubuntu root partition is mounted at /mnt/ubuntu

---

### Post by bherg on 2007-03-14
> **AnthonyJK@gmail.com said:**
> I have the exact same problem, but how do you chroot the partition?

sudo chroot /mnt/ubuntu /bin/bash

?

Thanks!

Yep, but before that you should mount proc filesystem and the device nodes of your system, otherwise it will not recognise your partition once you did chroot.

Just do it as follows:

- # mkdir /mnt/ubuntu
- # mount /dev/sda3 /mnt/ubuntu/
- # mount -t proc none /mnt/ubuntu/proc
- # mount -o bind /dev /mnt/ubuntu/dev
- # chroot /mnt/ubuntu /bin/bash

Then just execute lilo (lilo -b /etc/sdX where X is your partition number) and reboot. Once you reboot you should sync again the partition table with rEFIt and you're done!

Indeed, I used a HOWTO based on the MacPro, it's in spanish but I plan to translate it this week.

---

### Post by spigolo on 2007-03-14
hi again!
i finally installed ubuntu on the imac, it was a bit of a nightmare because, following the MacBook guide, i ended up with having a gpt wrong, so a wrong mbr after syncing, so i could not boot (using grub). 

anyway: for the keyboard problem starting from the livecd, i found that if it doesnt work you should unplug it and plug it back in, then it starts working (rebooting 10 times becomes too much sometimes :) )

now i have beryl up, but no sound and no isight (can't try wireless yet), i'll investigate  deeper in the next days (any useful guide?).

for the spanish guide: being italian, i was tempted to follow it, it seemed understandable :). but it was on dapper :) not on edgy.

---

### Post by cyberdork33 on 2007-03-14
sound is easy,

right-click the speaker icon in the corner,
select "Open Volume Control"
then choose the "Switches" tab on the window that opens
and check the box that says: Line in as output.

thanks for the keyboard tip!

---

### Post by spigolo on 2007-03-14
oh that was easy :)  !!! thanks, i thought i had tried them all. so... what about the mic???

---

### Post by cyberdork33 on 2007-03-14
I haven't messed with the mic on mine... there is a tutorial for getting the isight to work though. it involves pullings some info out of your OSX install, and it only works with a limited number of apps... but it will work!

[http://www.ubuntuforums.org/showthread.php?t=225621](http://www.ubuntuforums.org/showthread.php?t=225621)

The only difference being that you should make sure you get the latest version on linux-uvc at [http://people.freedesktop.org/~rbultje/](http://people.freedesktop.org/~rbultje/)

(I think that it is currently v 0.1.0-e)

---

### Post by macLuntu on 2007-03-17
Follow up on the problem where Ubuntu hangs at the end of the "splash bar".


This is because Ubuntu installs the vesa driver by default. This driver doesn't work with the ATI x1600 cards which is shipped with the Apple iMac (17" and 20").
Solution: (Needs a network connection)
Enter grub menu at boot (as mentioned that can take a while because of the keyboard issue)
In the grub menu type e to edit then get down to the second line from the top and press e again. Remove splash from boot params. Press enter, and the b to boot.

X will fail and you will be asked if you to see blah blah.. Answer no, and you will be presented by a prompt. No install the proprietary ATI drivers:
```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

Reboot

This fixed it for me.

---

