---
title: "Booting from CD - screen goes blank"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Fruitaloop on 2007-07-10
I've downloaded Ubuntu, then copied to a DVD and am trying to load onto a machine with a new, blank hard drive.  The CD appears to be good, because I was able to boot up from the CD 1 time.  Every other time, it will go thru all the initializing screens, even displaying when all the drivers are being loaded, then the screen goes blank.  The CD continues to run a while like it is still installing, but I can't see anything, not even the brown background screen.  Then finally the CD stops, and I can't do anything.
It is a 4 year old Gateway that meets the specs for Ubuntu.
Any suggestions?

---

### Post by the.phantom on 2007-07-10
the first screen in the live cd gives you the option to verify the quality of the cd. have you tried that?

what are the sys specks ( including video card)
and what version of U? 32 or 64 bit and version 
thanks

---

### Post by kvonb on 2007-07-10
On boot, try selecting the "safe graphics mode", it might be a video card issue.

What video card do you have, and is it onboard/PCI/AGP/PCIE etc'?

You can press <ctrl><alt><f1> to switch to a console when you get the black screen, you might see some error messages there.  Press <ctrl><alt><f7> to get back to the desktop.

---

### Post by Fruitaloop on 2007-07-10
Thanks for the quick response!
I have verified the quality of the CD, and it says it is good.
I downloaded Ubuntu 7.04
I don't remember the machine specs - and it doesn't have a formatted hard drive in it now so I can see them.  I think it had 256 meg of memory and the standard video card that came with Gateway machines about 3 years ago.  I'm not sure how to find the make of video card.

---

### Post by Fruitaloop on 2007-07-10
I think everyone is right - it is probably the video card.  I just tried it again with some of the suggestions (I've pretty much been using the 'safe graphics mode').  This time there was a screen full of colored lines as it was rebooting.  After that I tired the CTL ALT F1 and got a list of all the things it was doing, then at the bottom the message "<1> Fixing Recursive Fault, But Reboot Is Needed!"  This is probably what has been happening, but I couldn't see it until I hit the F1.
I don't know if this gives any more info or not????

---

### Post by lbelloq on 2007-07-11
Try booting with the -noapic option. I had the same problem with a Compaq notebook and it worked.

---

### Post by snwbord2456 on 2007-07-11
If you use an ATI card you cant install Ubuntu with the regular install .iso. (Note; make sure to try the other stuff first, because this way you have to download another .iso file and that could take a while and I also could be wrong)

Goto the downloads page and click the alternate version and use the text-based one to install the OS. Then use this guide

[http://ubuntuforums.org/showthread.php?t=399913&highlight=feisty+on+dell](http://ubuntuforums.org/showthread.php?t=399913&highlight=feisty+on+dell)

to update your drivers and then this one

[http://ubuntuforums.org/showthread.php?t=297092&highlight=e1505](http://ubuntuforums.org/showthread.php?t=297092&highlight=e1505)

if your wifi isnt running.

Good luck, I started using Ubuntu not even a week ago and I'm never going back to XP.

---

