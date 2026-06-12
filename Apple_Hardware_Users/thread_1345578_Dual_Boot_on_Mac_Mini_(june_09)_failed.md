---
title: "Dual Boot on Mac Mini (june 09) failed"
date: 2009-12-04
forum: Apple Hardware Users
---

### Post by Fluche on 2009-12-04
Hello,

I wanted to try the dual boot on my Mac Mini bought in june, freshly updated with snow leopard. 
I've donlowded the last version of Ubuntu and followed this doc : [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

At the end of the install, I clicked on "Restart", the CD was ejected, and the screen went black. And nothing else. 

So I shut off the comptuer (I hate to do that, but what else could I do), and the boot menu showed me the little nice apple and and a grey Window labelled "Unknow partition" 

I gave two tries and all it did is create several Linux Swap, an unknown partition,... if you want I can give you the diagnosis. 

Could you please help me? None of my friends is able. They're not on Mac nor on Linux. 

Thank you in advance

Fred

---

### Post by linuxopjemac on 2009-12-04
did you install rEFIt from within OSX ?

---

### Post by Fluche on 2009-12-04
Yes I did. I haved followed the doc step by step.

---

### Post by linuxopjemac on 2009-12-04
so you also synced your partition table from within rEFIt then ?

---

### Post by Fluche on 2009-12-04
Should I have done this step before installing Ubuntu?

---

### Post by linuxopjemac on 2009-12-04
no after, go to rEFIt, click the partition tool and ask it to sync the partition table.

---

### Post by Fluche on 2009-12-04
Ok, I wanted to do this, but after the restart, rEFIt gave me an error message 'No bootable device"

---

### Post by linuxopjemac on 2009-12-04
oops, ok. I have seen something like this earlier in the forums. What you could try is to start from the liveCD again into the live environment (use Ubuntu without installing) and then start gparted (the partition tool you saw during the installation). Add the boot flag to the Ubuntu root partition, even when you think it's already there. restart, try to sync then...then restart, then hopefully you see "Legacy OS" as an option and you click that. It should boot Ubuntu then hopefully.

---

### Post by Fluche on 2009-12-04
Great! I will try this at home tonight. 

Do you think I will be able to erase the unneded things on the hard drive (I have two Linux swaps)?

Thank you so muuuch!

---

### Post by linuxopjemac on 2009-12-04
you could erase it and make it ext4 and mount it later on the desktop. But if it's less than 1 Gb, I would probably not bother.

---

### Post by Fluche on 2009-12-04
Indeed, it is tiny. 

Thank you again!!!

---

### Post by Fluche on 2009-12-06
I finally managed to have this working, thanks to you.

Only a few things to have to be fixed but now it is a success.

Thank you again.

---

### Post by linuxopjemac on 2009-12-06
Great work, you did it yourself in the end ;)

---

### Post by Fluche on 2009-12-06
:p

Not really on my own.

---

### Post by coco banderos on 2010-01-08
If this really does work, can you change the title of the thread from "failed" to "SOLVED" so others can find it?

---

### Post by Fluche on 2010-01-11
Sorry... I forgot to modify the tread. 

Have a nice day,

Fred

---

