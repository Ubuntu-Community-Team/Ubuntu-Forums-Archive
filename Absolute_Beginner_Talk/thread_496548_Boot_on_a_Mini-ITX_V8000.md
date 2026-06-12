---
title: "Boot on a Mini-ITX V8000"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by TechnoX on 2007-07-09
I have test to install openSUSE as a server on one of my computers earlier, but it don´t works.
I'm testing to Install Ubuntu Server Edition instead. The installation went well.
When I took out the CD and restart the computer, wouldn't Ubuntu start. 
This is what occurs when I start the computer:
1. The screen with the motherboards logo appear:
> **VIA Mainboard**
VIA VPSD
[http://www.viavpsd.com](http://www.viavpsd.com)

2. Then comes the screen when BIOS loads (I think anyway that). It is a lot of text whitch I don't get the time to read but at the bottom it say (In about a half second):
> Grub Loading stage1.5
Grub loading, please wait...

3. Then comes the screen there you can choose which OS you want to load. It Says:
> Ubuntu, kernel 2.6.20-15-server
Ubuntu, kernel 2.6.20-15-server (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Windows NT/2000/XP (loader)

Use the '&#8593;' and '&#8595;' keys to select which entry is highlighted. 
Press enter to boot the selected OS, 'e' to edit the 
commands before booting, or 'c' for a command-line.

3a. If I choose "Ubuntu, kernel 2.6.20-15-server" or "Ubuntu, kernel 2.6.20-15-server (recovery mode)" become the screen black for about an second and then shows "Starting up..." and a while later the computer restarts and all starts on one again. 

3b. If I choose "Ubuntu, memtest86+" become a blue screen and the computer is scanning for errors in the harddisk (I think anyway that).

3c. If I choose "Windows NT/200/XP (loader)" so starts windows 98 normaly.

3b. I have test to press 'e' but i don't remember what occurs, if you need to know that I can start the computer and write it down. I remember what was occurs when I pess 'c'  anyway. It becoming a new screen whitch says:
> [  Minimal BASH-like line editing is supported. For 
the first word, TAB lists possible command 
completions. Anywhere else TAB lists the possible 
completions of a device/filename. ESC at any time 
exits.  ]

grub>   

I press tab and got this:
> Possible commands are: background blocklist boot border cat chainloader clear
cmp color configfile debug diplayapm displaymem embed find foreground fstest g
eometry halt help hide impsprobe initrd install ioprobe kernel lock makeactive
map md5crypt module modulenounzip pager partnew parttype password pause print q
uiet read reboot root rootnoverify savedefault serial setkey setup shade spash
image terminal terminfo testload testvbe unhide uppermem vbeprobe viewport


The spec. for the computer is (ask for more details):
Ram: 128Mb
Harddisk: 40Gb
Processor: VIA C3

I have also test to do the "rescue my system" from the CD but it still not works. In the "rescue my system"-installation it says something about the rootfilesystem, if I remember it correct so was it missing. But since I don't saw any manually settings there I could create any rootfilesystem I thought it create that self.

Sorry if my english is a little bad but english is not my mother tongue. But I'm very good at understanding english.

---

### Post by shrift on 2007-07-09
Try booting from the recovery mode. This one: Ubuntu, kernel 2.6.20-15-server (recovery mode).

---

### Post by shrift on 2007-07-09
Oh, you did that. My bad. I missed that part hmmmm.....

---

### Post by shrift on 2007-07-09
when you get to the grub list of boot options highlight the "Ubuntu, kernel 2.6.20-15-server" and press e to edit it.

Find the line that has "quiet splash" on it. At the end of that line add "noapic". See if that helps at all. (I'm not sure it will... just the only thing I can think to try here.)

---

### Post by TechnoX on 2007-07-09
I found the line and add noapic to it. Then I press escape twice to get back to the OS-list. There I choose "Ubuntu, kernel 2.6.20-15-server" but I get the same results as before. Then i went back to the line with "quiet splash" and found out that noapic was gone. I look for a save function but couldn't find any. I test the same thing a few times more but it didn't works. 

It should be a space before noapic, right? I test both with and without a space but it don't make any difference.

EDIT: I am without Internet for 4 days so I can't test anything then.

---

### Post by shrift on 2007-07-11
What you did is correct. It's just not working. : ( Sorry, unfortunately it is my belief that you need to reinstall Ubuntu. If you do this and you kept a separate partition for /home, make sure you don't reinstall the /home partition as then you can keep your user settings.

Anyone have some ideas?

---

### Post by regomodo on 2007-07-13
> **TechnoX said:**
> I found the line and add noapic to it. Then I press escape twice to get back to the OS-list. There I choose "Ubuntu, kernel 2.6.20-15-server" but I get the same results as before. Then i went back to the line with "quiet splash" and found out that noapic was gone. I look for a save function but couldn't find any. I test the same thing a few times more but it didn't works. 

It should be a space before noapic, right? I test both with and without a space but it don't make any difference.

EDIT: I am without Internet for 4 days so I can't test anything then.

If nopaic is gone it's because you didn't edit that file it super user mode. That means all changes were not saved.

$ sudo nano /boot/grub/menu.lst

then add that entry. To save ctrl+o and hit enter

---

### Post by TechnoX on 2007-07-13
> **shrift said:**
> What you did is correct. It's just not working. : ( Sorry, unfortunately it is my belief that you need to reinstall Ubuntu. If you do this and you kept a separate partition for /home, make sure you don't reinstall the /home partition as then you can keep your user settings.

Okey, What did you mean with the /home partition? I haven't any user settings yet (because I haven't started Ubuntu yet) and therefore it's no need to keep them.


> **regomodo said:**
> If nopaic is gone it's because you didn't edit that file it super user mode. That means all changes were not saved.

$ sudo nano /boot/grub/menu.lst

then add that entry. To save ctrl+o and hit enter

I'm not in the Terminal, where will I write *$ sudo nano /boot/grub/menu.lst* ?
Is it a terminal at all, in the boot-mode?

---

### Post by regomodo on 2007-07-14
if you can't boot up to get to the terminal use the livecd and "cd" to that directory
Nano is a text editor in the terminal

Also i'm fairly sure it's ok to edit that file in windows' notepad. It doesn't care about user permissions

---

### Post by TechnoX on 2007-07-15
> **regomodo said:**
> If nopaic is gone
Will it be noapic or nopaic?

> **regomodo said:**
> if you can't boot up to get to the terminal use the livecd and "cd" to that directory
Nano is a text editor in the terminal

Also i'm fairly sure it's ok to edit that file in windows' notepad. It doesn't care about user permissions
I have download the server edition and as I can see it is no livecd include in that edition. And if I will edit the file in windows I must burn an new CD because windows on that computer dosen't start right now. Indeed I have search for menu.lst on the CD with the explorer in Windows, but I couldn't find it. The directories isn't right, I think.

---

### Post by regomodo on 2007-07-15
noapic

cd does not mean compact disk in this context. it means change directory

example

```
cd /home/billybob/pr0n
```

which would guide the terminal to billybob's pr0n folder

---

### Post by TechnoX on 2007-07-15
I know ;)
But you said that I could change the file in windows and because windows dosen't start on that computer I try to find the file on the CD but I think all the files are compressed on the CD.

How can I come to the terminal? Or will I have to download the desktop edition and browse to the file?
Can I download the desktop edition and then install all server-components? How easy is that, in that case?

---

### Post by regomodo on 2007-07-15
leave the cd out for editing. did you read my post?

the file will be on the hard drive after you've done an install.

use the livecd. you'll be able to browse all your diles

---

### Post by TechnoX on 2007-07-15
> **regomodo said:**
> leave the cd out for editing. did you read my post?

the file will be on the hard drive after you've done an install.

use the livecd. you'll be able to browse all your diles
Yes, I have read what you said. I was only a bit tired so I misunderstand you.
I doesn't have any livecd, I thought the livecd wasn't included in the server edition. Is it included?:confused:

---

### Post by regomodo on 2007-07-15
ah, didn't see you are in server install

use dsl as a live cd. Mainly as it's tiny and wont take long to download. Also, as it's based on knoppix you should have no hardware issues

[http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)

---

### Post by TechnoX on 2007-07-16
I already have dsl, the first thing whitch is positive.:D
DSL works fine so I will look for the file in a while.
I edit when I have done that.

---

### Post by regomodo on 2007-07-17
you'll need to browse for that file using emelFM (i think that's what its called) in super user mode. Either that or use the terminal

---

### Post by TechnoX on 2007-07-18
I have done a couple of tries in the morning but without success.
emelFM wouldn't start in super-user mode so I use the terminal instead.

First I write *sudo su* to change to super-user mode. Then I have test to write */boot/grub/menu.lst*, *sudu nano /boot/grub/menu.lst*, *$ sudo nano /boot/grub/menu.lst* and some other commands. Often it says "Permission denied" which I think is very strange. Sometimes, when i got a file, so is it wrong file. It says several things about how DSL should boot.

---

### Post by regomodo on 2007-07-18
those commands are to your dsl cd. you need to mount your hard drive (hd? or sd?) and the cd to the correct directory.

hell, i've forgotten what you were trying to do

---

### Post by edchien on 2007-07-21
I've just run into the same issue as you, I also tried to install the server image onto my mini-itx.  The problem is that the linux-server kernel does not run on my mini-itx (i'm not sure why).  The server install cd actually boots the linux-386 kernel.  Thus, you need to do an 'apt-get install linux-386' on your mini-itx system.  I did this by booting the server CD and going into rescue mode and then installing the linux-386 kernel.  You might need internet connection as I'm not sure if apt-get will get the linux-386 package from the CD or download it from the ubuntu servers.

I'm using a raided setup on my system so, the simple rescue mode did not work on my system because I couldn't select my root/md0 parition.  The exact steps I took was, boot the server CD and go into rescue mode.  Let Ubuntu detect your hardrive components (keyboards and stuff) and when I ask for the root partition, hit ALT-F2 to gain access to a shell.

from there, you need to mount your root (/) system.
# mount /dev/<md0> /mnt

then you need to chroot into your root system (first you need to mount proc)
# mount -t proc /proc /mnt/proc
# chroot /mnt /bin/bash
# apt-get install linux-686

after its working you can remove the linux-server package
# apt-get remove linux-server

Hope this helps.

---

### Post by TechnoX on 2007-07-23
> **regomodo said:**
> those commands are to your dsl cd. you need to mount your hard drive (hd? or sd?) and the cd to the correct directory.

hell, i've forgotten what you were trying to do
Now, I have mount the hard drive and change the file (menu.lst). Then I have restart the computer and check so noapic is there, on the right place. It was right.
But, it's still not working. It is exactly the same course of events as before.

I haven't test edchien's suggestion yet, I wants a little more explanation first. I'm quite new with Linux. Or, at least, I need to ponder over it a while.

---

