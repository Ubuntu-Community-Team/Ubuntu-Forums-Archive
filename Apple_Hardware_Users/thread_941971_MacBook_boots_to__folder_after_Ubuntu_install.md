---
title: "MacBook boots to ? folder after Ubuntu install"
date: 2008-10-08
forum: Apple Hardware Users
---

### Post by Caraibes on 2008-10-08
I have a MacBook Pro, I installed Ubuntu (tried 8.04.1 and 8.10 beta) on the whole hard drive. 

I don't have the Mac OSX dvd. 

Ubuntu runs fine from the live-cd.

But once installed, it "won't boot"... It only boots to a blinking folder with a question mark...

Does anyone has a clue to help me out ?

Thanks in advance for your tips !

---

### Post by cyberdork33 on 2008-10-08
Check this thread.

[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by Caraibes on 2008-10-09
Thank you very much for indicating the right thread... Very informative !

As a matter of fact, while I was still unaware of that above answer, I installed Mandrive (from a 2008.1 live-cd)...

It just worked, without any trouble... After the install process, the Mac rebooted, and it came straight to Gnome, without any more fiddlings !

I was glad, since I do not have the Mac OSX dvd !

---

### Post by cyberdork33 on 2008-10-09
> **Caraibes said:**
> Thank you very much for indicating the right thread... Very informative !

As a matter of fact, while I was still unaware of that above answer, I installed Mandrive (from a 2008.1 live-cd)...

It just worked, without any trouble... After the install process, the Mac rebooted, and it came straight to Gnome, without any more fiddlings !

I was glad, since I do not have the Mac OSX dvd !
yes, it is a bug in ubuntu. It has not been fixed for some reason.

---

### Post by GoG-Man on 2009-07-12
[COLOR=black][FONT=Verdana]Well I wish I knew all this before I just turned my MacBook into a paper weight....[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I was installing Ubuntu on an external drive for use on another computer.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]And after I rebooted, the Folder with the blinking ? greeted me.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I need some help with this one...[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have booted with the OSX disc, the drive is fine, and all the data seems to be intact.  I selected the hard drive as the Start Up disk, but no Joy. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] I am working on downloading a rEFIt CD.  But I have to be honest I am new to this stuff.  I was strictly using VMWare to experiment with other OS, but it was not working; now I have messed up my whole macbook.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](The #1 priority for me is getting OSX back up.)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]If this has been answered somewhere, please be patient and point me in the right direction, I'm in the middle east, so my internet and support over here is next to nothing. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks,[/FONT][/COLOR]
Justin

---

### Post by GoG-Man on 2009-07-12
[COLOR=black][FONT=Verdana]I fixed it.... [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I booted up with the Ubuntu CD, and ran off the CD....[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I started "**Partition Editor**"[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Selected my Macbook HD[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Went to Partition->Manage Flag-> checked "bios_grub"[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Shutdown, removed CD, and it booted to OSX[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I was sweating bullets for awhile there... there are no Apple "Geniuses" in Baghdad !![/FONT][/COLOR]

---

