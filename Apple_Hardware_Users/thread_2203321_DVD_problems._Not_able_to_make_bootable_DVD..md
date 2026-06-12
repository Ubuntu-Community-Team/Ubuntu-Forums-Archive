---
title: "DVD problems. Not able to make bootable DVD."
date: 2014-02-02
forum: Apple Hardware Users
---

### Post by shearer4 on 2014-02-02
I have successfully installed Ubuntu on my Mac Pro, by downloading the .iso to my desktop, and re-directing the boot request to that file. Then installed 12.04 in Vbox without too many problems.  But, I have not been able to make a good, readable, bootable DVD on my installed superdrive.  You could ask, why do I care, since I have a successful installation?  

I have tested other burns on my DVD drive, and they are successful in Mac OS files and programs.  

I tried to follow all the instructions I can find on converting a download to Mac which shows up as a .dmg file, to an .iso file?  

Anybody else, seeing this problem?

---

### Post by zircon_34 on 2014-02-02
For making a bootable dvd just open disk utility in MacOS, drag your Ubuntu iso file (no need of dmg) into it and click burn, make sure to click check the dvd after burning. When you boot hold down option key and select your dvd. hope that helps, I just did this today and worked for me.

dmg. is to make your usb bootable...

---

### Post by shearer4 on 2014-02-03
Thanks.  I think I did exactly what you suggested, but not able to boot from that DVD. It shows up and has on it ubuntu-12.04.3-desktop-amd64.iso,  but when I try I get the error "no bootable media found" . 

I was able to boot and install Ubuntu by putting the .iso on my desktop and redirecting Vbox to that image while installing.  So, I am not sure why I feel I need to burn a DVD, but would like to understand what has happened.  

BTW:  I can see the DVD in Ubuntu and it shows the iso, but of course once in the desktop GUI, there is nothing to do.  

Thanks.

---

### Post by zircon_34 on 2014-02-03
> [COLOR=#000000]I was able to boot and install Ubuntu by putting the .iso on my desktop and redirecting Vbox to that image while installing.[/COLOR]

If I understand correctly you are running ubuntu on a virtual desktop right? It seems to me you are trying to boot your dvd in the virtual desktop environment, but the dvd is made for booting your mac at startup (when you press your power button, you hold the option key and should see the dvd and your HD) to boot your Mac straight into Live Ubuntu and not MacOSX..

---

### Post by shearer4 on 2014-02-03
Yes  I am running Ubuntu in Virtual Box.  I'm not trying to boot the DVD in Ubuntu however.  When I first installed VBox and then went to install Ubuntu into it, following the instructions, I made a DVD of the 12.04.3 .iso.  At that point,  I was not able to get Vbox to "see" the bootable drive it was asking for.  

So;  I put the .iso image on my desk top and got it installed that way.  I see now what you are saying, that this DVD could boot Ubuntu and run from the DVD on my Mac, but to install that way I would have to either dual boot using Boot Camp, or do what I have done and install in Vbox?  Am I right about that?  

Again, I am a complete noob to Linux, but not to Mac OSX, which is my primary OS.

---

### Post by zircon_34 on 2014-02-03
> Yes I am running Ubuntu in Virtual Box. I'm not trying to boot the DVD in Ubuntu however. When I first installed VBox and then went to install Ubuntu into it, following the instructions, I made a DVD of the 12.04.3 .iso. At that point, I was not able to get Vbox to "see" the bootable drive it was asking for.
Not sure why, I also used to use virtual desktop with VMware fusion, but did the same as you, I just used the .iso file copied on my desktop.

> I see now what you are saying, that this DVD could boot Ubuntu and run from the DVD on my Mac, but to install that way I would have to either dual boot using Boot Camp, or do what I have done and install in Vbox? Am I right about that?

Yes you can try it in live mode or you could install it as a dual boot system. However its not dual boot using boot camp as this only works with windows. If you want to dual boot MacOS X and Ubuntu you need to install refit or refind. But it involves a little more work, its more easy to run linux in virtual desktop.

> Again, I am a complete noob to Linux, but not to Mac OSX, which is my primary OS.
Me too, but I used now and then Ubuntu as virtual desktop, and now am running dual boot MacOS and Ubuntu, its worth it! I still need time to get to know it better, I cant yet use it for my daily workflow.

---

### Post by shearer4 on 2014-02-03
I agree, it is easier and less invasive it seems to me to run in a virtual desktop.  VBox is free too!  I'm also running, or was running Mint 16 in Vbox. But, I want to make a fixed hdd. Originally, I had selected dynamic and 8 gigs, but it's just not enough swap file.  So, I removed it and I am trying to reinstall it on another drive I have in my MacPro.  Having some trouble with that. Maybe it needs to be on the same drive as Vbox?

---

