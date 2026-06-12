---
title: "Help a death-sentenced kid(a.k.a me)"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by !Rami! on 2007-12-26
Sorry for the quite vulgar title, but i have a problem with both the terminal and libgpod. when i run the commando cd libgpod-0.6.0 it just say that it cant find the file even if its unpacked. this means that my Pod is unusable, because i had it down to the apple store to format is, since i thought that would be the case that it didnt sync with the PC. but now i cant use it at all. no songs or anything and i cant sync it either with my PC or my own computer, and since my dad bought it to me, he's going to kill me if he finds out. i really really need to install libgpod on the computer.

---

### Post by wheredidrealitygo on 2007-12-26
You should be able to download it from the repositories with Synaptic.

Go to "System, Administration, Synaptic Package Manager", and search for the package named "libgpod2".

---

### Post by wolfen69 on 2007-12-26
have you tried gtkpod?

---

### Post by !Rami! on 2007-12-26
I've installed GTKpod, but its quite an old model, and even worse, occasionally i've got no internet. so i have to go to the train terminal down town with my laptop then:)
EDIT: i haqve libgpod2, and i can play the one testsong that they tried to put in on the iPod in the apple store, but i cant transfer songs. it only opens in rhythmbox, but not in amarok.

---

### Post by LowSky on 2007-12-26
How old/model is the iPod?
DO you only use Ubuntu or do you have Windows?

The newest generation iPods dont work very well with Linux.
And why would your dad kill you? Did it work fine before? Or has it always not worked.

EDIT: try this 

> **hollowhead said:**
> See this thread 
[http://ubuntuforums.org/showthread.php?t=619615&page=9](http://ubuntuforums.org/showthread.php?t=619615&page=9)

follow the link posted by siwilson or me and follow the instructions it will work see my post for variations......

---

### Post by !Rami! on 2007-12-26
The iPod is the new nano, and we have a windows computer(the one i'm writing on now) BUT!! heres the big problem, the USB drivers in this computer is messed up, so i can't connect my ipod here. it had worked before until above happened.

---

### Post by LowSky on 2007-12-26
seems likes you need to reset your ipod to factory setting in iTunes and start fresh. I think I have reset my iPod like 2-3 times before, and mine is the old 5.5 gen Video iPod.

Also fix the USB drivers in Windows or reinstall Windows.

---

### Post by dannyboy79 on 2007-12-26
how can you screw up windows usb drivers? if you go into the control panel, then system, then hardware, just chose to uninstall the usb devices and then when you restart the machine, windows should reinstall the proper windows drivers for usb devices. I always thought that the ipods were plug and play, are you saying that they come with their own device drivers? not sure what else to suggest. can you check out your ipod at a friends house to see if you can transfer stuff to it their? Also, you stated that apple just reformatted it or whatever, did they show you that it still worked while you were at the store? Maybe this has something to do with what they did to it thinking they fixed it but they really didn't.

---

### Post by LowSky on 2007-12-26
You will be amazed what some people can do to PC drivers.. I have had to *fix my sister's computer too many times, and the only issue was she installed malware. 
As for the iPod not syncing, try doing a hard reset of it 

first switch it to Hold then back to normal
the hold the menu and middle button down until the screen reboots.

---

### Post by landrash on 2007-12-26
dannyboy79: The usb drivers in windows are rather easy to mess up and if you dont have any rollback there is a chance that you will have to reinstall windows.

!Rami!: Think I would suggest trying to fix the windows version alt trying different version of pod software. More information about models, more specific what the problems are and what you have tried would help us helping you.

More information about how too sync the new models can be found at [http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

---

### Post by dannyboy79 on 2007-12-26
> **landrash said:**
> dannyboy79: The usb drivers in windows are rather easy to mess up and if you dont have any rollback there is a chance that you will have to reinstall windows.

can you elaborate on that a little? how on earth does one screw up a usb driver? aren't these system files that shouldn't even be messed with? you should be able to do a repair of windows before having to reinstall windows regardless. please correct me if I am wrong.

---

### Post by !Rami! on 2007-12-26
I havent screwed up the USB drivers, only plug-and-play things with discs will run on the computer.

---

### Post by !Rami! on 2007-12-26
I've come quite far in the guide but i get stuck at this. ipod-read-sysinfo-extended /dev/sda1 /media/IPOD
when you look at df, it says dev/sda1 at the top and /dev/sdb2 at the line with the ipod, which line should i refer to?

---

### Post by rockin_goliath on 2007-12-26
I wouldn't bother trying to restore your iPod within Linux, it's just too complicated. You'll spend the same amount or more time trying to figure it out when instead you can install Windows into VirtualBox (in the repositories), install the VirtualBox guest additions in the virtual machine, install iTunes, and restore the iPod that way. When you are done, you can get rid of the WinXP virtual machine, and your new iPod should work fine in Rhythmbox. I hate having to use Windows for these kinds of things, but that's the way it is I guess.

---

### Post by sid351 on 2007-12-27
> **dannyboy79 said:**
> how can you screw up windows usb drivers? if you go into the control panel, then system, then hardware, just chose to uninstall the usb devices and then when you restart the machine, windows should reinstall the proper windows drivers for usb devices. I always thought that the ipods were plug and play, are you saying that they come with their own device drivers? not sure what else to suggest. can you check out your ipod at a friends house to see if you can transfer stuff to it their? Also, you stated that apple just reformatted it or whatever, did they show you that it still worked while you were at the store? Maybe this has something to do with what they did to it thinking they fixed it but they really didn't.

I've managed to eff up the USB drivers on a Windows machine before...quite funny really, despite the 3 late nights trying to t/s it and then the night reinstalling everything...glad I don't work there anymore!!!

---

