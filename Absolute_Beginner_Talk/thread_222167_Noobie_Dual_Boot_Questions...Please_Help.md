---
title: "Noobie Dual Boot Questions...Please Help"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by magnoliablossom on 2006-07-24
Hi.  I just tried to install ubuntu on my computer to boot with windows.  Anyway when all the partitioning went fine.  I d/l'ed the sys rescue cd, did the qtparted and all went fine...went back in Windows to make sure it still worked, it did...but had to do it's little check because the file structure had changed and it was a little miffed i gave more room to ubuntu...heheheh...at any rate, when it finished it's thang, i restarted, put in the livecd (love it btw) and then proceded to install it.  here we come to my problem....

when it goes to the partitioning screen in the installation process, it lists my windows partition as well...when i go to the next screen to assign which partition will be used for what, it tells me have to select something for the windows partition as well....is there something i'm not doing?  i'm not *trying* to select my windows drive, but it's not really giving me an option to omit it so i just cancel the install.  i don't want to corrupt my windows...although i have a back up copy of, it's a pain in the ummm wellllll....to reinstall.

any nudge in the right direction to get past this particular issue would be greatly appreciated. :)

---

### Post by Paerez on 2006-07-24
It will most likely try to get you to put it at "/media/windows" or something. Thats ok, that just means that when you are in ubuntu, if you go to /media/windows you can see your windows files. Just make sure it DOES NOT say "Format" on the windows partition :D

---

### Post by reacocard on 2006-07-24
you shouldn't have to mount it. If i remember correctly, just click the little arrow next to the partition (not the mount point, the partition), and make it blank. if this doesn't work, just go ahead and let it be mounted. you can always change it after Ubuntu is installed.

---

### Post by magnoliablossom on 2006-07-24
so...if i am understanding you correctly, it's alright that it's there in the list, just leave it at media windows and continue on my merry way with the installation...

sorry i don't mean to sound like an idiot.  i'm just trying to be sure i understand before preceding.

---

### Post by Paerez on 2006-07-24
no problem. It is definitely something to be careful about. I nuked my windows back in the day with Mandrake, and since then I am extremely careful with partitioning.

---

### Post by magnoliablossom on 2006-07-24
okie dokie....if i don't return within the next hour or so, send out the search parties. :P  thanks for the help....here it goes!!!!!! lol

---

### Post by magnoliablossom on 2006-07-24
Send in the troops....Attempted to install ubuntu for dual boot...all went well throught out install with defined partitions.  played around in ubuntu for a little while trying to figure out how to configure modem...couldn't do it so thought "no problemo"...restarted system, chose to boot to windows when suddenly encountered the dreaded "Blue Screen"...It may have been my imagination, but could almost swear I heard softly emitting from my speakers the familiar sinister laugh of Bill Gates chanting "you're not going to get away that easily"...trying not to  panic i then rebooted machine and chose to go in under "Safe Mode"....same "Blue Screen", more evil snicking...Gritted my teeth and proceded to pop in the XP cd and rebooted my machine....After a shower, doing my hair, giving myself a facial, then picking mosquitoes out of my citrus facial mask, checked progress of XP installation...Cooked dinner, fed kids, washed dishes, checked progress of XP installation....Finally came to the part where you put in your validation or whatever codes...sat there, filed nails, removed nail polish, repainted nails, and finally have been able to get back on the internet...Am thinking of trying once again without pre-creating the partitions and allowing the ubuntu installer to do it...However there are a couple of strange goings on with Windows...

1.  Windows is reporting a hard drive 30 gigs smaller than actual size (160 gig hard drive).
2.  Windows creates partition not starting at beginning of drive.  There is less than one gig of unused space before Window's partition.
3.  Windows obliterated ubuntu in reinstallment...It didn't even see the partitions created by sys rescue disk.

If chosing the option in the partioning portion of the livecd of letting ubuntu install on the continuous unused portion, will it attempt to install on that itty bitty bit left by Windows or will it attempt to do so on the much larger unused portion?

To navymom, I feel your pain.  I have a lucent winmodem as well and I got as far as:

$ sudo modprobe ltserial
$ sudo modprobe ltmodem

However when I did the first line, I received the following error:

FATAL:  Error inserting ltserial (/lib/modules/2.6.15-23-386/ltserial.ko): Invalid argument

As for the modem problems master Ubuntis, what are your suggestions?

If I had any hair left, I'd be blonde ](*,)

---

### Post by confused57 on 2006-07-24
You & navymom may want to consider an external serial dialup modem.
I'm giving an old computer to someone who has dialup, and (fortunately?) the internal modem is US Robotics, which  definitely does not provide a Linux driver.  I've taken the easy way out and ordered a Trendnet TFM-560X from buy.com for $33(free shipping)...it's supposed to be Linux compatible.
It'll be a few weeks before I can try it, but hope it works...I'm mainly worried about their ISP, peoplepc.com and Linux.

---

### Post by magnoliablossom on 2006-07-24
okie dokie.  i can give up on the modem for now but i can't give up on the dual booting or i won't have any internet until i can get a new modem.  

as the dual booting and partioning, i've followed the instructions from a couple of installation guides step by step but i still get the blue screen.  so i'm left with two options, either figure out where the problems lies and resolve it or just trash ubuntu.  i really don't want to do that because from what i've seen, i like it.  will continuous formating and reformatting hurt your hard drive?  because if it could then i may just have to give up.  every time i get ubuntu installed (i've done it twice now) i get the blue screen when i go back to load windows.  every time it happens, i have to again reformat and reinstall windows.

---

### Post by confused57 on 2006-07-24
If you can boot into Ubuntu, open a terminal:

```
cat /etc/fstab
```
and
```
sudo fdisk -l
```
The -l is a small "L"

This will tell show your partition table.

---

### Post by magnoliablossom on 2006-07-24
ok but what is that supposed to help me with?  right now i don't have ubuntu on my computer.  i've had to do another reformat/installation of windows.  i can't get on the internet with ubuntu to get help because of modem issues.  but i can't have windows and ubuntu on my computer because i get the blue screen.  i'm doomed. :(

---

### Post by confused57 on 2006-07-24
> **magnoliablossom said:**
> ok but what is that supposed to help me with?  right now i don't have ubuntu on my computer.  i've had to do another reformat/installation of windows.  i can't get on the internet with ubuntu to get help because of modem issues.  but i can't have windows and ubuntu on my computer because i get the blue screen.  i'm doomed. :(
I thought it might have been possible that grub was not pointing to the correct partition to boot Windows, for example the 1 Gb partition prior to Windows...I don't know, but I was hoping the commands would help determine that.
Also, do you have an option in bios to enable LBA?

---

### Post by magnoliablossom on 2006-07-24
> **confused57 said:**
> If you can boot into Ubuntu, open a terminal:

```
cat /etc/fstab
```
and
```
sudo fdisk -l
```
The -l is a small "L"

This will tell show your partition table.



okay, i'm going try this....but it's important i know what i need to do to redirect the it to boot from the correct partition because if windows is a butthead again i won't be able to come back until i've done another restore *sigh*...i'm not sure though it that will help....the first section is just free and not a partition at all.

sorry, i would have replied sooner but i left to defrag (4 times), shrink my windows partition, and rebooted 4 times to make certain that windows was happy with the new partition.  as for the question about the BIOS, what is the LBR and if i do have it what do i need to do with it?

someone please tell me this is worth it....i know i've seen all over the places that's not that hard to install, but i've followed every tutorial/wiki doc/and whatever i can find that sounds like it may apply to my system but i still keep getting that blue screen. ](*,)

---

### Post by confused57 on 2006-07-24
I'm really sorry you're having so many problems...if you haven't started already, you may want to take a break for a little while, come back and try  it later.
What I suggested may or may not help, I'm not sure it's worth it right now, I can imagine your frustration.
LBA is for bios to recognize large hard drives, some older bios do not support LBA, but if yours does, it wouldn't hurt to enable it.
What kind of computer are you installing on, system specs?
Good Luck

---

### Post by magnoliablossom on 2006-07-24
lol i think i'm going to take your advice on the break.  my cousin is the one that told me about and gave me a copy of her cd.  she had no problems installing the dual boot.  i've had nothing but problems and the hussy ain't no where around to tell me what it was she did to do hers. lol

---

### Post by gigaferz on 2006-07-24
It happened to me..and I was really careful..the partitioner on the live cd   messes up the windows partition..I had everything planned...Using the live cd on system, administration, then gparted..REsized the windows I had 3 partitions for ubuntu..
I messed up the root size I had  3gb..and after automatix I could not log in ubuntu..later I tried windows...Nothing..not even a blue screen...
partitioned, reformated..etc..etc...The hard drive was useless..

 until I formatted with  Bart PE  I formatted the hard drive..then finally the windows installation disks worked...

I think that is better to create the linux partition under windows..then install ubuntu on that..

---

### Post by Frank Golden on 2006-07-24
> **magnoliablossom said:**
> lol i think i'm going to take your advice on the break.  my cousin is the one that told me about and gave me a copy of her cd.  she had no problems installing the dual boot.  i've had nothing but problems and the hussy ain't no where around to tell me what it was she did to do hers. lolOkay since you are reformating wipe your drive
completely and create a NTFS partition big enough for XP and
your programs at beginning of drive . Leave the rest of drive
unallocated or make a Fat32 storage partition. This can be used to share files between XP and Ubuntu. Mke sure you have at least 10GB unallocated (free). After installing XP boot to the LiveCD
(I'm assuming you are using the final Ubuntu 6.06 LTS desktopCD)and choose to install from the live CD desktop. When asked about
where to install choose the option to install in the largest free
space. Ubuntu will create a ext3 partition and a ext2 swap
partition on the unallocated space and install itself.
During install GRandUnifiedBootloader (GRUB) will configure itself setting up our boot menu. You can change bootorder
from Ubuntu to have XP boot first. Ubuntu is the default.
The file you edit is /boot/grub/menu.lst

---

### Post by confused57 on 2006-07-24
> **magnoliablossom said:**
> lol i think i'm going to take your advice on the break.  my cousin is the one that told me about and gave me a copy of her cd.  she had no problems installing the dual boot.  i've had nothing but problems and the hussy ain't no where around to tell me what it was she did to do hers. lol
Your cousin is probably out on the town living it up, leaving you on your own.
The post by Frank Golden sounds like the best approach, not that he needed my endorsement, just wanted to point it out.

---

### Post by magnoliablossom on 2006-07-25
LMAO...I wish I had seen that two hours ago...before I had done the reformat....I'll try it again tomorrow...maybe i'll try it again tomorrow...i don't know...honestly i'm getting a little fed up with it...for some it may be easy but for me it's been nothing but a pain in the bum....seriously i would love to have it but apparently it just does not like me and i'm a little concerned that all this reformatting isn't good for my hard drive.


> **Frank Golden said:**
> Okay since you are reformating wipe your drive
completely and create a NTFS partition big enough for XP and
your programs at beginning of drive . Leave the rest of drive
unallocated or make a Fat32 storage partition. This can be used to share files between XP and Ubuntu. Mke sure you have at least 10GB unallocated (free). After installing XP boot to the LiveCD
(I'm assuming you are using the final Ubuntu 6.06 LTS desktopCD)and choose to install from the live CD desktop. When asked about
where to install choose the option to install in the largest free
space. Ubuntu will create a ext3 partition and a ext2 swap
partition on the unallocated space and install itself.
During install GRandUnifiedBootloader (GRUB) will configure itself setting up our boot menu. You can change bootorder
from Ubuntu to have XP boot first. Ubuntu is the default.
The file you edit is /boot/grub/menu.lst

---

### Post by Hotwhlz85 on 2006-07-27
"I think that is better to create the linux partition under windows..then install ubuntu on that.."

I second this!!  I had all sorts of formatting problems.  During the install Ubuntu wanted to completely erase my HDD.  The only options I was given was "either let me erase it or you format the sucker manually".  So I booted back into Windows and shrunk the Windows partition using Partition Magic.  This left a huge chunk of unallocated space on my hard drive.  Booted back into the LiveCD, clicked on istall, and Ubuntu loved the space I had set aside for it.  It happily installed itself and the rest has been awesome.

I rarely boot into Windows now (I've been up and running on Ubuntu for a little over a week) and don't see much use for Windows now.  

Best of luck to ya!

Ron

---

