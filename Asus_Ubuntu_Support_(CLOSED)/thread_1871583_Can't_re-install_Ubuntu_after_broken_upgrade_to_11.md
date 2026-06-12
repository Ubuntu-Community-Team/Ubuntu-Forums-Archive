---
title: "Can't re-install Ubuntu after broken upgrade to 11.10"
date: 2011-10-29
forum: Asus Ubuntu Support (CLOSED)
---

### Post by buren on 2011-10-29
I'd just upgraded to Ubuntu 11.10 and all sorts of random problems occured. However now I wan't to reinstall Ubuntu 11.10 on my computer but I can't.

I'm trying to accomplish this by installing Ubuntu 11.10 from a USB-drive. But when I boot from the USB drive I get to the point where I can choose from installing it from USB or just runing it. But no mather what option I choose I get a FATAL ERROR. 

I've tried to make another USB-boot drive from both Ubuntu and another computer running Win7 but I still get the same ERROR. 

The thing that makes me really nervous is that my current install won't recognize any USB or SD-cards at all, it's just like they don't exist. The boot priority list in BIOS can recognize the USB-drive. I have a ASUS U35JC computer and it lacks CD/DVD drive so I can't try installing Ubuntu that way.

Do anyone have any suggestions of how I might be able to reinstall Ubuntu? (at this point I will settle with either 11.04 or 11.10..)

---

### Post by garvinrick4 on 2011-10-29
Make sure it is booting usb first:
Put USB in and boot:
Tap space bar soon as you see 3 icons on bottom of screen.
Choose to install hit enter.

If that does not work then hit F6 when you see icons and go to far right and set to boot with nomodeset.
Now try.

---

### Post by varunendra on 2011-10-30
Getting to the option where you can choose between installing or just running means the USB is booting fine. The "FATAL ERROR" may be caused by several reasons. 
Try the nomodeset option as told by garvinrick4. If that doesn't help, also try the [other options]("https://help.ubuntu.com/community/BootOptions") altogether.

If none of those options help, the starting point for further troubleshooting would be to check the integrity of the iso:
How to MD5Sum: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Ubuntu Hashes: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Also, if you have access to another computer, try the same USB on it to see if it gives the same error.

---

### Post by buren on 2011-11-01
I can do neither of your suggestions Im afraid.. and I just relized I missread the Error message (it is not visable long on the screen). After I press Install ubuntu or Run from USB, the output goes very fast but it sats FIRMWARE ERROR. And after a while the ubuntu splash appears for a few seconds and then I get this output 

[http://imageshack.us/g/69/imag0786.jpg/](http://imageshack.us/g/69/imag0786.jpg/)

---

### Post by shawnat88 on 2012-01-03
try my fix here: 
[http://ubuntuforums.org/showthread.php?t=1837366](http://ubuntuforums.org/showthread.php?t=1837366)

---

