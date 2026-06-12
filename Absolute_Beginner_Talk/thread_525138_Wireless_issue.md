---
title: "Wireless issue"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Eezyville on 2007-08-14
OK so I got a Broadcom 4310 wireless card. It wont work. I believe I have drivers for it. I think I need the firmware for it. So I tried to get this "fwcutter" but received an error.

HTTP request sent, awaiting response... 404 Not Found
21:31:30 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have the windows xp drivers for it, i downloaded them and extracted them using wine. What do i do. I think I need the fwcutter because I was using a tutorial to set up my wireless card.

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

thats the thread I was using for my wireless. What next?:confused:

---

### Post by Eezyville on 2007-08-14
OK I don't know what just happened. This is how it went down:

1st I extracted the files from the .exe drivers file I downloaded from HP's website. 

I already tried to get this fwcutter thing installed but I don't think it worked so I asked for help. 

I was looking around in that link I posted earlier and on the first reply someone suggested a command line to create firmware files in the directory I'm currently in.

bcm43xx-fwcutter /home/$USER/Desktop/bcmwl5.sys

thats the command line

So I type it in and look in my home folder and some files appeared.

Next I type in, "sudo apt-get install network-manager-gnome" and "nm-applet --sm-disable" just to see what happens. 

The my wireless works. ](*,)](*,)](*,)

:confused:

Edit: Now i have two wireless bar icons and a bunch of firmware files in a place where i don't think they're safe. Where should I put these files? How do I get rid of the extra wireless icon? And WTF just happened?!

Edit2: Ok so the second wireless bar just went away. :confused:
ok then.:confused:

---

