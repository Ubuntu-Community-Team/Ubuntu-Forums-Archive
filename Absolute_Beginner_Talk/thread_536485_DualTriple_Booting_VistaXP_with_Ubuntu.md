---
title: "Dual/Triple Booting Vista/XP with Ubuntu"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Andrew Garn on 2007-08-27
I have 2 320gb SATA Hard Disks.

I want to either dual boot vista with ubuntu or:

triple boot vista and xp with ubuntu

------------

There are lots of guides to this however I only want my ubuntu partition to take up around 20gb of space from one of the disks, as I will be primarily using windows vista for work and ubuntu for experimenting with.

So which order do I install the os in and what partition sizes do i create?

thanks

---

### Post by Caton420 on 2007-08-27
WINDOWS FIRST!!! wow that was what i KEPT messing up on lol, windows uses an NT Bootloader (or other) while linux uses Grub Bootloader (or other) and you want to use the grub bootloader, it lets you boot windows and linux rather than just windows, well unless your into a ton of worthless work :)
Have fun linux rocks for a hobby
*EDIT* Ubuntu comes with Grub :)

---

### Post by Andrew Garn on 2007-08-27
i know windows overwrites the mbr but i thought linux was better for creating the partitions i need to install the OS's.

Still would like to know how to create the partitions what sizes and how many :)

---

### Post by Caton420 on 2007-08-27
i personally made 1 part. for xp in the xp installer and left the rest as free space, then in ubuntu installer allowed me to parition, it comes up automatically... ps the Swap partition should not be huge like mine was its mostly for the install so 2-4gb or so

---

### Post by Majorix on 2007-08-27
Hey Andrew!

You can dual boot Ubuntu with XP or with Vista, no problems. Even though I have never tried it myself, a triple boot should be possible too.

To do a dual boot, pop in your XP (or Vista CD) into the drive and hit a key when it says if you want to boot from the disk.

Once in there, hit next (and you have to agree on a license too) until you get to the partitioning screen. There delete all partitions. Then create a new partition the size of your hard disk (was it 320) minus 20gbs. So you leave 20 gb for Ubuntu and take the rest (300gbs) for Windows. Make sure you don't format the Ubuntu partition in any way, just leave it untouched.

Then when you are done installing Windows, put in the Ubuntu LiveCD. I suggest you go with 7.04 at this time, as 6.06 is too old and 7.10 is too shaky at this time. Once you boot into Gnome, select Install and answer the few questions until you reach the partitioning screen. There, choose "use the largest continuous free space" and Ubuntu will automatically use that 20gb space to create the swap partition and the linux partition. It should be easy.

Finally, when you reboot after done with Ubuntu, you will be asked which OS you want to boot. Choose whichever you want and you will be booted into that OS.

GRUB by default boots Linux partitions first. To overcome that you have to play around with your boot.lst. Though I forgot exactly what you had to change there. Maybe a kind person here will help you on that.

Good luck.

---

### Post by Andrew Garn on 2007-08-27
> **Majorix said:**
> Hey Andrew!

You can dual boot Ubuntu with XP or with Vista, no problems. Even though I have never tried it myself, a triple boot should be possible too.

To do a dual boot, pop in your XP (or Vista CD) into the drive and hit a key when it says if you want to boot from the disk.

Once in there, hit next (and you have to agree on a license too) until you get to the partitioning screen. There delete all partitions. Then create a new partition the size of your hard disk (was it 320) minus 20gbs. So you leave 20 gb for Ubuntu and take the rest (300gbs) for Windows. Make sure you don't format the Ubuntu partition in any way, just leave it untouched.

Then when you are done installing Windows, put in the Ubuntu LiveCD. I suggest you go with 7.04 at this time, as 6.06 is too old and 7.10 is too shaky at this time. Once you boot into Gnome, select Install and answer the few questions until you reach the partitioning screen. There, choose "use the largest continuous free space" and Ubuntu will automatically use that 20gb space to create the swap partition and the linux partition. It should be easy.

Finally, when you reboot after done with Ubuntu, you will be asked which OS you want to boot. Choose whichever you want and you will be booted into that OS.

GRUB by default boots Linux partitions first. To overcome that you have to play around with your boot.lst. Though I forgot exactly what you had to change there. Maybe a kind person here will help you on that.

Good luck.

Very helpful thanks

so do i unplug the 2nd disk during my installations? then format it to fat 32 after i finish installing the operating systems?

---

### Post by Caton420 on 2007-08-27
no need

---

### Post by Andrew Garn on 2007-08-27
> **Caton420 said:**
> no need

if its unplugged i can be sure what i'm partitioning :)

---

### Post by Caton420 on 2007-08-27
oh lol, if you think you may accidentally part the wrong drive then i advise you to unplug it yes

---

### Post by Andrew Garn on 2007-08-27
Another Question: If i format the 2nd disk as FAT32 will ubuntu be able to read/write to it as well as vista/xp?

---

### Post by Caton420 on 2007-08-27
im using NTFS i can read/write straight after install(7.04 i believe? the newest release), infact it was a drive on my desktop :) idk about fat32 personally but iv heard yes it can

---

### Post by akiratheoni on 2007-08-27
Well if I were you, I would probably give more than 20GB to your Ubuntu partition, or put your /home directory on a larger partition... when I originally installing Ubuntu, I was thinking I'd be the same as you, using Vista more but using Ubuntu as experimental, so I partitioned my 500 GB so Ubuntu only got about 15GB. Now, I'm using Ubuntu a lot more and wished I had more space for my Ubuntu install instead of Vista :(

Lol, that's my unhelpful 2cents. :P

---

### Post by Andrew Garn on 2007-08-27
so linux can read off a vista ntfs partition then?

as for the linux space issue: i wanted to use linux for dvr with a tv capture and digital tv reciver card.

but if i can copy files to the windows partitions once they are created surely space is irellevant on ubuntu partition?

---

### Post by akiratheoni on 2007-08-27
Yeah, and you can get an program to write to NTFS partitions. I don't know what the name is, though.

---

### Post by Caton420 on 2007-08-27
its true i suddenlly find myself using linux (ubuntu obviously) 95% of the time, i didnt see that comming as a windows user

---

### Post by Caton420 on 2007-08-27
> **Andrew Garn said:**
> so linux can read off a vista ntfs partition then?

as for the linux space issue: i wanted to use linux for dvr with a tv capture and digital tv reciver card.

but if i can copy files to the windows partitions once they are created surely space is irellevant on ubuntu partition?

yup worked right out of install, no need for extras in my case but if you do for some odd reason its a 2 second download and install process
also if your into video editing like me its fairly easy to emulate MAC on a linux box from what i hear... no experience though i cant wait to try

---

### Post by Andrew Garn on 2007-08-27
what do you use linux for?

and surely if linux can read off and copy to windows partitions but windows cannot read off linux surely a better idea to give the space to windows?

i have a lot of recorded tv shows/music that i would want to be watchable/listenable on both os's

---

### Post by Andrew Garn on 2007-08-27
> **Caton420 said:**
> yup worked right out of install, no need for extras in my case but if you do for some odd reason its a 2 second download and install process
also if your into video editing like me its fairly easy to emulate MAC on a linux box from what i hear... no experience though i cant wait to try

i was going to use an open source pvr program such as MythTV i hadnt considered video editing yet

---

### Post by Caton420 on 2007-08-27
> **Andrew Garn said:**
> what do you use linux for?

and surely if linux can read off and copy to windows partitions but windows cannot read off linux surely a better idea to give the space to windows?

i have a lot of recorded tv shows/music that i would want to be watchable/listenable on both os's

i use linux as my primary os (very suddenly if you ask me... youll see its like an addiction lol)
well i guess your second question is completely up to you, sending large amounts of data drive to drive can take a very long time believe it or not (it took abouth an hour or 2 to transfer 2 or 3 dvd video folders) so it all depends

hope this helps

---

### Post by Andrew Garn on 2007-08-27
> **Caton420 said:**
> i use linux as my primary os (very suddenly if you ask me... youll see its like an addiction lol)
well i guess your second question is completely up to you, sending large amounts of data drive to drive can take a very long time believe it or not (it took abouth an hour or 2 to transfer 2 or 3 dvd video folders) so it all depends

hope this helps

it does thanks :)

data still copying to disk at the moment so i'm still here for a while incase anyone has some more suggestions for me

---

### Post by Caton420 on 2007-08-27
your installing windows right now or ubuntu?
do you have 2 computers set up or somthing? if so do you have AIM on it?

---

### Post by Andrew Garn on 2007-08-27
> **Andrew Garn said:**
> it does thanks :)

data still copying to disk at the moment so i'm still here for a while incase anyone has some more suggestions for me

by the way my computer came preinstalled with vista business  and oem serial on the top

can i reinstall with my serial using a standard windows vista business dvd?

---------

2 pcs side by side, and i'm copying the files i want to keep off this one, 3minutes left of that i can start to format, and i have msn messenger on them but not aim

---

### Post by Caton420 on 2007-08-27
umm i dont beleve so.. but go ahead and try, worst to worst you still have like 30days with out it
ps did u see post above?

---

### Post by Andrew Garn on 2007-08-27
> **Caton420 said:**
> umm i dont beleve so.. but go ahead and try, worst to worst you still have like 30days with out it
ps did u see post above?

yes i edited my post to reply to yours

so how do i reinstall vista then?

---

### Post by Caton420 on 2007-08-27
wuts msn sn?

---

### Post by Andrew Garn on 2007-08-27
i pmed it to you

i just checked and my vista serial works on the vista business dvd i have.

---

### Post by Caton420 on 2007-08-27
msn is giving me far too much trouble im sorry if u ever get aim i pmed my aim sn

---

### Post by MQMike on 2007-08-27
I’m late to this, but this how-to seems fail safe.
Vista   ***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

---

### Post by Andrew Garn on 2007-08-27
> **MQMike said:**
> I’m late to this, but this how-to seems fail safe.
Vista   ***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

cheers, i had that site open already :)

---

