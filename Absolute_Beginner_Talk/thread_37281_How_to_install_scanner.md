---
title: "How to install scanner?"
date: 2005-05-26
forum: Absolute Beginner Talk
---

### Post by davidgypsy on 2005-05-26
.

---

### Post by apollyonis on 2005-05-28
First of all, USB or parallel?

---

### Post by davidgypsy on 2005-05-28
[QUOTE=apollyonis]First of all, USB or parallel?[/QUOTE]

Parallel.

---

### Post by jcplansi on 2005-09-22
usb

---

### Post by xmastree on 2005-09-22
Try searching the forums for **snapscan**. That's how I got mine working.

But we really need more info, like make and model at the very least.
Give us a chance.  :smile:

---

### Post by kaputek on 2005-09-22
I have problem with scaner too... 
I have a Plustek OpticPro U12B USB. When I connected it first time all works ok. Xsane detected it correct. But now when I try connect scanner (i thing that modules are loaded correctly)  xsane dont see my scaneer :( I really don't know what happend !

---

### Post by xmastree on 2005-09-22
what happens if you run xsane as root?
If that works, it's a permission problem on the scanner port. Find out where it is, by typing **lsusb** in a  terminal:

Here's mine:```
Bus 004 Device 003: ID 0aec:3260 Neodio Technologies Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
[COLOR=Red]Bus 002 Device 004: ID 066f:4200 SigmaTel, Inc. STIr4200 IrDA Bridge[/COLOR]
Bus 002 Device 003: ID 0403:fc82 Future Technology Devices International, Ltd
Bus 002 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c01a Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

```I don't have a scanner on this system, but let's pretend that the IrDA bridge is really a scanner...  :^o 

Look at what dev and bus it appears on, and do this:
```
sudo chmod 660 /proc/bus/usb/002/004
```substituting the correct numbers for bus and dev.

Now it should run as a regular user, at least until you restart...

---

### Post by kaputek on 2005-09-22
no it don't work... lsusb show scenner but xsane dont see it (on root too) xsane only show /dev/video. its my tvcard. but when I first time plugin scanner and start xsane show me info to chose between tvtuner and my scaner. now its only tuner....

---

### Post by bonjun on 2005-09-23
[QUOTE=xmastree]what happens if you run xsane as root?
If that works, it's a permission problem on the scanner port. Find out where it is, by typing **lsusb** in a  terminal:

Here's mine:```
Bus 004 Device 003: ID 0aec:3260 Neodio Technologies Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
[COLOR=Red]Bus 002 Device 004: ID 066f:4200 SigmaTel, Inc. STIr4200 IrDA Bridge[/COLOR]
Bus 002 Device 003: ID 0403:fc82 Future Technology Devices International, Ltd
Bus 002 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c01a Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

```I don't have a scanner on this system, but let's pretend that the IrDA bridge is really a scanner...  :^o 

Look at what dev and bus it appears on, and do this:
```
sudo chmod 660 /proc/bus/usb/002/004
```substituting the correct numbers for bus and dev.

Now it should run as a regular user, at least until you restart...[/QUOTE]

i have also scanner problem
i have tried this, but it does't work

scanner: Microtek ScanMaker 3840 (USB)
ubuntu: hoary

---

### Post by ferguds on 2005-09-25
[QUOTE=bonjun]i have also scanner problem
i have tried this, but it does't work

scanner: Microtek ScanMaker 3840 (USB)
ubuntu: hoary[/QUOTE]

sudo chmod 660 /proc/bus/usb/002/004
the above didn't work for me either...
but the following worked straight away!
$ sudo chmod 666 /proc/bus/usb/002/004

Thanks for the tip!

---

### Post by bonjun on 2005-09-27
[QUOTE=ferguds]sudo chmod 660 /proc/bus/usb/002/004
the above didn't work for me either...
but the following worked straight away!
$ sudo chmod 666 /proc/bus/usb/002/004

Thanks for the tip![/QUOTE]

done this, but, still, scanner don't work

---

### Post by bonjun on 2005-09-28
I need help with my scanner (Mcrotek ScanMaker 3840, USB), i can't get it to work,
here's my list of usb devices

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 05da:30d4 Microtek International, Inc.
Bus 001 Device 001: ID 0000:0000

when i start "XSane Image Scanning Progra", it says no devices available

sudo chmod 660 /proc/bus/usb/001/002
and
sudo chmod 666 /proc/bus/usb/001/002
restart my pc, and restart XSane, i got the same error no devices available

and, i also run xsane on root, and it didn't work either, i got the same error no devices available

and when I .......... scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

i also tried installing the backend driver for my scanner...
i downloaded the driver and unpacked the package and try running the installation program (install-sh of the package)
this error appears: "install:              no input file specified"
is there something wrong with the way i install the package...
am i doing the right thing.....

---

### Post by xmastree on 2005-09-28
[QUOTE=bonjun]I
Bus 001 Device 002: ID 05da:30d4 Microtek International, Inc.

sudo chmod 666 /proc/bus/usb/001/002
restart my pc,
[/QUOTE]Don't restart it. If you do it will reset the permissions back again. 
I also had to use the driver file from the windows installer. and edit /etc/saned.d/snapscan.conf to include it. as outlined in [this thread]("http://www.ubuntuforums.org/showthread.php?t=26911&highlight=snapscan")

Have you tried running xsane as root? if that works then it's only the permission thing you need to set

---

### Post by bonjun on 2005-09-28
[QUOTE=xmastree]
Have you tried running xsane as root? if that works then it's only the permission thing you need to set[/QUOTE]

i have tried it without restarting and xsane as root, still, i was unable to use the scanner

[QUOTE=xmastree]Don't restart it. If you do it will reset the permissions back again. 
I also had to use the driver file from the windows installer. and edit /etc/saned.d/snapscan.conf to include it. as outlined in [this thread]("http://www.ubuntuforums.org/showthread.php?t=26911&highlight=snapscan")
[/QUOTE]

windows installer?,,, that seems to be the problem,,,, i will follow the link

---

### Post by xmastree on 2005-09-28
Whoa confused the hell out of me there. I clicked reply with quote just as you edited your post and changed it completely... So I was quoting something completely different.

Anyway, it's /etc/sane.d not saned.d sorry for the confusion. You should have libsane installed, have a look in synaptic.

---

### Post by libertyaikido on 2005-09-28
This workaround is fine, but what's the fix for the problem?

Do we have to do the workaround every time we install Ubuntu on a new machine?

What's the fix that will no longer require you to change the permissions every time you reboot the machine.

---

### Post by Mustard on 2005-09-28
I imagine it's possible to write a script that would do it for you when the machine boots up.  Just a thought.  I wouldn't have a clue where to put it or how to call the script though. :)

---

### Post by najames on 2005-10-06
I have been flogging installing my old $10 GoogleGear USB scanner in Suse 10 (actually an Artec Ultima 2000) and finally got it to work tonight.  None of the stuff here really seemed to help.  su root and chmod 777 some of the dirs/files, didn't help.

1) go here and see if your scanner is listed in supported devices.  It said I needed this back-end Gt680xfw.usb for the Artec Ultima 2000.

    [http://www.sane-project.org](http://www.sane-project.org)

2) I edited the files and ran these commands and it seemed to know about my scanner.       

scanimage -L 
sane-find-scanner

3) I edited some of the .conf files listed in this thread.  Not really sure if it was needed. I did find an empty directory in /usr/share/sane/gt68xx/    Notice the similar name, like the driver?

4) Went to my WinXP PC and did a search for *.usb and it found the same named file, Gt680fw.usb and I copied it in the Linux directory in step 3.  I did NOT make any changes to the file or the name.

5) I started Kooka and it all finally worked.  The Kooka notice "that it couldn't find my scanner" was gone, and the software all worked.  I scanned a couple docs at 100 and 300dpi and called it good enough.

Finding the driver or "firmware" as mentioned sometimes is the key.  If you don't have the disks try the scanner company website for drivers.

I now have 2 reasons to do a temp install of WinXP, benchmark, install then steal drivers.  Then I can install Linux from scratch and wipe out WinXP.  Bill Gates ain't such a bad guy after all.

---

### Post by bonjun on 2005-10-08
i can't, still, get my scanner to work...
i have downloaded driver of sane-backends 1.0.16 with Microtek scanmaker 3840 support, but i can't install the driver, can anybody help me to install the driver...

thanks in advance

---

### Post by bonjun on 2005-11-03
just for update,,, i had compiled sane-backends 1.0.16, for it support my scanner, unfortunately, i was unable to use xsane as my gui for my scanner,,,, but, i can use my scanner at command line (terminal), by scanimage...

anybody, any idea how can i use xsane for my scanner

---

### Post by matchstich on 2006-12-15
i got command not found

---

### Post by HackerBaloo on 2008-01-07
After making this chmod. running xsane , I got the error: " Couldn't open firmware file (`/usr/share/sane/gt68xx/PS1Gfw.usb'): No such file or directory"
I have a Packard Bell 1200 Diamond Plus, and to make it work I downloaded a driver file from:
[http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)
and copied it to /usr/share/sane/gt68xx/

And now it works :o)

---

### Post by famleon on 2008-04-26
i review the data

Bus 003 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner

and I run the xsane but i got the error Failes to open device gt68xx:libusb:003:002: invalid argument

---

### Post by SumnerBoy on 2008-04-27
I can see my scanner via lsusb and scanimage -L. I have installed SaneTwain on my Windoze laptop and configured xinetd for SANED with saned:scanner.

However when I try to access the scanner I get a user permission error. The only way I can get it to work is to change the xinetd config be root:scanner.

This is obviously far from ideal (having an external port exposed with root permissions). Anyone know how to get it to work with saned:scanner?

---

### Post by encompass on 2008-04-27
have you tried this?
[http://ubuntuforums.org/showthread.php?t=669135](http://ubuntuforums.org/showthread.php?t=669135)
It may help...

---

### Post by encompass on 2008-04-27
And are you running 64 bit ubuntu or 32 bit ubuntu?
It seems you may also have this bug...
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/115898](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/115898)
They have a work around but it a little work to get it going.

---

### Post by SumnerBoy on 2008-04-28
Hey guys - thanks for the links to those posts. I have tried both the v18 and v15 versions of the libsane-sm3840 libraries but neither seemed to work.

My scanner is definitely working and is recognised by the system but it won't grant access when running as saned (via xinetd). I can't see why this won't work - saned is definitely a member of the scanner group.

Any other ideas?

---

### Post by SumnerBoy on 2008-05-01
BTW - encompass - I am running Ubuntu 8.04 32 bit.

---

### Post by persianprez on 2008-05-01
my hp scanner was automaticcaly installed without any drivers or such.  it is also connected with usb. to scan, i used to the program that came with ubuntu, im not on my laptop right now so i cant say which program it is as i dont remember.

---

