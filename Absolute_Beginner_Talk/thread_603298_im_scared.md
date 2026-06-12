---
title: "im scared"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by gubemton on 2007-11-05
i had a virus on windows so i though id install ubuntu. So i already had 2 partitions, one with windows and one with a few files (ntfs). So i installed ubuntu on what i believed it displayed as partition 2 (ubuntu7.10). BUT it installed and it displayed an error saying it ran out of space. I shat myself. Im pretty sad right now,  becusei dont know what todo, the windows wont start up and when i use livecd ubuntu to try and acess the "unmounted ntfs volume" it says its unmounted and needs to be mounted and it mentions using ntfsfix or something. Please help me, all my photos and videos were on it, and if they are lost, is there any way i can use software to bring them back? Please, )=

thanks

p.s not disapointed in ubuntu

---

### Post by Meomix on 2007-11-05
use the ubuntu live cd to hack into the windows partition and collect your files into a cd
this requires that you have 2 CD drives in your computer since the ubuntu live cd takes up one drive

---

### Post by gubemton on 2007-11-05
how? it wont let me

---

### Post by quinnten83 on 2007-11-05
which live cd version are you using?
 is ntsf-3g installed, this is the only way to read NTFS drives.
Install ntfs-3g go to Applications> add/ remove, type in the search field: ntfs. The option that appears install it.
go then to places, computer. You should now be able to see the NTFS drives.
if you don;t have a cd, i hope you have a memory stick or external (usb) harddrive you can copy to.

there are several other tools you can use to check why your windows won't start on the live CD.
are you getting an error message when windows is starting? Is GRUB starting?
tell us what errors you are getting...

---

### Post by gubemton on 2007-11-05
im on 7.10 live cd
and i havent tried that. 

but, ubuntu didnt even proerly install,
so i was left with a unclean install
no grub, just it says os is corrupted and all

any tool to recover the data i lost after i format?

---

### Post by gubemton on 2007-11-05
i installed ntfs 3g, made no difference, it just says cannot mount volume

---

### Post by TeaSwigger on 2007-11-05
Don't be scared, just patient, you'll get it :) If you want to try recovering the existing installs, please be as specific as you can so someone might best be able to help. 

If the whole disc is reformatted, you can't recover anything. So proceed methodically here. If you have things you want to try to recover: You can boot the computer to the live CD, and it is able to read and write to your hard drive. You may need to install the package ntsf-3g as quinnten83 described above in order to access the windows portions of that hard drive. Then you can copy what you want to another CD if you have two drives, a USB card or whatever. When you are done, if you want to reinstall windows, do that next, then return to the live CD and try installing.

Besides the ubuntu sites and wikis etc, there is a lot of information here:
[http://ubuntuguide.org/](http://ubuntuguide.org/)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
and here:
[http://www.psychocats.net](http://www.psychocats.net)
You might want to bookmark them for reference.

---

### Post by jaybombalous on 2007-11-05
u said in your original post, u installed ubuntu to what u thought was partition 2. Yep you sure did and that partition was the NTFS drive u are talking about that has all your pics and what not, thats why it is to small for the OS. Wanna bet??? :(

what u can do is probably download 'supergrub rescue disk' boot to that, rewrite the windows MBR and reboot to windows, the sad part is u will not have the NTFS pictures partition.

At least if I understand u correctly.

---

### Post by jaybombalous on 2007-11-05
you could also make a bootable cd of puppy linux. U can load this OS into RAM so u can use the cd rom for other things (burning data) after say u installed the ntfs driver (not sure if thats possible in puppy, but I don't see why not).

I have a *.iso image u can burn to CD to do all these things I am talking about, but I am not sure how u are gonna d/l it. How are u accessing the Internet now?

---

### Post by gubemton on 2007-11-05
well, when i installed ubuntu, i used guided mode and it was going to use my second partition which had like 12 gigs, at 77% it got stuck and said it didnt have enouigh space. Then when i booted up it said corrupt OS and if i boot into ubuntu live cd i there are three drives, and one says 99 gb unmounted volume or something and when i try and acess (after installing ntfs 3g) it still says the drive is unmounted and was not correctly mounted because of shutdown or something. It says to unmount it through windows but that isnt exactly happening either. What if i installed windwos in the second partiton, if it still exists?

---

### Post by jaybombalous on 2007-11-05
can u download torrents and burn *.iso images to CD?

If so then use this...

[http://thepiratebay.org/tor/3873673/supergpartpuppy.iso](http://thepiratebay.org/tor/3873673/supergpartpuppy.iso)

boot up and use supergrub option and then do a windows MBR repair option AUTO is preferable.

U don't wanna go and install a new OS from scratch if u don't have too.

---

### Post by mlentink on 2007-11-05
If I were you, I'd try and recover anything I possibly could. Which means not writing anything to that disk, let alone install an os on it. 
Use a help-disk like [SuperGrubDisk]("http://supergrub.forjamari.linex.org/") or [Ultimate Boot CD]("http://ubcd.sourceforge.net/download.html") to try and access the data, salvage it to DVD or another (USB?) disk and only then perhaps install a new OS

---

### Post by steve.horsley on 2007-11-05
I agree with not writing anythong more tho the disk until you are sure where you stand.

First, I would try and find out what partitions are on the disk. From the Ubultu live CD, you can open Accessories->Terminal and entehr this command:
**sudo fdisk -l**
which will tell you what partitions are there. 

At the moment, I think the worst possible thing might be that there was something like a hidden (to windows) recovery partition like the dell utility partition that's on my laptop. That makes the windows partition into partition 2 which is the one you say you tried to install onto. Lets hope this isn't the case.

---

### Post by fourthdimension on 2007-11-26
Heirens Boot CD works great.  Tons of recovery tools.  I'm not sure where it stands as far as legality goes, though...

---

### Post by skymera on 2007-11-26
heh is that a joke?

---

### Post by candtalan on 2007-11-26
> 
First, I would try and find out what partitions are on the disk. From the Ubultu live CD, you can open Accessories->Terminal and entehr this command:
**sudo fdisk -l**
which will tell you what partitions are there. 


Do not be scared. Just go slowly at the moment and do not panic.
Using the above instructions to get information about your partitions is a good approach -take it gently, and let us know what is shown?

---

### Post by skymera on 2007-11-26
if you read, this is from 3 weeks ago, the guy above me dug it back up,
with what seems to be a joke :lol:

i cant try as im in windows atm.

---

### Post by fourthdimension on 2007-11-26
??  [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

---

