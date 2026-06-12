---
title: "No boot into Ubuntu 9.1 Install CD"
date: 2010-03-03
forum: Apple Hardware Users
---

### Post by gabyx on 2010-03-03
Hi all
I have a very urgent problem, its so bad I dont know what to do...
I tried to install a dual boot, (os x and ubuntu). I could always boot with the Ubuntu CD, but now I can try everything (format whole HD to *free space* )  press "C"  at start up,  press "alt" and choose "windows"  (ubuntu cd)  everything does not help even resetting PRAM with alt+P+R

what I get is a BLAC SCREEN with blinking underline (always)


Does anyone know what I can do to make my mac again able to install a ubuntu, it seems I ahve messed up my firmware..?¿ I just dont know how? (I once overwrote my MBR according to a thread here... (but I reformated now the whole HD to freespace with GUID partition table.....
but still blinking underline when I want to boot the ubuntu 9.1 cd.

Its such crap.... =(

Thanks for any help or advice!!!

Gabriel

---

### Post by linuxopjemac on 2010-03-03
which machine do you use ?

---

### Post by gabyx on 2010-03-04
I have found the problem,

Restarting in Os X, then shutdown , dooo not restar!!!, then press power button, press "C" , this will again boot Ubuntu and any linux!

It happend that I never did a Shutdown, instead I did restars and this caused my mac not to boot anymore correctly from Ubuntu or any other Linux CD/DVD

SO always restart in Os X and Shutdown then start your mac from the CD
THAT was my workaround


Thanks alot! :-)

If someone has problems with this, post here

---

### Post by gabyx on 2010-03-04
I have NOT solved it yet!!

They way above just seemd to solve it but on my IMAC8,1  (Duo Core2) (early 2008) , this morning it worked, installed ubuntu on ext2 on the second partition after os x, and when I want to boot again with the live cd,,

---> black screen blinking underline.... same **** as always


Has anyone an idea?

Thanks

---

### Post by linuxopjemac on 2010-03-04
why don't you boot the hard drive after installation ?

---

### Post by madscientist032 on 2010-03-04
How did you format your harddrive into two partitions? I recommend you use Boot Camp to format it correctly into two partitions. 

Once Boot Camp finishes the partitioning process, insert the Ubuntu Live CD and restart your iMac. **Hold down the ALT key *after* the start-up chime plays. DO NOT release it until you see "Macintosh HD" and "Windows CD"** Once you see that, select the "windows cd" and press enter. 

Your iMac should now boot from the Ubuntu Live CD.

---

### Post by linuxopjemac on 2010-03-04
good idea,
install [rEFIt]("http://refit.sourceforge.net/"). Then sync your partition with partition tool , then reboot and then select legacy os.

---

### Post by madscientist032 on 2010-03-04
Yeah - using Boot Camp is the easiest way to install Ubuntu. The best part is that the partition Ubuntu is to be installed onto is relatively obvious. 

Easier to install Ubuntu on a Mac than it is to dual-boot on Windows, IMO. :D

---

### Post by gabyx on 2010-03-09
SOLVED STRANGED PROBLEM:


The problem was that my mac when presse "c" could not start anymore from CD ( blinking underline)

Actually after POWER OFF of the IMac I could again boot from the CD normally with "c"

I think above the blinking underline stand "Missing Operating System"  BUT I could not see it, so it tried to boot still from the installed Ubuntu even when I pressed "C" (probably a BUG)...

I booted from OpenSUSE CD then selected reboot from harddisc --> then I rebooted into GRUB (FINALLY :-)  could chose UBUNTU , logged into UBUNTU --> did a grub-update in the console and then it worked properly, so I could now choose from "Boot Legacy HD" in refit  boot into GRUB ---> BOOT UBUNTU --> SOLVED
but after installation of UBUNTU (correct installation , corrrect partitioning, ) I could no boot into GRUB... with refit by selecting  "Boot Legacy HD" , only after I updated grub (deinstalled it and installed it again, with synaptic package manager)  I could finally boot into GRUB from REFIT

---

### Post by madscientist032 on 2010-03-09
Pressing 'C' after the Boot Chime lets you boot from the inserted CD. 

Holding 'ALT' after the boot chime lets you see what partitions / bootable media you can boot into.

Glad to see we helped you.

---

### Post by Atilana on 2010-03-10
why don't you boot the hard drive after installation, i think is the best you can do!

---

