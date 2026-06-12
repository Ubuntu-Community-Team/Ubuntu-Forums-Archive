---
title: "Failed a dual boot, can't launch Windows or Ubuntu."
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by ronaldmonster on 2007-11-08
I'm doing this from a LIVE Ubuntu CD. 

Well, first I used a automatic linux installer. Everything seemed to go well, dual boot installed Linux, and the rest of the family could use Windows. Please don't turn this into a fanboy post why I should only use Linux, I like both ok and nothing is wrong with that.

So I got everything set up as normal, got all the new updates, codecs for media, Nvidia card driver. And finally Compiz Fusion, which I tried to launch and it came up a white screen.  So I figure no biggy, just restart, don't know what happened but it damaged a .ini boot file. And I can't launch either OS with using this CD.

Please help me :(

---

### Post by System Monitor on 2007-11-08
Same thing happened to me almost, except i had been using Ubuntu and i shutdown and tried to load windows, didn't work, so i used system recovery app my computer has. When it finished i restarted and no boot menu came up or anything. maybe it has to do with GRUB
thanks!!!

---

### Post by ronaldmonster on 2007-11-08
> **System Monitor said:**
> Same thing happened to me almost, except i had been using Ubuntu and i shutdown and tried to load windows, didn't work, so i used system recovery app my computer has. When it finished i restarted and no boot menu came up or anything. maybe it has to do with GRUB
thanks!!!

That doesn't help out my situation at all...

---

### Post by mistergq on 2007-11-08
first, before you messing around with anything, can you back up all the important information on that computer.  you may end having to reinstall Windows first, then install ubuntu second if you can get this boot problem fixed.

second, which windows do you have?

---

### Post by ronaldmonster on 2007-11-08
Windows XP Home Edition. 

I don't know what happened. This is just weird, I can't access my XP partition cause an error comes up.

---

### Post by NotTheMessiah on 2007-11-08
I think you should delete your ubuntu partition and then reinstall(gutsy?) - then you'll see grub again and you would be able to boot in XP. And you should do a back up before you start installing an OS that you know little about(i didn't and paid the price for it the first time :))

---

### Post by ronaldmonster on 2007-11-08
But I have music I can't replace I use for my sets, If I lose that it would be a pain :\

So how would I go about deleting linux if I can't access XP without it restarting during the XP start up screen?

---

### Post by genbuntu on 2007-11-08
Well heres what I can offer (and don't expect this to be a one shot solution , its may just be a helping hand) :

Try restoring your GRUB or whatever partitions you want to modify/delete by booting with following burned to a cd:

1) System rescue disk:
 [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

OR

2) Super grub disk: 
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

I haven't had experience with any, but it seems the 'super grub disk' claims to be better at handling the kind of situation you are in.

---

### Post by System Monitor on 2007-11-08
you cant burn iso if you are using live cd(unless you have 2 cd drives) : (

---

### Post by Sef on 2007-11-08
> 2) Super grub disk:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

I haven't had experience with any, but it seems the 'super grub disk' claims to be better at handling the kind of situation you are in.


Super GRUB Boot Disk is excellent; I have used it to install GRUB on machines that would not boot up.

---

### Post by NotTheMessiah on 2007-11-08
> **ronaldmonster said:**
> But I have music I can't replace I use for my sets, If I lose that it would be a pain :\

So how would I go about deleting linux if I can't access XP without it restarting during the XP start up screen?

That is why i said that you should back up your stuff before you do anything. So your music wasn't that important to you since you don't have a back-up :)

Boot up the LiveCD find your ubuntu partition, delete it - you don't have to format it if you don't want to) then install it(install icon on your desktop) and choose the guided- use the largest free space option to install it again.

But try everything you can to fix the grub before you delete your partition. 
I thought that you didn't have anything important when i stated that you should delete it straight away. So try everything and if it doesn't work -delete and reinstall.

---

### Post by ronaldmonster on 2007-11-09
> **genbuntu said:**
> Well heres what I can offer (and don't expect this to be a one shot solution , its may just be a helping hand) :

Try restoring your GRUB or whatever partitions you want to modify/delete by booting with following burned to a cd:

1) System rescue disk:
 [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

OR

2) Super grub disk: 
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

I haven't had experience with any, but it seems the 'super grub disk' claims to be better at handling the kind of situation you are in.

How would I go about using that? I'm not to sure but I might have messed it up more.

---

### Post by genbuntu on 2007-11-09
The good and 'not so good' thing about open-source is that one doesn't get spoon-fed troubleshooting advice. 
First try glancing at the documentation and ask about any specific trouble you are having.

1)  [http://supergrub.forjamari.linex.org/?section=documentation](http://supergrub.forjamari.linex.org/?section=documentation)

2)  [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

> System Monitor  	
you cant burn iso if you are using live cd(unless you have 2 cd drives) : (

System monitor: Try reading the section "How to make your Super Grub USB Disk" , in link (2) above to try booting from a usb drive (if possible).

---

