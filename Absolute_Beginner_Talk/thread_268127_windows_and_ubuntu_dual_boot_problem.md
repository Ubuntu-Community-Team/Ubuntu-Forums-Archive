---
title: "windows and ubuntu dual boot problem"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by y3ahright on 2006-09-29
ok i dual booted my ubuntu and windows last night. So this is the first day i am using ubuntu. So i wanted to go back to my windows XP PRO OS so i restart and get  this 

Booting 'windows Nt/2000/XP (loader)'
root (hd0,0)
filesysem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

it will just sit there and do nothin.
anyone know what i can do other than reinstall cuz it will take forever to back-up my stuff and reinstall thx

---

### Post by bulldog on 2006-09-29
Can you give me the outcome of```
sudo fdisk -l
```l is as in like

---

### Post by y3ahright on 2006-09-29
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3845    30884931    7  HPFS/NTFS
/dev/hda2            3846        4819     7823655   83  Linux
/dev/hda3            4820        4865      369495    5  Extended
/dev/hda5            4820        4865      369463+  82  Linux swap / Solaris

---

### Post by y3ahright on 2006-09-29
ok i stumbled upob this by accident and maybe it will help.

sudo fdisk /dev/hda1

The number of cylinders for this disk is set to 61279.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

---

### Post by bulldog on 2006-09-29
There's nothing wrong as far as I can see with your GRUB.

If you boot into Ubuntu can you read your windows disk?

It should be in your /media folder.

---

### Post by y3ahright on 2006-09-29
yes i can. last night my friend helped my mount it but i wouldnt wrk. also last night i could get into xp without a problem.  But now i can see my windows folders from ubuntu but cant load... and 1 more question u know in windows its cd.. to go back wat is it in the termanal for linux??

---

### Post by bulldog on 2006-09-29
The same to go back one directory cd to go to your /home cd~

You can retry to install GRUB from the live cd.
It's pretty simple to do.

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by y3ahright on 2006-09-29
ok thx but i dont understand y i cant get into xp its just confusing..

---

### Post by bulldog on 2006-09-29
See my previous post and try an reinstall of GRUB,maybe there's something not quite right.

---

### Post by neewby on 2006-09-29
try and make windows partition active, IF you have a partition magic . Or download a partitioning boot disk, should sort it out. You may have your table mixed up , windows is still definitely there I think it is Hda1

---

### Post by y3ahright on 2006-09-29
well i just did the live cd thing im hoping that it will wrk... time to try

---

### Post by bulldog on 2006-09-29
> **neewby said:**
> try and make windows partition active, IF you have a partition magic . Or download a partitioning boot disk, should sort it out. You may have your table mixed up , windows is still definitely there I think it is Hda1

Yep windows is there allright but wishes not to boot.

That's why I suggest to install GRUB again to see if windows is properly recognized.

Going to fool around with Partition Magic doesn't feel the right thing to do.

---

### Post by y3ahright on 2006-09-29
well :( no luck i reinstalled the GRUB but it still sits at the same spot... any thing else i can try??

---

### Post by bulldog on 2006-09-29
I only can suggest to use the windows cd and go to recovery console and type fixboot and if that won't do,try fixmbr.

If this works and you can boot windows again you won't have GRUB because your MBR should be replaced with the bootloader of Windows.

But you know now how you can reinstall GRUB with the live cd ;) 

Try this and see if you can get windows to boot on his own.

---

### Post by y3ahright on 2006-09-29
well fixboot didnt wrk so i tryed fixmbr and it said disk error ctrl alt delete to restart :( so i guess i have to reinstall GRUB and make it better.

---

### Post by y3ahright on 2006-09-29
ok so i got ubuntu back but XP still wont load... maybe im being impatient is it suppsoed to stay at
 
booting 'windows nt/2000/xp (loader)'
root (hd0,0)
filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

for a long time?? cuz i let it sit for like 5 min and i figured that should be long enuf.

im rly in a pickle plz plz plz help...

---

### Post by y3ahright on 2006-09-29
sudo fdisk /dev/hda1

The number of cylinders for this disk is set to 61279.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
(e.g., DOS FDISK, OS/2 FDISK)
Edit/Delete Messagcould that be the problem and if it may be how do i change it to 1024 or less???

---

### Post by bulldog on 2006-09-29
Nope there's a disk error,it should boot windows on the fly.

I'm a little worried you couldn't 'repair' windows,not even with fixmbr.

When this won't work by disk error the only thing is to try a reinstall of windows but I'm pretty sure it won't install,because fixboot and fixmbr should work if your disk is allright.

You surely can't repair it with Ubuntu or the live cd!

---

### Post by y3ahright on 2006-09-29
thx alot tho for ur time and 1 other thing i have 2 windows mounts on my desktop one called windows and the other called windows(2) y is that??

---

### Post by bulldog on 2006-09-29
> **y3ahright said:**
> sudo fdisk /dev/hda1

The number of cylinders for this disk is set to 61279.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
(e.g., DOS FDISK, OS/2 FDISK)
Edit/Delete Messagcould that be the problem and if it may be how do i change it to 1024 or less???

You stated it booted before without problems,or this is changed by something you did.
There's an error with your hdd for sure,and there are tools on the manufacturer internet page,to try to repair your problems.

You have to know the name of your hdd to search for such a tool.

But the change your loosing your Ubuntu too is evident so try to backup your data before running this kind of utility.

---

### Post by y3ahright on 2006-09-29
ok but now all i need is a good way to freakin back up my hd ... all i gots is my ipod ... gonna take FOREVER!!!
and actually yes i did change i just relized b4 i had 2 hd's a 20 gig for ubuntu and my 40 for windows
but then i decided to dual boot... man im smart for that idea.. so yes i did change something

---

### Post by bulldog on 2006-09-29
> **y3ahright said:**
> thx alot tho for ur time and 1 other thing i have 2 windows mounts on my desktop one called windows and the other called windows(2) y is that??

To know what's wrong I have to see your fstab.
There's the mounting registerd and maybe is your windows mounted twice.
Normally will Ubuntu make a mount point for your windows partitions and if I recall you have mounted it again with your friend.

This is easy to repair by removing the line you put in fstab and keeping the original.

---

### Post by bulldog on 2006-09-29
> **y3ahright said:**
> ok but now all i need is a good way to freakin back up my hd ... all i gots is my ipod ... gonna take FOREVER!!!
and actually yes i did change i just relized b4 i had 2 hd's a 20 gig for ubuntu and my 40 for windows
but then i decided to dual boot... man im smart for that idea.. so yes i did change something

Well I have a dual boot too,with two hdd's,one IDE and one SATA,and I can assure you it works perfectly.

Thus dual booting can be done without a prob.

---

### Post by y3ahright on 2006-09-29
ok i know y lol how do u get to fstab cuz last nite my friend took me there and made me add a line so i think thats it.. but how do u get there??

---

### Post by bulldog on 2006-09-29
> **y3ahright said:**
> ok i know y lol how do u get to fstab cuz last nite my friend took me there and made me add a line so i think thats it.. but how do u get there??

```
 gksudo gedit /etc/fstab 
``` should do the trick.

---

