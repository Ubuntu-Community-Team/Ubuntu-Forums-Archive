---
title: "Trouble installing Ubuntu 7.10 (Intel iMac)"
date: 2007-11-01
forum: Apple Intel Users
---

### Post by Soundblokey on 2007-11-01
I'm trying to install Ubuntu 7.10 on my iMac (standard spec 24" from last august) but I can't get it to boot from any disk.

I've partitioned the hard drive using bootcamp to give 36GB of space for Linux and another 10GB slot which my housemate put in for no apparent reason…but it seems to have worked ok. I've downloaded and installed rEFIt which also works fine (well, it loads at startup and gives me all the options I'd expect).

So having done all this I have the disk image downloaded from the Ubuntu site, I used terminal to create an install disk for Ubuntu and then restarted. rEFIt loaded up fine and gave me the options of running MacOS or Linux so I selected Linux and hit enter.

10 minutes of a blank screen with whirring noises and all the usual sounds you'd expect from trying to load a disk it just stopped and sat there with a blank screen.

Any help on what I'm doing wrong would be greatly appreciated (I'm assuming it's me since my Mac works fine with everything else I've ever done, not including ProTools which just hates everything anyway and is probably unrelated). If it's not me then any ideas on how to get it sorted would be great since I've already mentioned it at my local apple store and the few who didn't just say they don't support it couldn't help anyway.

Oh and I'm a complete Linux noob who only found out that terminal existed on Mac today so please keep it nice and simple :)

---

### Post by cyberdork33 on 2007-11-01
> **Soundblokey said:**
> I'm trying to install Ubuntu 7.10 on my iMac (standard spec 24" from last august) but I can't get it to boot from any disk.

I've partitioned the hard drive using bootcamp to give 36GB of space for Linux and another 10GB slot which my housemate put in for no apparent reason…but it seems to have worked ok. I've downloaded and installed rEFIt which also works fine (well, it loads at startup and gives me all the options I'd expect).

So having done all this I have the disk image downloaded from the Ubuntu site, I used terminal to create an install disk for Ubuntu and then restarted. rEFIt loaded up fine and gave me the options of running MacOS or Linux so I selected Linux and hit enter.

10 minutes of a blank screen with whirring noises and all the usual sounds you'd expect from trying to load a disk it just stopped and sat there with a blank screen.

Any help on what I'm doing wrong would be greatly appreciated (I'm assuming it's me since my Mac works fine with everything else I've ever done, not including ProTools which just hates everything anyway and is probably unrelated). If it's not me then any ideas on how to get it sorted would be great since I've already mentioned it at my local apple store and the few who didn't just say they don't support it couldn't help anyway.

Oh and I'm a complete Linux noob who only found out that terminal existed on Mac today so please keep it nice and simple :)

how are you creating the disc from the terminal?

Just burn it (slowly) from Disk Utility.

---

### Post by Soundblokey on 2007-11-02
Tried that and writing it using a terminal command to copy the image but I'm pretty sure it's not that since I have tried 5 different windows disks and 3 different linux disks- none of them work (I went through all the steps to boot windows and everything).

I get the impression that it's just a built in problem with my Mac but I don't quite know what yet. Either that or I've just been doing something wrong for windows and had 2 faulty and 1 badly written for linux...unlikely but then I have a habit of pulling that sort of thing off lol.

Still as always I'm open to try any sensible suggestions and such input is greatly appreciated! :)

---

### Post by cyberdork33 on 2007-11-03
> **Soundblokey said:**
> Tried that and writing it using a terminal command to copy the image but I'm pretty sure it's not that since I have tried 5 different windows disks and 3 different linux disks- none of them work (I went through all the steps to boot windows and everything).

I get the impression that it's just a built in problem with my Mac but I don't quite know what yet. Either that or I've just been doing something wrong for windows and had 2 faulty and 1 badly written for linux...unlikely but then I have a habit of pulling that sort of thing off lol.

Still as always I'm open to try any sensible suggestions and such input is greatly appreciated! :)
what command...

---

### Post by Soundblokey on 2007-11-08
Can't find it now lol, it was just an hdiutil burn command so basically the same as using disk utility anyway, I'm pretty sure that worked since refit recognised the disk as a linux one and also I've tried this with other disks, some official and some burned by other people and they've all given me the same result- refit recognises them but when I try and boot them it won't work

---

### Post by cyberdork33 on 2007-11-08
> **Soundblokey said:**
> Can't find it now lol, it was just an hdiutil burn command so basically the same as using disk utility anyway, I'm pretty sure that worked since refit recognised the disk as a linux one and also I've tried this with other disks, some official and some burned by other people and they've all given me the same result- refit recognises them but when I try and boot them it won't work
I find that OSX burns bootable discs very poorly. Try burning them as slow as possible and you might have better luck.

---

### Post by Soundblokey on 2007-11-09
Thx :) it's a good idea and I've had trouble with that in the past but I already burned it at the slowest speed it'll normally do (2x) and since I've tried disks that aren't burned for other OSs, now including ubuntu 6.06, I'm certain it's something more to do with my mac than the disk itself so I'm going to go to the apple store and see if they have any idea what's wrong and whether I can fix it myself or anything useful really.

---

### Post by cyberdork33 on 2007-11-09
> **Soundblokey said:**
> Thx :) it's a good idea and I've had trouble with that in the past but I already burned it at the slowest speed it'll normally do (2x) and since I've tried disks that aren't burned for other OSs, now including ubuntu 6.06, I'm certain it's something more to do with my mac than the disk itself so I'm going to go to the apple store and see if they have any idea what's wrong and whether I can fix it myself or anything useful really.

haha. I assume a 'beermat' is the same thing we call a coaster?

---

### Post by Zelut on 2007-11-10
My guess is that its something with the CD as well.  When prompted with the rEFIt screen you should be given an option to boot from CD as well.  I would find some other options for burning the CD (do you know anyone else that currently runs linux that can give you a copy, or burn a fresh copy from Nautilus?)

If the CD actually works you should be given an option at rEFIt to boot from CD, and then go on from there..

---

### Post by Soundblokey on 2007-11-16
Ah you see this is why I think it's a hardware fault- as I said I've tried many disks, around 20 now of legal or cracked versions of most OSs which are either official disks or ones burned with 5 different programs, including using Nero on my PC and with almost all of them, it gives me the option to boot from disk, that I can get- just once I click it the screen goes black and after trying for a while it fails to boot and sits there doing nothing. I think I'll just run linux on my PC once I replace the fuse I blew last week hehe.

And yes a beermat is basically a coaster, although generally the word coaster is used over here to mean a proper mat made of cork or something, where beermats are cheap square card ones with beer adverts on :) But then don't get me started on the difference in English and American English…new words are good but I always get really annoyed when I hear things like 'Aluminum' lol

(That last paragraph seems so much more geeky and less funny on the internet :()

---

### Post by powermacj7 on 2007-11-19
I got as far as the Ubuntu install screen on my iMac duo core (white) and the keyboard would not work. I purchased the newer Apple keyboard (aluminum) model. So I turned the computer off, hooked up the older keyboard (original) and tried it again, same problem, no keyboard. I obviously could not selected anything. This was the 64-bit Ubuntu version. 

I have 7.10 installed on a older Thinkpad, was curious as to how Ubuntu would run on a newer machine. I am looking around to purchase a laptop, newer that would have great Linux support, and perhaps Ubuntu all ready installed. I see that Dell does sell some models for under $800. 

I have always been a Mac user and never purchased a PC before. I am leaning toward the Thinkpad model again. :confused:

---

### Post by cyberdork33 on 2007-11-19
> **powermacj7 said:**
> I got as far as the Ubuntu install screen on my iMac duo core (white) and the keyboard would not work. I purchased the newer Apple keyboard (aluminum) model. So I turned the computer off, hooked up the older keyboard (original) and tried it again, same problem, no keyboard. I obviously could not selected anything. This was the 64-bit Ubuntu version. 

I have 7.10 installed on a older Thinkpad, was curious as to how Ubuntu would run on a newer machine. I am looking around to purchase a laptop, newer that would have great Linux support, and perhaps Ubuntu all ready installed. I see that Dell does sell some models for under $800. 

I have always been a Mac user and never purchased a PC before. I am leaning toward the Thinkpad model again. :confused:

The keyboard problem is one that has plagued us for quite awhile (this includes all the mactels). It is related to the Apple firmware, and unfortunately, that means that the Ubuntu community cannot make any changes to fix it. The keyboards were working well after the Mac firmware updates that came out in September, but it is again not working for me since I have installed Leopard.

If you are attempting to boot the Live CD (not the alternative CD) there is a timeout that should boot the default option (Install) so that you can get to the point where the keyboard works again (within linux rather than the bootloader). A trick that also used to work for me was, when at the bootloader screen, I could unplug and replug the usb keyboard, and that would get it working. 

The Thinkpads are very nice machines, but I would indeed recommend something like the Dell linux machines as you can be sure that the hardware will work well with Ubuntu (unlike the Mac). You may very well find that a thinkpad will work just fine though. The Hardware & Laptop Forum has a lot of information about (in)compatible hardware. You might want to check there before making a purchase.

---

### Post by powermacj7 on 2007-11-20
Well thanks for the reply. I am leaning toward the Dell that comes configured with Ubuntu all ready. As far as my Mac, I think I will just leave it with Leopard, as I was not keen on a dual boot machine anyway.

---

