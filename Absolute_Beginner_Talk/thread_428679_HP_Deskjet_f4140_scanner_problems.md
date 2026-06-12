---
title: "HP Deskjet f4140 scanner problems"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Qchan on 2007-04-30
[b][color=darkred]
I don't know how many out there can help me, but I'm at a loss here.

I first had a Lexmark All in One which was utter garbage. After getting it installed, it did what it was supposed to. The scanner even worked. Now, the scanner on the Lexmark appeared to have been dying on me, so I went out and got an HP All in One. I've been hearing how HPs work fantatically on Linux. Heck, I even installed and HP on my mother's PC running Ubuntu. Works flawlessly!

Anyway, I get the HP Deskjet f4140 All in One home. Linux detects the printer almost instantly. I was able to get the printer working and networked with my home lan almost painlessly. The next thing I needed to do was scan. I opened Xsane and it told me it couldn't detect it. I thought that was pretty weird. I scrambled to find out why Xsane couldn't detect it. I went all over the Internet searching for answers. I typed lsusb and of course the all in one is seen. I typed in 'sane-find-scanner' and it sees the scanner.

> 
~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [HP], product=0x7e04 [Deskjet F4100 series]) at libusb:002:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


Yet I can't get Xsane (or Sane for that matter) to find it. I first thought that maybe it wasn't supported, but being that this is an HP, I knew there had to have been a backend that would work with it. As long as its detected, I should be able to use the hp.conf backend. I edited the file and even added the usb <enter hex numbers here> and restarted sane. Heck, I even restarted the PC. Nothing.

Can anyone help me out? I'm fresh out of ideas and there is literately NO Linux information about this All in One on the net AT ALL. NONE! Go ahead and go to Google and type "Linux HP Deskjet f4140" you will find 4 search queries and that is it. The queries don't even talk about HP and Linux in the same sentence.
[/b][/color]

---

### Post by Qchan on 2007-04-30
[b][color=darkred]
Any one? Suggestions are welcome. Even a weird guess would be better than nothing.
[/b][/color]

---

### Post by Qchan on 2007-04-30
[b][color=darkred]
What I'll do is I'll continue to work on this issue and when I find a solution I will post it here. I'm sure there are others out there who have this model all in one with the same issues.
[/b][/color]

---

### Post by Qchan on 2007-05-08
[b][color=darkred]
Alright. Here's an update.

It appears as though this particular scanner is not supported. The printer portion is, but not the scanner. It also appears as though most (if not all) of the HP Deskjet series scanners are not supported under SANE. I tried to find an equivlent driver for this particular series, but it was a no go.

For anyone who has issues with this scanner, what you can do is use a Virtual Box (Vmware or Virtual Box) to run a session of Windows XP. Have that Virtual Box point to the scanner and use Windows XP under Linux to do the scanning. You can use GIMP for Windows to do the scanning (I wouldn't use HP's software). From there, you can put the scans on a shared directory and it'll work that way.

If I come across anymore updates, I'll be sure to let all of you know.
[/b][/color]

---

### Post by lessgov2007 on 2007-05-16
I just bought the same All-in-One Printer F4140 and had the same problems.  I visited the Sane website only to find they do not support the Deskjet series of printers and scanners.  I stumbled on a program package produced for HP printers such as ours.  It's produced as an open source free project for download.  I believe this is an HP sponsored project.  Anyways to the point. [ Visit this website and download the package]("http://hplip.sourceforge.net/index.html") which, ends with a .run extension.  You will need to make the file executable before you install it.  You will also need root password to install.  You may even get some error messages as I did throughout the installation process.  It took some time to install but everything works great!  I can print and scan now using xsane or sane.  You will even have a little utility program to manage your printer.  Kinda like you would have in a Windoze OS.  I hope this helps you get up an running.  This works with many models and distro's so check out this site it may solve your problem.

---

### Post by paulmac on 2007-07-10
May or may not apply to this thread.  HP Deskjet F4140 has issues with on board scanning/printing.  Very, very slow.

Just spent an hour and one half with HP and they are sending a warranty replacement for my 2 month old Deskjet F4140.

I have Ubuntu on one machine and Mac on another and Xp on another.  This slow scanning and printing problem may have more to do with the F4140 than the OS since these problems were found by using the Copy Menu on the scanner/printer itself.  Please consider testing the machine by using the provided buttons before presuming the problem is with the OS.

With this defective machine (new) a typical color scan took 3 to 3.5 minutes.  A color copy to print took six minutes.  

HP was very helpful in the 1.5 hour diagnosis of this defective machine and sending a warranty replacement.

It may be your OS, it may be your all in one that is giving you fits.  Test it as afore described.

---

### Post by MissG on 2007-08-06
> **lessgov2007 said:**
> [ Visit this website and download the package]("http://hplip.sourceforge.net/index.html")
This completely did the trick for me. Thanks so much for posting.

---

### Post by cfrivas on 2007-08-08
My printing works but HP Device Manager-today-does not find printer; some kind of communications failure. Last night I was able to to print and scan, why not today!!!!!!!?
I did manage to install HPLIP_2.7.7 but for F4100 series, my printer is a F4140

---

### Post by cfrivas on 2007-08-09
I managed to calm down and correctly install HPLIP 2.7.7

---

### Post by samuelkarush on 2008-04-01
above instructions work very well for me using ubuntu 7.04 and hp deskjet and f4135 all in one. took about 15 min. including reading.
 thanks!
sk

---

### Post by Qchan on 2008-04-01
[b][color=darkred]
I want to say that the above solution worked well for me as well. In current versions of Ubuntu (Namely Gutsy), this printer works right out of the box.
[/b][/color]

---

