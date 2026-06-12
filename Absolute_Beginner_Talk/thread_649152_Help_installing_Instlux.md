---
title: "Help installing Instlux"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by VtecCivic93 on 2007-12-24
Ok so i want too get Linux on my computer but i dont have a cd or anything so i downloaded Isntlux, and i also downloaded the unbuntu 6.06 desktop, and the english instlux 6.06 unbutu installer, do i need anything else? I read u just run the english installer and it reboots the pc, then u choose wether too run windows or the unbuntu installer, but when i reboot it doesnt give me an option and it prompts too un-install the english installer..any help?!

Basically how can i get my computer too boot from the unbuntu installer instead of automatically loading windows? I did what this tutorial said [http://paulsiu.wordpress.com/2006/12/25/using-instlux-to-install-ubuntu-in-windows-xp-over-the-network/](http://paulsiu.wordpress.com/2006/12/25/using-instlux-to-install-ubuntu-in-windows-xp-over-the-network/) but it doesnt give me the option too choose windows or unbuntu installerht

---

### Post by Lord DarkPat on 2007-12-24
Sorry if it's of no help, but WHAT IS INSTLUX?
Never heard of it.

---

### Post by VtecCivic93 on 2007-12-24
ok well i just got ir working through the psychocats tutorial, but that makes it so i have two OS running at the same time, is there a way too uninstall windows so i just have the linux/unbuntu???

---

### Post by logos34 on 2007-12-24
Instlux would have been the last installer I'd have chosen...UNetbootin is way better.

But I tried it out about nine months ago and it I think it worked ok...

What version of windows do you have?

---

### Post by VtecCivic93 on 2007-12-24
> **Lord DarkPat said:**
> Sorry if it's of no help, but WHAT IS INSTLUX?
Never heard of it.

Its a program that lets u install linux /unbuntu without any cd's or anything just programs u downloaded..but i just got the one from psychocats but i want just linux not linux and windows.

---

### Post by VtecCivic93 on 2007-12-24
> **logos34 said:**
> Instlux would have been the last installer I'd have chosen...UNetbootin is way better.

But I tried it out about nine months ago and it I think it worked ok...

What version of windows do you have?

Well idk how too use any of them maybe u could tell me, ive got windows xp sp2

---

### Post by logos34 on 2007-12-24
Did it install on a separate partition or INSIDE windows on a folder (loopmounted filesystem, i.e. like wubi does)?

It's been so long I can't remember

---

### Post by VtecCivic93 on 2007-12-24
> **logos34 said:**
> Did it install on a separate partition or INSIDE windows on a folder (loopmounted filesystem, i.e. like wubi does)?

It's been so long I can't remember

Well the one i just got from psycho cats, just runs linux/unbuntu inside of windows through virtual machine, i want linux as my only operating system, not windows and linux..

---

### Post by asmiller-ke6seh on 2007-12-24
> **Lord DarkPat said:**
> Sorry if it's of no help, but WHAT IS INSTLUX?
Never heard of it.

[The answer to your question]("http://cybernetnews.com/2006/06/02/install-linux-in-windows-using-instlux/"). I have never used it, nor heard of it before now.

---

### Post by logos34 on 2007-12-24
> **VtecCivic93 said:**
> Well the one i just got from psycho cats, just runs linux/unbuntu inside of windows through virtual machine, i want linux as my only operating system, not windows and linux..

in that case you can't get rid of windows after installing ubuntu because it's running ON windows (not quite VM, more like loop mounted fs).  

Here's the guide you want to use (but you'll need to dl the text-mode alternate install cd--sorry, the live/desktop cd won't work):
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
(-->'**CD image approach**')

ADD: You'll install on a separate partition.  Grub will be your bootloader.  Then you can safely delete the windows partition and format it as ext3 (use it for storage or whatever).

---

### Post by VtecCivic93 on 2007-12-24
so which of the 3 things do i download, the UNetBootin one? and even when u click that link theres hundreds of different downloads and that throws me off..if its not too much trouble for u, could u give me direct link too each thing i need too download? Thanks!

---

### Post by logos34 on 2007-12-24
no, just read the section 
**'CD image approach**' at the bottom, as I said in my previous post.  

You need these three things:
> 
Download vmlinuz and initrd.gz from [WWW] [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/) and save them to hd-media
#

Download the ALTERNATE ubuntu-installer CD from [WWW] [http://www.ubuntulinux.org/download/](http://www.ubuntulinux.org/download/) and save the .iso file in the root directory of first partition of your hard drive.
#

Download Grub For Dos from [WWW] [http://sarovar.org/download.php/1138/grub_for_dos-0.4.2.zip](http://sarovar.org/download.php/1138/grub_for_dos-0.4.2.zip)

---

### Post by VtecCivic93 on 2007-12-24
> **logos34 said:**
> no, just read the section 
**'CD image approach**' at the bottom, as I said in my previous post.  

You need these three things:
Alright well see if u click onthat first link, and then click the intrd.gz it just opens a page thats has like 3 thousand pages or just typing, it doesnt ask me too download anything, and when i click the link for intrd.gz it freezes my comp because theres so many pages or words and stuff..what do i do?grr and which unbutu from the site do i get? wow i suck at this lol


AND how do i create a directort in the root directory like it says, im a noob. =P

---

### Post by logos34 on 2007-12-24
> **VtecCivic93 said:**
> Alright well see if u click onthat first link, and then click the intrd.gz it just opens a page thats has like 3 thousand pages or just typing, it doesnt ask me too download anything, and when i click the link for intrd.gz it freezes my comp because theres so many pages or words and stuff..what do i do?


AND how do i create a directort in the root directory like it says, im a noob. =P

no, those are gzipped/compressed kernel images--**right-click **and '**save link as**' (save to hard drive) or whatever it is in windows.  

Then just make a new folder in C:  name it 'hd-media'

---

### Post by VtecCivic93 on 2007-12-24
> **logos34 said:**
> no, those are gzipped/compressed kernel images--**right-click **and '**save link as**' (save to hard drive) or whatever it is in windows.  

Then just make a new folder in C:  name it 'hd-media'

ok got both the intrid.gz and the vmlinuz done..now im downloading the 6.06 LTS version and i clicked the checkbox for the text format, so when its done i just move it into the C: drive?

---

### Post by logos34 on 2007-12-24
> **VtecCivic93 said:**
> ok got both the intrid.gz and the vmlinuz done..now im downloading the 6.06 LTS version and i clicked the checkbox for the text format, so when its done i just move it into the C: drive?

yep.  

the .iso and grldr in the base directory, or c:\

and 

vmlinuz and initrd.gz in 'hd-media', or c:\hd-media\

Remember, you want to **extract** just the 'grldr' file from the zipped grub4dos archive.  Then copy it over to c:  And create the menu.lst too.

---

### Post by VtecCivic93 on 2007-12-24
> **logos34 said:**
> yep.  

the .iso and grldr in the base directory, or c:\

and 

vmlinuz and initrd.gz in 'hd-media', or c:\hd-media\

Remember, you want to **extract** just the 'grldr' file from the zipped grub4dos archive.  Then copy it over to c:  And create the menu.lst too.

Ok i just clicked "extract here" here being the hd-media folder..now do i just copy and paste ' c:\grldr="Install Ubuntu" ' into the system startup text file?

---

### Post by logos34 on 2007-12-24
> **VtecCivic93 said:**
> Ok i just clicked "extract here" here being the hd-media folder..now do i just copy and paste ' c:\grldr="Install Ubuntu" ' into the system startup text file?

no, read the instructions again...grldr goes in c:\, not c:\hd-media.

paste ' c:\grldr=Install Ubuntu' into boot.ini file

---

### Post by VtecCivic93 on 2007-12-24
Ok well i tried it, rebooted the comp and it didnt give me the option too install unbuntu so i took screenys too show u what i have...

Ok, so i just move the 6.06. LTS thing i downloaded too the c: drive and exctract it "here"?

heres the pics:
[IMG]http://i131.photobucket.com/albums/p302/tuner_cavalier/help4-1.jpg[/IMG]

[IMG]http://i131.photobucket.com/albums/p302/tuner_cavalier/help2-1.jpg[/IMG]

[IMG]http://i131.photobucket.com/albums/p302/tuner_cavalier/help-1.jpg[/IMG]

[IMG]http://i131.photobucket.com/albums/p302/tuner_cavalier/help3.jpg[/IMG]

---

### Post by logos34 on 2007-12-24
you probably read my last post by now...need to copy grldr to c:


boot.ini should look like this (here's mine):
> [boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect /usepmtimer
**c:\grldr=Install Ubuntu**

---

### Post by logos34 on 2007-12-24
I just noticed that those images are from the gutsy archive, but you're using the dapper 6.06 iso...it may not be an issue but if it gives problems dl the dapper version
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/)

---

### Post by VtecCivic93 on 2007-12-24
> **logos34 said:**
> I just noticed that those images are from the gutsy archive, but you're using the dapper 6.06 iso...it may not be an issue but if it gives problems dl the dapper version
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/)

alright well i feel like a dumbass but i dont know where the .iso file nor the grldr file are that i need too move too the c:

---

### Post by logos34 on 2007-12-24
no, you had it before...move initrd.gz back to hd-media folder

copy the **grldr **(what you you extracted from grub4dos zip) to **c:**

then edit boot.ini so the 'c:\grldr=Install ubuntu' is last

---

### Post by VtecCivic93 on 2007-12-24
> **logos34 said:**
> no, you had it before...move initrd.gz back to hd-media folder

copy the **grldr **(what you you extracted from grub4dos zip) to **c:**

then edit boot.ini so the 'c:\grldr=Install ubuntu' is last

oooh ok, i moved it back, and it didnt say too do anything with the grub thats why i was like WTF lol..ill do that and i edited the boot already made it last and got rid of the " " i had in there...


Do i need too extract the unbuntu-6.06 file into the c drive? or do i leave it in zip format

---

### Post by VtecCivic93 on 2007-12-24
Alright well i did everything, rebooted the comp and it gave me the option too install unbuntu w00t! BUT
when i hit enter on install unbuntu it came up with a black screen that had:

GRUB4DOS 0.4.2 (2006-12-28) Memory blah blah

find /menu list
find /boot/grub/menu.lst
find /grub/menu.lst
comman line
reboot
halt

WTF?

---

### Post by logos34 on 2007-12-24
> **VtecCivic93 said:**
> Do i need too extract the unbuntu-6.06 file into the c drive? or do i leave it in zip format

I was going to ask about that because I noticed it didn't have the .iso suffix (maybe you have filetypes disabled in folder options)...hope that doesn't cause a problem.  It's an iso image, you don't need to 'extract' it.  

> ...when i hit enter on install unbuntu it came up with a black screen that had:

GRUB4DOS 0.4.2 (2006-12-2 Memory blah blah

find /menu list
find /boot/grub/menu.lst
find /grub/menu.lst
comman line
reboot
halt

hmm...try renaming hd-media folder** grub**.

---

### Post by logos34 on 2007-12-24
the line in boot.ini should have quotes:
> c:\grldr="Install Ubuntu"

sorry about that error

---

