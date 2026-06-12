---
title: "Do I make something special with the .iso file...?"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by Pretorian on 2005-12-30
Hi there,
Do I make something special with the .ISO file before to burn it on a CD ( and the same for a live CD):confused: 
bcs I placed the disc drive first in the BIOS but nothing happened, could you help me?
Thanks

---

### Post by Perfect Storm on 2005-12-30
First you need to burn the .ISO file as an **Image**. THen make sure that your BIOS is set up for booting with your CD/DVD drive.

---

### Post by Herman on 2005-12-30
Checking an MD5sum:
When anyone goes to a website to find an .iso to download, for an operating system or some other software, they can also usually find an MD5 sum for it. An Md5sum is used to check and make sure it is the 'real McCoy', and has not been accidentally corrupted or altered in some way. This looks like a string of mixed up numbers and letters. Normally you can find that somewhere around the button of hyperlink you click to start the download.
You can copy that string of mixed up numbers and letters, right off the website, and paste it on a text file (gedit), you can save that for later on.
Then you download your .iso, and when it is finished, maybe it will end up on your desktop. (That's where mine go anyway).
I move the .iso into my /home/herman folder before I do anything, no other folder or place will do. Well, you can put it in some other folder, but then you'll need to know how to specify a folder path when you do the next command I am going to show you. Some new people might not have learned folder paths yet. (It's just the address of your file). Anyway, back to the main subject:
Then I open a terminal and type the command 'md5sum', followed by the name of the file. Let's say I want to check my new ubuntu-5.10-live-i386.iso 
I right-click on the .iso file, and click 'properties'. In the 'properties' window that comes up, there is a white rectangle near the top with the name of the file in it. It is a good idea to copy that right off the 'properties' window, that saves typing and also typing errors and makes the job easier.
Okay, I you open a terminal, and type 'md5sum', and paste the name of the file there, like this:
```
herman@redxz:~$ md5sum ubuntu-5.10-live-i386.iso
``` Now I press [enter] and wait a minute or two and in a while the output will be there. This will be another string of garbled text. I copy that off the terminal, and find my gedit file where I saved the md5sum for that .iso file earlier, and I paste the output from the terminal under the md5sum from the website. If they match, then my new .iso is good.
If they are different, I may try again, or try downloading from a different website or mirror. :D (Herman)

---

### Post by Herman on 2005-12-30
Burn an .iso to a CD:
When I place my blank CD-R or CD-RW disk into the CD drawer, I get a window that comes up asking me the following: 'Burn audio, video, or data CD?'
I always click 'cancel' for that one, because I do not want any of those kinds of CD, I want to burn my .iso to my CD as an .iso image, not as data.
To do that I simply right-click on the .iso I want to burn, and then on the right-click menu, I click 'burn to disk'.
Avoid burning the CD at too high a speed.
It is advisable to set the burn speed to a nice careful, steady pace like 4x, which is often recommended.
I burn mine on the slowest possible speed just to be sure, (1x), and it only takes an extra minute or two. 
And that is how to make an .iso image CD in Ubuntu. :D (Herman)

---

### Post by Herman on 2005-12-30
[MD5 GUI for Windows]("http://www.toast442.org/md5/")
[Home of the MD5summer]("http://www.md5summer.org/")
[Nullriver Software ~ Products]("http://www.nullriver.com/index/products/winmd5sum")
You can also, if you are unfortunate enough not to have any other Ubuntu computer around, check Md5 sums in Windows, but you need to add special software. Here are a few links, (above) to look at. I don't know much about them, I have never used any of them.
As for burning an .iso as an image in Windows, you will have to use whatever extra software you have in Windows for that, so I can't help you there either, sorry. 
I hope these help.  :D (Herman)

---

### Post by steve.horsley on 2005-12-30
Remember taht a .iso file is an **image** of a CD. Look for an option that burns an **image** rather than burning a data CD. I seem to remember that Nero has a Burn Image pulldown menu that then launches a file open dialog where you can select the image file to burn.

Things **not** to do:
* Put the .iso file on as a data file so that you can see the .iso file there when you insert the written CD.
* Unzip the .iso file and write its **contents** to the CD. This puts the data on the CD, but not the boot sector, so the CD is not bootable.

---

### Post by LanDroid on 2005-12-30
[QUOTE=Herman]Checking an MD5sum:
When anyone goes to a website to find an .iso to download, for an operating system or some other software, they can also find an MD5 sum. An Md5sum is used to check and make sure it is the 'real McCoy', and has not been accidentally corrupted or altered in some way. This looks like a string of mixed up numbers and letters. Normally you can find that somewhere around the button of hyperlink you click to start the download.
...[/QUOTE]
OK, I found a tasty little program [here](http://rndware.info/products/md5compare.asp) to perform that task and generated the MD5sum for the LiveCD file I downloaded.  Unfortunately I can't find the correct MD5sum anywhere on your download page.  Is there a secret password or something?  Is the following string correct for the file "ubuntu-5.10-live-i386.iso"?

49f36f8aef009d6403360de23b5a47d4

Also, I guess I'll try googling this, but any advice on how to change the BIOS to use the bootable Live CD?  I'm nervous about doing this - how will I get back to booting from the main drive if the disc doesn't work?  Using Windows XP Home version.

:confused:   Heh, three questions and I haven't even burned the file to disc yet.  Maybe Ubuntu Linux is not for me...  :rolleyes:

**On edit:**
OK, I found the checksums below and it matched - so far so good. 
[http://mirror.cs.umn.edu/ubuntu-releases/5.10/MD5SUMS](http://mirror.cs.umn.edu/ubuntu-releases/5.10/MD5SUMS)

I'm checking [Herman's page on BIOS Boot Order](http://www.users.bigpond.net.au/hermanzone/p1.htm) right now...  Progress is slow, but happening... ;)

---

