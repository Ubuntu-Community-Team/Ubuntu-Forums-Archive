---
title: "Install Error (CD-ROM doesnt have a valid 'Release'"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by ludatha on 2007-04-21
I'm installing Ubuntu 7.04 on my PS3, when I run it, it comes up with kboot, I press enter and it comes up with:

[?] Ubuntu installer main menu

It all goes well untill I get to 'Detect and mount CD-ROM'
If I press enter on that, it only detects floppy, and if I continue it scans the CD-ROM and then come up with a red background saying:
'The CD-ROM does not seem to contain a valid 'Release' file, or that file could not be read correctly.
You may try to reapeat etc. etc.'

What am I to do?

---

### Post by leibowitz on 2007-04-22
Did you do a md5sum check on the iso file you downloaded before burning it.

Or did you try to check the cd with the boot menu entry.

---

### Post by ludatha on 2007-04-22
Check it with the boot menu
I don't know what a md5sum is (well dont know what they are for) 
Ive never installed an OS before

---

### Post by ludatha on 2007-04-22
Any other help please?
I really want to get this working!

---

### Post by leibowitz on 2007-04-22
I don't know at all if the PS3 is an Ubuntu supported platform. What processor is that, Cell broadband is that correct.

What is the CD-ROM you downloaded. Probably the 7.04 desktop for i386. So anyway, did you intend to try to install an i386 kernel on a PS3. This won't work at all.

I may be wrong.. but AFAIK you should try to download a Linux distribution that is fully supported to run on a PS3.

---

### Post by ludatha on 2007-04-22
[http://cdimage.ubuntu.com/custom/20070420-feisty-ps3/](http://cdimage.ubuntu.com/custom/20070420-feisty-ps3/)
thats the one, although ive tryed the alternate install as well

the processor is called:
Cell Broadband Engine

---

### Post by leibowitz on 2007-04-22
Good. Tell me how did you burn the cdimage ISO you downloaded. With what burning software, and describe the process.

ps: md5sum is a software that calculate an unique identifier on a file. It is used to check that the file you downloaded contain everything from the original file, and avoid corrupt download.

You should see an associated .md5sum file on the directory where you downloaded the .iso file. But I can't access the URL you provided so I cannnot tell you what the md5sum is for this image.

---

### Post by leibowitz on 2007-04-22
I found some various docs, as I can't test anything on a PS3, I will just paste them here for you to look at.

[https://help.ubuntu.com/community/Installation/PS3](https://help.ubuntu.com/community/Installation/PS3)
[http://www.psubuntu.com/](http://www.psubuntu.com/)
[http://www.playstation.com/ps3-openplatform/manual.html](http://www.playstation.com/ps3-openplatform/manual.html)

---

### Post by ludatha on 2007-04-22
Ok
I downloaded the file then extracted everything into a folder called ubuntu of my desktop using WinRAR free, then I put in a brand new blank CD-RW in the drive and Copyed the files using windows explorer onto the disk, windows did its thing, burned the files etc. then it ejected the disk. I put the disk in the ps3, when to Install other OS, and installed it. Then I restarted the console and Kboot thingy came up, saying the options were install or expert, so I pressed enter and it came up the with installer (bluebackground, asking to do stuff) Th first 2 steps work and the third (Detect and Mount CD-ROM) failed.

---

### Post by leibowitz on 2007-04-22
You don't have to extract anything. The .iso file you downloaded is an image of a CD-ROM. You need to burn it with an ISO burner tool, like Nero. In nero you will need to "Burn an image". 

Random search: [http://www.wizardskeep.org/mainhall/tutor/neroiso.html](http://www.wizardskeep.org/mainhall/tutor/neroiso.html)
That's an old version of nero showed there but it's still the same.

---

### Post by ludatha on 2007-04-22
OK, ill burn it using Nero ([http://www.download.com/Nero-7-Ultra-Edition-Enhanced/3000-2646_4-10654753.html?tag=lst-0-1](http://www.download.com/Nero-7-Ultra-Edition-Enhanced/3000-2646_4-10654753.html?tag=lst-0-1)) and tell you the results

---

### Post by ludatha on 2007-04-23
I burnt it using nero, and it actually worked, apart from the fact it said a few files were corrupt, but I may have edited them before, so I'm downloading it again just to be sure, but its at 2 kbs and im on 20% after 2 hours!

---

### Post by leibowitz on 2007-04-23
What are you actually using to download the file. And why did you edit any file. Maybe that's related to the PS3 installation I don't know so please let me know.

---

### Post by ludatha on 2007-04-23
the disk wasnt big enouf or somthing, since my laptop cant handel downloads, i'm using the actual ps3 to download it.

---

### Post by ludatha on 2007-04-24
WOW, thanks for your help, it worked, well the installation did, but when it re-booted after installation it comes up with kboot, I press enter and it says some stuff, and then comes up with a new screen saying:

> [ 25.710550] vland_id0, 124
[ 25.710550] vland_id1, 126
[ 25.710550] vland_id2, 127
[ 25.710550] vland_id3, 123

BusyBox v1.1.3 (debian 1:1.1.3-3ubuntu3) Built-on shell (ask)
Enter 'help' for a list of built-in commands.

/bin/sh: con't access tty: job control turned off
(initranfs)

What do I type in?

EDIT: on closer inspection, the optical mouse I plugged in is flash like mad!

---

### Post by ludatha on 2007-04-24
should I create a new thread about this?

---

### Post by leibowitz on 2007-04-24
Did you do everything that is explained on the PS3 related previous links.

Anyway you decide if you create a new topic.

Note that someone has talked about this earlier and I can't find a way to help him.
"job control turned off- what do I do ?" > [http://ubuntuforums.org/showthread.php?t=417842](http://ubuntuforums.org/showthread.php?t=417842)

---

