---
title: "more dual booting"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by ScottMac on 2007-06-16
i would like some advice on how to set up my dual boot setup.

This would be the ideal setup for me. is this possible?
i have a 40gig ide hard drive that i want to install ubuntu onto. i have a separate 120gig serial ata that i would like to install windows onto. 

i intend to store most of my data on the windows hard drive and install ntfs-3g so i can work with all the files in ubuntu.
does it matter that one of the hard drives is sata and the other is not?

any advice on how i could set this up will be greatly appreciated.

thanks

---

### Post by overdrank on 2007-06-16
> **ScottMac said:**
> i would like some advice on how to set up my dual boot setup.

This would be the ideal setup for me. is this possible?
i have a 40gig ide hard drive that i want to install ubuntu onto. i have a separate 120gig serial ata that i would like to install windows onto. 

i intend to store most of my data on the windows hard drive and install ntfs-3g so i can work with all the files in ubuntu.
does it matter that one of the hard drives is sata and the other is not?

any advice on how i could set this up will be greatly appreciated.

thanks

Hi and welcome. I would install windows on a partition on the sata drive first  ( the partition size is up to you ) about 40gigs then install ubuntu on the sata drive about the same then use the additional space on both drive as backup and storage. But that is just my opinion. Good luck!:D

---

### Post by FleetAdmiral74 on 2007-06-16
I do not believe it matters which HD you install what OS on. 

And about the dual boot, go ahead and install Windows first. Then install Ub on the other HD. It should set up dual booting automatically, so no worries there.

---

### Post by ScottMac on 2007-06-16
thanks for the responses! Currently the 120 gig sata is partitioned into a 10 gig partition and a 110gig partition. the 10gig partition has all the windows files on it and the 110gig has all my games and music. ive already installed ubuntu on the 40gig ide.

what i would like to know is whether i will be able to dual boot if i just plug in both hard drives or do i have to format and reinstall? also what should the 40gig be set to ie master slave or cable select? 

when dual booting when do you select which OS you want to use?

---

### Post by FleetAdmiral74 on 2007-06-16
> **ScottMac said:**
> thanks for the responses! Currently the 120 gig sata is partitioned into a 10 gig partition and a 110gig partition. the 10gig partition has all the windows files on it and the 110gig has all my games and music. ive already installed ubuntu on the 40gig ide.

what i would like to know is whether i will be able to dual boot if i just plug in both hard drives or do i have to format and reinstall? also what should the 40gig be set to ie master slave or cable select? 

when dual booting when do you select which OS you want to use?

I will try to answer as best I can...

1) Make sure both HDs are plugged in and Windows already installed before you install Ubuntu, otherwise it will not pick up the other windows OS and will NOT auto set-up the dual boot.

2) Not sure about xp, but when installing ubuntu it lets you format and install pretty much in one step, its pretty user friendly. It shows you all the partitions and what not visually so you know what you are doing.

And you choose a bit after your bios loads. Think about when XP normally loads (or starts loading). At that time it will just give you a list instead to choose from.

Oh, and I have always prefered one master and one slave HD. Not sure about that cable select stuff...

EDIT: So the 40gig drive you want all ubuntu, you want windows on the 120 drive, but that is already partitioned with data? might need to back that up first...if I understood right, that is.

---

### Post by louieb on 2007-06-16
How is the 40 gig drive set now? 
Plug in the larger drive and reboot. If Ubuntu comes up then its just a matter of configuring GRUB to boot windows. IF windows comes up then its a little more involved. but first just plug the second drive in and get back with what happens.

---

### Post by overdrank on 2007-06-16
> **ScottMac said:**
> i would like some advice on how to set up my dual boot setup.

This would be the ideal setup for me. is this possible?
i have a 40gig ide hard drive that i want to install ubuntu onto. i have a separate 120gig serial ata that i would like to install windows onto. 

i intend to store most of my data on the windows hard drive and install ntfs-3g so i can work with all the files in ubuntu.
does it matter that one of the hard drives is sata and the other is not?

any advice on how i could set this up will be greatly appreciated.

thanks

HI if you had the drives set up already the way you want them then why ask this question. Just ask how the best way to configure the drives for dual boot! :-k
And I agree with Louieb

---

### Post by ScottMac on 2007-06-16
Overdrank: i thought that you had to reinstall windows and ubuntu to get a dual boot to work but if i dont have to reinstall windows and ubuntu then i would much rather do that :)

ok i plugged both hard drives in but the computer automatically boots into windows and doesn't give me a choice. In my bios the 120gig is the channel 0 slave and the 40gig is the channel 1 master. 
 
This is without reinstalling ubuntu on the 40 gig.

let me get this right... if i leave the install of windows but reinstall ubuntu on the 40gig while it is in the same computer, it should pick up that i want to dual boot??

---

### Post by louieb on 2007-06-16
Ok since you can't switch you boot order in BIOS. You need to point the MBR of your sata drive to the grub program (statge2) on your Ubuntu install. See the Reinstall GRUB link in my signature. or Check out the Dual Boot link and the section on the Super GRUB Disk. Both should work. I do like the Super Grub Disk its a neat tool to know how to use.
 
> let me get this right... if i leave the install of windows but reinstall ubuntu on the 40gig while it is in the same computer, it should pick up that i want to dual boot??
 
Oh and YES it should automaticly setup dual boot is the answer to that question.

---

### Post by ScottMac on 2007-06-17
ok i reinstalled grub but when i boot up grub loads up but gives me error 17: unable to mount partition or something like that?? is this because i installed grub to the wrong partition? im thinking of just reinstalling ubuntu but will it still work now that i have attempted to reinstall grub already?

thanks

---

### Post by ScottMac on 2007-06-17
ok ive read up a bit more and now realize that grub didnt recognize my partition or filesystem type...

grub> find /boot/grub/stage1
(hd1,0)

ok working so far...

grub> root (hd1,0)

no output... it just goes back to grub>

Will a reinstall of ubuntu do the trick for me??

---

### Post by Dedoimedo on 2007-06-17
Hello,

First, try this little gem for fixing Grub:

Super Grub Disk
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

No need to reinstall Grub.

Second, more on dual boot, try this:
[http://www.dedoimedo.com/computers/dual_boot.html](http://www.dedoimedo.com/computers/dual_boot.html)

Dedoimedo

---

### Post by ScottMac on 2007-06-17
well ive yet to successfully dual boot ubuntu and windows...
i tried to use super grub disk but i think i messed up something when i initially tried to reinstall grub. so i formatted and reinstalled windows and ubuntu in that order. grub 1.5 loads fine and windows boots perfectly. ubuntu begins to load but stops while it is loading up and begins to check the disk it is on for errors. the test fail and it reboots... 

should i just reinstall ubuntu again or am i on a hiding to nothing

thanks for your continued interest

---

### Post by logos34 on 2007-06-17
> grub 1.5 loads fine and windows boots perfectly. ubuntu begins to load but stops while it is loading up and begins to check the disk it is on for errors. the test fail and it reboots...

When the grub menu comes up, select the main ubuntu kernel then hit 'e' key to edit.  If the root line reads 'root (hd0,0)' change it to 'root (hd1,0)'.  (assuming / (root) is hda1.  Hit 'enter' and then 'b' to boot it or hit esc to go back and hit enter on the highlighted entry.  If it gets linux to boot then make the change permanent by editing menu.lst.

---

### Post by ScottMac on 2007-06-17
ok wow this is weird... i tried to boot ubuntu twice and it failed both times. i then read logos34 post and checked that it was root (hd1,0) which it was and then restarted and now the dual boot works fine. in other words i didnt change anything and now it works! oh well im not going to question the mystical working of the ubuntu juju power...

---

