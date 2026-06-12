---
title: "Duel booting and partioning(?)"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Aiello on 2007-08-21
Well, I having been playing around in the live CD for a while and have decided to install Ubuntu on my computer. But, I want it to duel boot with Windows. Also, since it is a family computer, Windows will need most of the disk space on the HDD. 
I'm not that tech savvy and all this talk of partioning and GRUB isn't making much sense to me.:confused: How can I install Ubuntu along side Windows on the same HDD while giving Windows most of the disk space? How do I choose which OS the computer boots? Any way to make it so that it boots Windows by default?
Please try to explain as much as you can. Complete newb here.
-Thanks!

---

### Post by oilchangeguy on 2007-08-21
> **Aiello said:**
> Well, I having been playing around in the live CD for a while and have decided to install Ubuntu on my computer. But, I want it to duel boot with Windows. Also, since it is a family computer, Windows will need most of the disk space on the HDD. 
I'm not that tech savvy and all this talk of partioning and GRUB isn't making much sense to me.:confused: How can I install Ubuntu along side Windows on the same HDD while giving Windows most of the disk space? How do I choose which OS the computer boots? Any way to make it so that it boots Windows by default?
Please try to explain as much as you can. Complete newb here.
-Thanks!

how large is the hard drive? how much free space does it have? you'll have to use gparted from the live cd, to manually partition the drive. grub (grand unified boot loader) is what boots the os. yes you can change the boot order from within grub.

---

### Post by reckless2k2 on 2007-08-21
it is not a hard thing to do but very intimidating if you are confessed not very computer functional. The easiest way to put it is that it is not very comfortable to do if all of those things are foreign to you. this is kind of where linux really opens the doors for you to learn more about linux and computers in general. 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

That will give you the answers on how to do it but you may have read it already. i know it may not be the answer you want to hear but if you are not very computer literate it will be difficult and you may mess up. hahaha. it's kinda like this in a nut shell:

1 - defrag your windows computer first. 

2 - then use a tool like gparted livecd to resize the current windows partition. you will make it smaller. ubuntu only needs like 5GB...make it 10 to be safe on the back end of the partition. now you should have windows in front at XXGB and an empty space of 10GB at the end. 

3 - pop in the ubuntu livecd and install to largest free space. it kinda does all the work. when it asks about the grub, just leave it to install on the MBR. 

4 - reboot and you're done...you'll have a choice of ubuntu on the top and windows on the bottom. 

this is quick and dirty loose. good luck. backup important windows files before starting just in case you can't loose them.

---

### Post by st33med on 2007-08-21
> **Aiello said:**
> Well, I having been playing around in the live CD for a while and have decided to install Ubuntu on my computer. But, I want it to duel boot with Windows. Also, since it is a family computer, Windows will need most of the disk space on the HDD. 
I'm not that tech savvy and all this talk of partioning and GRUB isn't making much sense to me.:confused: How can I install Ubuntu along side Windows on the same HDD while giving Windows most of the disk space? How do I choose which OS the computer boots? Any way to make it so that it boots Windows by default?
Please try to explain as much as you can. Complete newb here.
-Thanks!

First off, it gives you an option to free up some space in the hard drive for Linux. A Partition is space that the OS goes on and uses.
Next, GRUB is a boot manager that asks you what OS you want to use.
And, yes, we can help you have Windows boot up by default. Just install Ubuntu, and I (or 'we';)) will help you.

---

### Post by Aiello on 2007-08-21
Thanks for the info. So, basicly when the Ubuntu installer asks how you want to partion the disk, just click the first option and set it to how much disk space you want Ubuntu to have?

---

### Post by Aiello on 2007-08-21
Yes? No? Maybe?

---

### Post by ajgreeny on 2007-08-21
Another good guide here:  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Aiello on 2007-08-21
Yeah, I saw that one.
The things I was worried about was disk partioning and GRUB. But, it sounds like the Ubuntu installer takes care of partioning for you and all GRUB is is something that allows you to choose to run Windows or Ubuntu when you start the computer... I think.

---

### Post by MQMike on 2007-08-21
Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

(for setting Windows as the default and more)

And/or:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by stmiller on 2007-08-22
[IMG]http://www.mousqbaretous.com/Lanne2003/images/duel.jpg[/IMG]

---

### Post by pgar23 on 2007-08-22
see my signature for a video tutorial on dual booting. If you cant dual boot after this you probably also can work an electronic can opener. ONE THING THEY DONT MENTION ON HERE THO...when installing XP you must convert however many GBs of memory you want to MBs...one thing UBUNTU doesnt require.

GOOD LUCK

---

