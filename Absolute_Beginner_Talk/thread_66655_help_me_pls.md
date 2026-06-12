---
title: "help me pls"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by energeist on 2005-09-18
im a complete newbie on LINUX so pls someone help me.

I dont know how start installing Ubuntu.
i dont know the commands to start the installation.
can someone help me with the whole process

---

### Post by aysiu on 2005-09-18
For Ubuntu, read this:

[https://wiki.ubuntu.com/Installation/I386](https://wiki.ubuntu.com/Installation/I386)

But something tells me that for Linux in general you may want to start with this:

[http://www.psychocats.net/essays/linuxguide.php](http://www.psychocats.net/essays/linuxguide.php)

---

### Post by energeist on 2005-09-18
the guide says that there will be a spash screen asking me to pick a language.
but there wasn't any for me.

I have a brand new HD where i am to install ubuntu.
I boot from CD Drive and i have downloaded the ISO from the site.

it waits for me to type a command:

"[DR-DOS] A:\>  "

what should i type or do.
Im a complete noob at this one.
i can handle Windows but i cant think on how to install Ubuntu.
Help me pls T_T

The one that i downloaded at the site is the:

Ubuntu 5.10 (Breezy Badger)
PC (Intel x86) install CD

---

### Post by aysiu on 2005-09-18
[QUOTE=energeist]
I boot from CD Drive and i have downloaded the ISO from the site.

it waits for me to type a command:

"[DR-DOS] A:\>  "
[/QUOTE] Wait. Did you *burn* the ISO, or did you just download it? Did you burn the ISO as a disk image or as data? DR-DOS A:\> means you're probably in DOS--i.e., Windows. You're not booting off the Ubuntu CD.

I'm not kidding about reading the link I gave you before.

[http://www.psychocats.net/essays/linuxguide.php](http://www.psychocats.net/essays/linuxguide.php)

Please, read that through in its entirety. It took me quite a while to write, but it's everything I wish someone had told me when I first started with Linux--it includes info on ISOs and BIOS settings. Read it.

---

### Post by drogoh on 2005-09-18
DR-DOS?  No, that isn't even Windows at all, sounds more like a boot floppy to me.  Remove any disk you may have in your floppy drive and try booting with just the Ubuntu CD in the CD-ROM.

---

### Post by Blue1k on 2005-09-18
Check your PM.. :)

---

### Post by energeist on 2005-09-18
OK i have gathered info that i need to boot it manually.
how do i start it manually.
what are the commands.
im currently searching for the file that will make 
the installer run.

help me anyone pls

---

### Post by Blue1k on 2005-09-18
There is no manual need for anything. 

Just make sure in BIOS that your Boot squence is set to CDROM first before IDE (hardrive).

Once you have burned the ISO to disk all you need to do is restart with the new Ubuntu CD in the tray and the boot menu will start automatically

---

### Post by Emerzen on 2005-09-18
Hi Energeist...it sounds like you're having a couple of problems:

1.)  You need to get into your PCs BIOS.  This is a small program that runs before any operating system.  When you 1st turn your computer on you should see a screen w/ the PC vendor's name flash by and a message something like, "Press F1 for setup."  It may not be F1 but you'll have to watch for this.  Whatever key it tells you to press, you need to press it rapidly to enter the setup program known as the BIOS.  If Windows or DOS boots up, it's too late and you have to start over.  You should see a text based screen pop up that you navigate through w/ the arrow keys (usually).  Once there you have to look for a section on "boot order" or "boot set-up" or something like that.  (Sorry to be vague but the BIOS is pretty specific to the PC Vendor).  Once you find this, make sure the first device you are booting from is your CDROM drive.

2.)  If #1 is done, put the Ubuntu CD into the CD drive and turn your computer off, then turn it back on.  The PC should now boot from the CD ROM (you should hear the CD ROM makeing alot of noise).  You will see an Ubuntu screen w/ logo pop up shortly if all is well.  Once that pops up, press enter for a 'typical' install.  

If you're sure your PC is booting from the CD and you are getting a C:> prompt, then something is wrong with the CD, in other words, you've booted into Windows/DOS.  A few posts above someone asked if you had burned the CD as an ISO or as a DATA CD.

Burning an ISO is not the same as just copying files to the CD and burning them.  Whatever software you used to burned the ISO, Nero for example, should have an option to "burn an ISO."  You have to select this option to burn the ISO and make it bootable.  

Hope that helps.  Let me know what problems you run in to and I'll try to help.

---

