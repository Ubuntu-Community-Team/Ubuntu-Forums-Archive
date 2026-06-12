---
title: "My install Saga continues"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Mek-Eng on 2007-08-22
So I had put a post before about not being able to install because Ubuntu was running too slow off the CD. Well:

I tried throwing on some other operating systems just as a stop gap in the mean time, but still ran into install errors. Since I'm sure the other CDs were working, I figured something was up. I then remembered that the CD-rom drive was a giant POS. So I pulled the DVD-RW from the other computer and used it for the install of UBUNTU. It went a lot smoother (and quieter), but still took 20min to load the main screen and was pretty slow when I was in it. When I clicked the 'install' button I eventually (20min later) got the outline of a window opening, but nothing ever materialized inside the window. after another 20min, I gave up. 

The computer shouldn't be giving me this much grief! It's a 1.7Ghz Celeron with 256Mb ram and I'm installing onto a ATA100 40Gb HD. I've installed windows Xp on the system before and it didn't give me any issues. 

Is there a text only version of the loader for Ubuntu... or how should I get this working??

---

### Post by gashcrumb on 2007-08-22
If you have a reasonably fast internet connection you could use the "minimal" CD installer:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I use this to install ubuntu on older machines that have less CPU/RAM than your machine there, works perfectly.  Once you've installed the CD and you get to a terminal prompt, just do "sudo apt-get install ubuntu-desktop" to download/install what usually comes on the normal install CD.

---

### Post by Mek-Eng on 2007-08-22
Would it be able to install from the normal install CD after doing the minimal install or would it have to download it again?

---

### Post by wpshooter on 2007-08-22
Yes, there is a text based installer.  Just look for and download the **ALTERNATE** version of Ubuntu.

And if it were me and there was no other O/S, programs or data on this computer that I needed to save, I would get [www.killdisk.com](www.killdisk.com) and WIPE that hard drive completely clean before attempting the Ubuntu installation.

P.S. - Make sure that the very first thing that you do when you boot to the Ubuntu CD is to check the integrity of the CD by running the verification function that is found on the initial Ubuntu boot screen menu.

Good luck.

---

### Post by deadgobby on 2007-08-22
You could install ubie server CD and it is text based. Once that is installed.  You'll get the shell screen like this. 
username@ubuntu:~$
 From there you can install any type of desktop flavor that Linux has to offer. So if you want gnome as a desk top.
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ubuntu-desktop
 You have 256 of ram speed and running a live CD can take up time to get it to install. Installing the server pack just cuts the graphic phase of things and your off and on the dance floor. 

taken from this link


[http://psychocats.net/ubuntu/nox](http://psychocats.net/ubuntu/nox)

Gobby

---

### Post by Mek-Eng on 2007-08-22
I just click the 'alternate' button on the bottom before hitting the install button right??

---

### Post by wpshooter on 2007-08-22
> **Mek-Eng said:**
> I just click the 'alternate' button on the bottom before hitting the install button right??

NO.  You have to get the proper Ubuntu download website and download the ALTERNATE (text based) version of Ubuntu and then burn it to a CD and then install from THAT cd.

---

### Post by Mek-Eng on 2007-08-22
[ATTACH]41342[/ATTACH]

Like this???

---

### Post by Midwest-Linux on 2007-08-22
I have always used the alternate text based installer  for Ubuntu Fiesty 7.04 in  every computer I installed it into regardless of the computer or size of the ram. I never had a bad install or did the screen freeze. When it is at 6% installing, it may seem to hang...but its not...that process just takes longer. Connect the computer to the internet before installing Ubuntu, this way it will do a auto configure for the internet...

When burning the ISO to disc...always use the  lowest burn speed..it just takes a few more minutes but will save you hours of time...

If the computer played sound before with windows but not with Ubuntu, it could be that the internal sound card isn't configured for Ubuntu. If the sound card is internal, then just throw in a inexpensive PCI sound card into the PCI slot ...should do the trick.

If you see messages about ACPI or BIOS being old ... don't be concerned as all this means you have to manually shut off the computer AFTER shutting Ubuntu down...its a minor bug issue that doesn't seem to affect the way Ubuntu performs...it mainly affects older computers.

Don't expect to listen to do streaming audio after installing, you have to install the G-Streamer packages and use Totem to play streaming audio. Rhythum Box or MMS didn't work...at least for me. Totem/Mplayer you have to manually type in the listen now link...then it will play...

Ubuntu will install 1/4 the time of a what a full install of Windows will take. When you do the text install it will ask some basic questions like keyboard layout, user name and password, and such.


I use Dban "Nuke and Boot"  from soundforce to wipe HD's clean...its free. Keep us posted.

---

### Post by deadgobby on 2007-08-22
Down like the wind...
GObby

---

### Post by Mek-Eng on 2007-08-22
Well, I'll have to wait till home to try the alternate version install, my plan for the computer is for my little brother to be able to play Runescape, write any reports and stuff he'll have (he's 14). I'd also like to be able to install Diabo II and to link the computer to my home network so I can print off the network printer. 
The Diablo II... if I can't get it working easily, I'll just put Win98 or Xp on a small hard drive and have it run off that (I may ask about dual booting eventually? Does it have to be windows first then Linux?) 
As for the networking, I've got a new Linksys Wireless-G Router with Linux core... I just assume Linux would be able to work with a Linux core.

---

