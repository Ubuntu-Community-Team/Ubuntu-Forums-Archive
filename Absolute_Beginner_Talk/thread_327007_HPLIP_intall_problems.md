---
title: "HPLIP intall problems"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Goweb on 2006-12-28
I went to the URL:

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

To install HPLIP 1.6.12 on my linux ubuntu 6.10 system.

I downloaded the driver (The Self-Extracting Archive With Installer) to my desktop...opened the terminal, made sure I was in the desktop directory and entered:

sh ./hplip-1.6.12.run

I get the following:
proweb@proweb-desktop:~$ sh ./hplip-1.6.12.run
sh: Can't open ./hplip-1.6.12.run

Any ideas?

---

### Post by meng on 2006-12-28
Try
cd Desktop
sh hplip(etc)

---

### Post by Goweb on 2006-12-28
Hey That Worked!

Now Im getting this:

Before proceeding please enable the universe/multiverse repositories in Synaptic or Apt.  In addition disable the Ubuntu CD source.

Im a newbie on Linux....have no idea what to do on the above mentioned steps...

How is this done? Thx!

---

### Post by meng on 2006-12-28
Go to Synaptic Package Manager (under System > Admin)
Go to Repositories, somewhere in the toolbar/menu.
Uncheck the CD repository, check every other offered repository. Click Reload.
Done.

---

### Post by Goweb on 2006-12-28
Thx for your help!

The install has been going for over 2 hours now......Why so long???

Says:

DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
note: You may be prompted for a password. Please enter the appropriate password for your system for 'sudo' when prompted.
Running 'sudo apt-get install --force-yes --yes build-essential libjpeg62-dev build-essential python-dev libcupsys2-dev libusb-dev lsb openssl libsnmp9-dev python-qt3 python-reportlab sane-utils'
Please wait, this may take several minutes...

Any ideas??

---

### Post by paridoth on 2007-01-03
> **Goweb said:**
> Thx for your help!

The install has been going for over 2 hours now......Why so long???

Says:

DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
note: You may be prompted for a password. Please enter the appropriate password for your system for 'sudo' when prompted.
Running 'sudo apt-get install --force-yes --yes build-essential libjpeg62-dev build-essential python-dev libcupsys2-dev libusb-dev lsb openssl libsnmp9-dev python-qt3 python-reportlab sane-utils'
Please wait, this may take several minutes...

Any ideas??

im getting the exact same problem, just sits there.

---

### Post by water on 2007-01-06
I've got the problem as well, my issues is related to lsb - the lsb install fails due to some issue with postfix 

If you run ```
sudo apt-get install lsb
``` you'll see the errors

I have no idea how to take it from here, and at the moment I haven't got the time to try and figure it out either...

:water

---

### Post by Phosphoric on 2007-01-07
> **paridoth said:**
> im getting the exact same problem, just sits there.

Me too. :(

---

### Post by 11hjpphty76lkjj on 2007-01-12
I'll update the documentation from sh ./hplip<version> to sh hplip<version>

Now why it's taking so long...there is a problem where during the lsb install postfix is downloaded and wants to be configured--however it hangs.  I'm working on a work around.  Currently you can install lsb manually as water stated.  Also because the postfix install doesn't finish if you exit out of the installer apt will break.

Run 

sudo apt-get install -f
then
sudo apt-get install lsb

and then re-run the installer.

I'm working on a work around.

Aaron

---

### Post by Phosphoric on 2007-01-13
moved a step closer now, thanks Aaron.

I've now got the HP device manager and it has correctly spotted my PSC1400 series.  However, when I click on the scan icon Xsane goes off for a long time and eventually comes back with. 
 "Failed to open device "hpaio:/usb/PSC_1400_series?serial=blah blah"
Error during device i/o

Any ideas where to next?

Thanks.

---

### Post by 11hjpphty76lkjj on 2007-01-13
can you run

sudo tail -f /var/log/messages

and then in another terminal window run xsane, and go back to /var/log/messages and post any errors.

Aaron

---

### Post by Phosphoric on 2007-01-14
Hi Aaron,

here's what I get:

ray@ubuntu:~$ sudo tail -f /var/log/messages
Jan 14 09:45:42 ubuntu gconfd (ray-5103): Resolved address "xml:readwrite:/home/ray/.gconf" to a writable configuration source at position 1
Jan 14 09:45:42 ubuntu gconfd (ray-5103): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 14 09:45:42 ubuntu gconfd (ray-5103): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 14 09:45:42 ubuntu gconfd (ray-5103): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 14 09:45:46 ubuntu gconfd (ray-5103): Resolved address "xml:readwrite:/home/ray/.gconf" to a writable configuration source at position 0
Jan 14 09:48:08 ubuntu hpiod: removing usblp driver interface=1 for hp:/usb/PSC_1400_series?serial=MY5CKCD03P04BM io/hpiod/device.cpp 504
Jan 14 09:48:08 ubuntu kernel: [17179783.696000] drivers/usb/class/usblp.c: usblp0: removed
Jan 14 09:50:50 ubuntu exiting on signal 15
Jan 14 09:50:51 ubuntu syslogd 1.4.1#17ubuntu7: restart.
Jan 14 09:52:07 ubuntu hpiod: device cleanup uri=hp:/usb/PSC_1400_series?serial=MY5CKCD03P04BM


Sorry, don't know how to attch the contents of terminal properly.

Thanks:)

I found some info elsewhere that made sure that my scanner was added to "etc/udev/rules.d "file 45-libsane rules.
I found the Product and Vendor ID for my scanner from "lsusb" and added the following line in to 45-libsane rules:

#HP PSC1410
SYSFS[idVendor}=="03f0",SYSFS{idProduct}=="4d11".MODE="664",GROUP="scanner"

It didn't do anything eitherway.

---

### Post by 11hjpphty76lkjj on 2007-01-14
Have you looked over this doc?

[http://hplip.sourceforge.net/troubleshooting/scanning.html](http://hplip.sourceforge.net/troubleshooting/scanning.html)

---

### Post by Phosphoric on 2007-01-14
Thanks Aaron,  I've looked at that document.

I don't have a /etc/sane/dll.conf file but I do have /etc/sane.d/dll.conf.  Using "gedit" I find that I have an entry for hpaio which is un-commented.

When I try to run "$ export SANE_DEBUG_DLL=128 $ scanimage -L" 
I get
"bash: $: command not found"

I'm not getting on very well here:(

---

### Post by moshuptrail on 2007-01-14
when you see a $ in the middle of a command, just split it to two lines:
$ export SANE_DEBUG_DLL=128
$ scanimage -L


I've seen that syntax before, but it never works.  Not sure why it's posted that way.

---

### Post by Phosphoric on 2007-01-14
Well I've tried splitting that command but nothing obvious happens for me.

Geez...... why is it so hard?  I just want my scanner to work which goes perfectly in XP.

I've been struggling with Ubuntu for 4 or 5 months now, on my 5th install.  Still can't get basic stuff to work.:( 

Where are all the lucky people that get it to work straight out of the box?








I'm drowning here.

---

### Post by moshuptrail on 2007-01-14
When you type
$ scanimage -L

you should get get lot of output, that's what Aaron wanted posted.  (BTW aaron is an expert on this, he helped me through some issues)

I am using hplip 1.6.12 with an OfficeJet V40 for scanning and printing.  I haven't used it for faxing yet.

P.S. Did you check if your printer is on the supported list (sorry if you already posted that)?
PPS. if you get command not found for scanimage, you need to install sane-utils first

---

### Post by Phosphoric on 2007-01-15
I have sane utils installed according to synaptic package manager.  This is my terminal output:

ray@ubuntu:~$ $ export SANE_DEBUG_DLL=128
bash: $: command not found
ray@ubuntu:~$ $ scanimage -L
bash: $: command not found
ray@ubuntu:~$


I must be doing something basic wrong here, I'm very new to terminal work. :( 

Thanks again.

---

### Post by macogw on 2007-01-15
HPLIP is part of the default install, isn't it?  I didn't have any setup for installing HP printers with either of my Ubuntu boxes.  Just System > Administration > Printers, add new printer, choose which HP printer you have so that it knows which driver piece, and you're done.

---

### Post by Phosphoric on 2007-01-15
@ macogw,
yes the printer setup is straight forward, worked straight away for me, however I have an HP PSC 1410 and I can't get the scanner to work (or even be recognised)
I'm half way there with the help of previous posters, so fingers crossed for some help with the final push.

Thanks.:)

---

### Post by Phosphoric on 2007-01-17
> **Phosphoric said:**
> I have sane utils installed according to synaptic package manager.  This is my terminal output:

ray@ubuntu:~$ $ export SANE_DEBUG_DLL=128
bash: $: command not found
ray@ubuntu:~$ $ scanimage -L
bash: $: command not found
ray@ubuntu:~$


I must be doing something basic wrong here, I'm very new to terminal work. :( 

Thanks again.

Is my problem here the " $ $ "?

The code I was instructedd to put in the terminal was "$ export SANE_DEBUG_DLL=128"

Should I leave off the $ at the beginning?

I'll try this when I get home this evening.

Thanks

---

### Post by Phosphoric on 2007-01-17
Well, I still don't know about $ $ but I now have a functioning scanner.

Dead easy when you know......turn it of and turn it back on again! :-k 

Don't know yet if this is a permanent fix but I can finally get on with the next problem now.


Thanks. :)

---

