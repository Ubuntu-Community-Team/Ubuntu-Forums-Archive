---
title: "Desperate help with scanner"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by evilc on 2006-03-11
I have available 3 scanners.
1/Logitech Pagescan (USB)
2/Microtek ScanMaker 3730 (USB)
3/ Plustek OpicPro 9630P (Cable)

I have installed QuiteInsane and Xsane both show up in Gimp2 I need to install anyone of the scanners but have no idea how, can someone lead me through the installation, treat me as a 4 year old my knowledge of linux terms are nil.:confused:

Thanks

---

### Post by Pragmatist on 2006-03-11
Do not despair. Your in luck, one of your scanners works!!

Read these and come back when your stuck:
```
man sane-plustek_pp
```
[http://www.tldp.org/HOWTO/html_single/Scanner-HOWTO/](http://www.tldp.org/HOWTO/html_single/Scanner-HOWTO/)
[http://www.linuxmanpages.com/man5/sane-plustek.5.php](http://www.linuxmanpages.com/man5/sane-plustek.5.php)

Also do this to find other man pages related to plustek:
```
man -k plustek
```

---

### Post by evilc on 2006-03-12
Pragmatist, thanks had a look seems the OpticPro should work but I have no idea how to install it, the links lead to what I need but not knowing linux expressions or  codes  leaves me  clueless.

---

### Post by Pragmatist on 2006-03-12
Ok, lets start with these questions:
1.) can you also use USB with your scanner or do you only have parallel cable?
2.) If you only have parallel cable, try this:

(a) connect your scanner and then boot your computer

(b) open a terminal (look through the main menu under utilities or system or something like that. If you peruse the menus you'll find something called terminal.)

(c) type this: [B]scanimage -L

[/B](d) cut the output by highlighting with your mouse, right-clicking and selecting cut.

(e) paste what you cut into your post.

---

### Post by evilc on 2006-03-12
here's what showed:

clive@ubuntu:~$ scanimage -L
device "snapscan:libusb:004:002" is a Acer FlatbedScanner22 Flatbed scanner
clive@ubuntu:~$

( I could not copy this from terminal & there was no cut option?)

thx

I have stuffed up used this link [http://www.ubuntuforums.org/showthread.php?t=106647&highlight=plustek+scanner](http://www.ubuntuforums.org/showthread.php?t=106647&highlight=plustek+scanner) and the last code screen went berserk on me I have sane and bits and pieces all over the place. should I reformat and start again? btw the scanner I have is not Acer but may possibly work

---

### Post by nalmeth on 2006-03-12
An easy way to copy/paste in linux:
highlight the text (this copies it) 
click middle (scroll) button, or left and right buttons at once to paste

don't know anything about scanners in linux tho sorry!

---

### Post by evilc on 2006-03-12
Nalmeth, sorry don't work my scroll button is set to auto scroll tried both l/r buttons only activates scroll. ( I'm using Firefos with all in one gestures extention)

---

### Post by BoyOfDestiny on 2006-03-12
[QUOTE=evilc]Nalmeth, sorry don't work my scroll button is set to auto scroll tried both l/r buttons only activates scroll. ( I'm using Firefos with all in one gestures extention)[/QUOTE]

He means it will paste in terminal.

Anyway normally copy and paste are ctrl + c and ctrl +v (respectively)

in a terminal window

shift + ctrl + c is copy
shift + ctrl + v is paste

Hope that helps =)

Also, there is the gui way, either via menu or right clicking...

---

### Post by evilc on 2006-03-12
shift + ctrl + c is copy
shift + ctrl + v is paste
Duh I've been on computer too long going brain dead. Thanks for reminding me.

---

### Post by Pragmatist on 2006-03-12
>  I have stuffed up used this link [http://www.ubuntuforums.org/showthre...lustek+scanner]("http://www.ubuntuforums.org/showthread.php?t=106647&highlight=plustek+scanner") and the last code screen went berserk on me 

The advice in that post is not for your model scanner.

Did you have the "Plustek OpicPro 9630P (Cable)" scanner plugged in?  Was it the only scanner you had plugged in?

---

### Post by evilc on 2006-03-12
[QUOTE=Pragmatist]The advice in that post is not for your model scanner.

Did you have the "Plustek OpicPro 9630P (Cable)" scanner plugged in?  Was it the only scanner you had plugged in?[/QUOTE]

I have played safe and re-installed Ubuntu. I rerun scan command and got the following,

clive@ubuntu:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
clive@ubuntu:~$

The scanner is the Plustek OpticPro 9630P with cable.

Thanks

---

### Post by Pragmatist on 2006-03-12
Do this: [B]cd /usr/share/doc/libsane/plustek
[/B]Then follow these instructions (found in **/usr/share/doc/libsane/plustek/Plustek-PARPORT.txt** I just added sudo):

**sudo **./MakeModule.sh

Then the module should be compiled, installed and loaded.

Add the following three lines to file /etc/modules.conf

alias char-major-40     pt_drv
pre-install pt_drv modprobe -k parport
options pt_drv lampoff=180 warmup=15 port=0x378 lOffonEnd=0 mov=0 slowIO=1

See man page for sane-plustek_pp ("man sane-plustek_pp") for explanation of
these options.

Now "scanimage -L" should show something like this:
device `plustek:/dev/pt_drv' is a Plustek 9630P flatbed scanner

---

### Post by evilc on 2006-03-13
[QUOTE=Pragmatist]Do this: [B]cd /usr/share/doc/libsane/plustek
[/B]Then follow these instructions (found in **/usr/share/doc/libsane/plustek/Plustek-PARPORT.txt** I just added sudo):

**sudo **./MakeModule.sh

Then the module should be compiled, installed and loaded.

Add the following three lines to file /etc/modules.conf

alias char-major-40     pt_drv
pre-install pt_drv modprobe -k parport
options pt_drv lampoff=180 warmup=15 port=0x378 lOffonEnd=0 mov=0 slowIO=1

See man page for sane-plustek_pp ("man sane-plustek_pp") for explanation of
these options.

Now "scanimage -L" should show something like this:
device `plustek:/dev/pt_drv' is a Plustek 9630P flatbed scanner[/QUOTE]


Sorry to be pain but failed see copy of terminal,

clive@ubuntu:~$ cd /usr/share/doc/libsane/plustek
clive@ubuntu:/usr/share/doc/libsane/plustek$ sudo ./MakeModule.sh
sudo: ./MakeModule.sh: command not found
clive@ubuntu:/usr/share/doc/libsane/plustek$

---

### Post by Pragmatist on 2006-03-13
Give the output of this:
```
cd /usr/share/doc/libsane/plustek
``` 
```
ls -l
```
```
uname -r
```

---

### Post by evilc on 2006-03-13
[QUOTE=Pragmatist]Give the output of this:
```
cd /usr/share/doc/libsane/plustek
``` 
```
ls -l
```
```
uname -r
```[/QUOTE]

clive@ubuntu:~$ cd /usr/share/doc/libsane/plustek
clive@ubuntu:/usr/share/doc/libsane/plustek$ ls -l
total 48
-rw-r--r--  1 root root 4744 2005-09-28 00:14 FAQ.gz
-rw-r--r--  1 root root 2476 2005-09-28 00:14 Makefile.kernel24.gz
-rw-r--r--  1 root root 2808 2005-09-28 00:14 Makefile.kernel26
-rw-r--r--  1 root root 2509 2005-09-28 00:14 MakeModule.sh
-rw-r--r--  1 root root 2290 2005-09-28 00:14 Plustek-PARPORT.changes.gz
-rw-r--r--  1 root root 1615 2005-09-28 00:14 Plustek-PARPORT-TODO.txt
-rw-r--r--  1 root root 1633 2005-09-28 00:14 Plustek-PARPORT.txt
-rw-r--r--  1 root root 2871 2005-09-28 00:14 Plustek-USB.changes
-rw-r--r--  1 root root 2470 2005-09-28 00:14 Plustek-USB-TODO.txt
-rw-r--r--  1 root root 5696 2005-09-28 00:14 Plustek-USB.txt.gz
clive@ubuntu:/usr/share/doc/libsane/plustek$ uname -r
2.6.12-10-686

---

### Post by Pragmatist on 2006-03-13
>  sudo: **./**MakeModule.sh: command not found 
My mistake, I forgot to remove the **./**

Type exactly this: 
 [B]
cd /usr/share/doc/libsane/plustek

[/B]and then

[B]sudo MakeModule.sh
[/B]

---

### Post by evilc on 2006-03-13
[QUOTE=Pragmatist]My mistake, I forgot to remove the **./**

Type exactly this: 
 [B]
cd /usr/share/doc/libsane/plustek

[/B]and then

[B]sudo MakeModule.sh
[/B][/QUOTE]


This is crazy I know it's there but getting this,

clive@ubuntu:~$ cd /usr/share/doc/libsane/plustek
clive@ubuntu:/usr/share/doc/libsane/plustek$ sudo MakeModule.sh
Password:
sudo: MakeModule.sh: command not found

---

### Post by Pragmatist on 2006-03-13
Your not crazy, I just got the same message.  The reason is that there are no execute permissions set on the script MakeModule.sh (don't ask me why :)
** -rw-r--r--**  1 root root 2509 2005-09-28 00:14 MakeModule.sh
See how there are r and w but no x.  So we do this:
```
sudo chmod 744 MakeModule.sh
```
Now if you list the files again with **ls -l **, MakeModule.sh permissions look like this:
[B]-rwxr--r--  1 root root 2509 Sep 27 07:14 MakeModule.sh
[/B]Now try **NOTE: IT IS CORRECT WITH THE ./ ** the problem was the permissions:
**sudo ./MakeModule.sh**

---

### Post by evilc on 2006-03-13
Almost got past that one,

clive@ubuntu:/usr/share/doc/libsane/plustek$ sudo ./MakeModule.sh
This script will try and build a suitable kernel-module for your system.
If you'd like to make the module WITH debug output, restart this script
with as follows:
./MakeModule.sh DEBUG=y
Press <ENTER> to continue or <CTRL><C> to cancel.

Check for root - done.

Check for kernelversion:
Using makefile for kernel 2.6.x
Build-directory:
/usr/share/doc/libsane/plustek/build
Removing build-directory - done.
Creating build-directory - done.

Linking source files...ls: /usr/share/doc/libsane/plustek/../../backend/plustek-pp_*.c: No such file or directory
ls: /usr/share/doc/libsane/plustek/../../backend/plustek-pp_*.h: No such file or directory
 - done.
Copying Makefile to build-directory - done.
Making the module...
make: *** /lib/modules/2.6.12-10-686/build/: No such file or directory.  Stop.
There were some build errors...
clive@ubuntu:/usr/share/doc/libsane/plustek$

---

### Post by Pragmatist on 2006-03-13
Enough is enough :)  I actually downloaded this package to make sure it has what you need and it DOES:

Go here:
[B][http://alioth.debian.org/project/showfiles.php?group_id=30186](http://alioth.debian.org/project/showfiles.php?group_id=30186)

[/B]and download this file:[B]
[sane-backends-1.0.17.tar.gz]("http://alioth.debian.org/download.php/1347/sane-backends-1.0.17.tar.gz")

[/B]Save it to your home directory and type this:
```
tar xvzf sane-backends-1.0.17.tar.gz
```

Then this:
```
cd  sane-backends-1.0.17
```

Then this:
```
sudo cp -r backend /usr/share 
```

Then this:
```
cd /usr/share/doc/libsane/plustek
```

Finally THEN this :)
```
sudo ./MakeModule.sh
```

---

### Post by evilc on 2006-03-13
Your not going to believe this?

sane-backends-1.0.17/backend/plustek-pp_genericio.c
sane-backends-1.0.17/backend/plustek-pp_hwdefs.h
sane-backends-1.0.17/backend/plustek-pp_image.c
sane-backends-1.0.17/backend/plustek-pp_io.c
sane-backends-1.0.17/backend/plustek-pp_map.c
sane-backends-1.0.17/backend/plustek-pp_misc.c
sane-backends-1.0.17/backend/plustek-pp_models.c
sane-backends-1.0.17/backend/plustek-pp_motor.c
sane-backends-1.0.17/backend/plustek-pp_p12.c
sane-backends-1.0.17/backend/plustek-pp_p12ccd.c
sane-backends-1.0.17/backend/plustek-pp_p48xx.c
sane-backends-1.0.17/backend/plustek-pp_p9636.c
sane-backends-1.0.17/backend/plustek-pp_procfs.c
sane-backends-1.0.17/backend/plustek-pp_procs.h
sane-backends-1.0.17/backend/plustek-pp_ptdrv.c
sane-backends-1.0.17/backend/plustek-pp_scale.c
sane-backends-1.0.17/backend/plustek-pp_scan.h
sane-backends-1.0.17/backend/plustek-pp_scandata.h
sane-backends-1.0.17/backend/plustek-pp_sysdep.h
sane-backends-1.0.17/backend/plustek-pp_tpa.c
sane-backends-1.0.17/backend/plustek-pp_types.h
sane-backends-1.0.17/backend/plustek_pp.c
sane-backends-1.0.17/backend/plustek-pp_wrapper.c
sane-backends-1.0.17/backend/plustek_pp.conf
sane-backends-1.0.17/backend/plustek-pp.h
sane-backends-1.0.17/backend/pnm.c
sane-backends-1.0.17/backend/qcam.c
sane-backends-1.0.17/backend/qcam.conf
sane-backends-1.0.17/backend/qcam.h
sane-backends-1.0.17/backend/ricoh.c
sane-backends-1.0.17/backend/ricoh.conf
sane-backends-1.0.17/backend/ricoh.h
sane-backends-1.0.17/backend/ricoh-scsi.c
sane-backends-1.0.17/backend/s9036.c
sane-backends-1.0.17/backend/s9036.conf
sane-backends-1.0.17/backend/s9036.h
sane-backends-1.0.17/backend/saned.conf
sane-backends-1.0.17/backend/sane_strstatus.c
sane-backends-1.0.17/backend/sceptre.c
sane-backends-1.0.17/backend/sceptre.conf
sane-backends-1.0.17/backend/sceptre.h
sane-backends-1.0.17/backend/sharp.c
sane-backends-1.0.17/backend/sharp.conf
sane-backends-1.0.17/backend/sharp.h
sane-backends-1.0.17/backend/sm3600.c
sane-backends-1.0.17/backend/sm3600-color.c
sane-backends-1.0.17/backend/sm3600-gray.c
sane-backends-1.0.17/backend/sm3600.h
sane-backends-1.0.17/backend/sm3600-homerun.c
sane-backends-1.0.17/backend/sm3600-scanmtek.c
sane-backends-1.0.17/backend/sm3600-scantool.h
sane-backends-1.0.17/backend/sm3600-scanusb.c
sane-backends-1.0.17/backend/sm3600-scanutil.c
sane-backends-1.0.17/backend/snapscan.c
sane-backends-1.0.17/backend/snapscan.conf
sane-backends-1.0.17/backend/snapscan.h
sane-backends-1.0.17/backend/snapscan-scsi.c
sane-backends-1.0.17/backend/snapscan-sources.c
sane-backends-1.0.17/backend/snapscan-mutex.c
sane-backends-1.0.17/backend/snapscan-sources.h
sane-backends-1.0.17/backend/snapscan-usb.c
sane-backends-1.0.17/backend/snapscan-usb.h
sane-backends-1.0.17/backend/snapscan-options.c
sane-backends-1.0.17/backend/sp15c.c
sane-backends-1.0.17/backend/sp15c.conf
sane-backends-1.0.17/backend/sp15c.h
sane-backends-1.0.17/backend/sp15c-scsi.h
sane-backends-1.0.17/backend/st400.c
sane-backends-1.0.17/backend/st400.conf
sane-backends-1.0.17/backend/st400.h
sane-backends-1.0.17/backend/stubs.c
sane-backends-1.0.17/backend/tamarack.c
sane-backends-1.0.17/backend/tamarack.conf
sane-backends-1.0.17/backend/tamarack.h
sane-backends-1.0.17/backend/teco1.c
sane-backends-1.0.17/backend/teco1.h
sane-backends-1.0.17/backend/teco1.conf
sane-backends-1.0.17/backend/teco2.c
sane-backends-1.0.17/backend/teco2.conf
sane-backends-1.0.17/backend/teco2.h
sane-backends-1.0.17/backend/teco3.c
sane-backends-1.0.17/backend/teco3.conf
sane-backends-1.0.17/backend/teco3.h
sane-backends-1.0.17/backend/test.c
sane-backends-1.0.17/backend/test.conf
sane-backends-1.0.17/backend/test.h
sane-backends-1.0.17/backend/test-picture.c
sane-backends-1.0.17/backend/umax1220u.c
sane-backends-1.0.17/backend/u12.c
sane-backends-1.0.17/backend/u12.h
sane-backends-1.0.17/backend/u12-scanner.h
sane-backends-1.0.17/backend/u12-hwdef.h
sane-backends-1.0.17/backend/u12.conf
sane-backends-1.0.17/backend/u12-shading.c
sane-backends-1.0.17/backend/u12-tpa.c
sane-backends-1.0.17/backend/u12-ccd.c
sane-backends-1.0.17/backend/u12-hw.c
sane-backends-1.0.17/backend/u12-if.c
sane-backends-1.0.17/backend/u12-image.c
sane-backends-1.0.17/backend/u12-io.c
sane-backends-1.0.17/backend/u12-map.c
sane-backends-1.0.17/backend/u12-motor.c
sane-backends-1.0.17/backend/umax1220u-common.c
sane-backends-1.0.17/backend/umax1220u.conf
sane-backends-1.0.17/backend/umax.c
sane-backends-1.0.17/backend/umax.conf
sane-backends-1.0.17/backend/umax.h
sane-backends-1.0.17/backend/umax_pp.c
sane-backends-1.0.17/backend/umax_pp.conf
sane-backends-1.0.17/backend/umax_pp.h
sane-backends-1.0.17/backend/umax_pp_low.c
sane-backends-1.0.17/backend/umax_pp_low.h
sane-backends-1.0.17/backend/umax_pp_mid.c
sane-backends-1.0.17/backend/umax_pp_mid.h
sane-backends-1.0.17/backend/umax-scanner.c
sane-backends-1.0.17/backend/umax-scanner.h
sane-backends-1.0.17/backend/umax-scsidef.h
sane-backends-1.0.17/backend/umax-uc1200s.c
sane-backends-1.0.17/backend/umax-uc1200se.c
sane-backends-1.0.17/backend/umax-uc1260.c
sane-backends-1.0.17/backend/umax-uc630.c
sane-backends-1.0.17/backend/umax-uc840.c
sane-backends-1.0.17/backend/umax-ug630.c
sane-backends-1.0.17/backend/umax-ug80.c
sane-backends-1.0.17/backend/umax-usb.c
sane-backends-1.0.17/backend/v4l.c
sane-backends-1.0.17/backend/v4l.conf
sane-backends-1.0.17/backend/v4l-frequencies.h
sane-backends-1.0.17/backend/v4l.h
sane-backends-1.0.17/backend/sm3840.conf
sane-backends-1.0.17/backend/sm3840.c
sane-backends-1.0.17/backend/sm3840_lib.c
sane-backends-1.0.17/backend/sm3840_params.h
sane-backends-1.0.17/backend/sm3840_scan.c
sane-backends-1.0.17/backend/sm3840.h
sane-backends-1.0.17/backend/sm3840_lib.h
sane-backends-1.0.17/frontend/
sane-backends-1.0.17/frontend/Makefile.in
sane-backends-1.0.17/frontend/saned.c
sane-backends-1.0.17/frontend/scanimage.c
sane-backends-1.0.17/frontend/stiff.c
sane-backends-1.0.17/frontend/stiff.h
sane-backends-1.0.17/frontend/test.c
sane-backends-1.0.17/frontend/tstbackend.c
sane-backends-1.0.17/tools/
sane-backends-1.0.17/tools/hotplug/
sane-backends-1.0.17/tools/hotplug/libsane.usermap
sane-backends-1.0.17/tools/hotplug/libusbscanner
sane-backends-1.0.17/tools/hotplug/README
sane-backends-1.0.17/tools/hotplug-ng/
sane-backends-1.0.17/tools/hotplug-ng/convert-usermap.sh
sane-backends-1.0.17/tools/hotplug-ng/libsane.hotplug
sane-backends-1.0.17/tools/hotplug-ng/README
sane-backends-1.0.17/tools/udev/
sane-backends-1.0.17/tools/udev/convert-usermap.sh
sane-backends-1.0.17/tools/Makefile.in
sane-backends-1.0.17/tools/RenSaneDlls.cmd
sane-backends-1.0.17/tools/README
sane-backends-1.0.17/tools/libtool-get-dll-ext
sane-backends-1.0.17/tools/mustek600iin-off.c
sane-backends-1.0.17/tools/sane-config.in
sane-backends-1.0.17/tools/sane-desc.c
sane-backends-1.0.17/tools/check-usb-chip.c
sane-backends-1.0.17/tools/sane-find-scanner.c
sane-backends-1.0.17/tools/umax_pp.c
sane-backends-1.0.17/tools/xerox
sane-backends-1.0.17/tools/gamma4scanimage.c
sane-backends-1.0.17/tools/check-po.awk
sane-backends-1.0.17/doc/
sane-backends-1.0.17/doc/canon/
sane-backends-1.0.17/doc/canon/canon.changes
sane-backends-1.0.17/doc/canon/canon.install2700F.txt
sane-backends-1.0.17/doc/leo/
sane-backends-1.0.17/doc/leo/leo.txt
sane-backends-1.0.17/doc/matsushita/
sane-backends-1.0.17/doc/matsushita/matsushita.txt
sane-backends-1.0.17/doc/mustek/
sane-backends-1.0.17/doc/mustek/mustek.CHANGES
sane-backends-1.0.17/doc/mustek_usb/
sane-backends-1.0.17/doc/mustek_usb/mustek_usb.CHANGES
sane-backends-1.0.17/doc/mustek_usb/mustek_usb.TODO
sane-backends-1.0.17/doc/plustek/
sane-backends-1.0.17/doc/plustek/FAQ
sane-backends-1.0.17/doc/plustek/Makefile.kernel24
sane-backends-1.0.17/doc/plustek/Makefile.kernel26
sane-backends-1.0.17/doc/plustek/MakeModule.sh
sane-backends-1.0.17/doc/plustek/Plustek-PARPORT.changes
sane-backends-1.0.17/doc/plustek/Plustek-PARPORT-TODO.txt
sane-backends-1.0.17/doc/plustek/Plustek-PARPORT.txt
sane-backends-1.0.17/doc/plustek/Plustek-USB.changes
sane-backends-1.0.17/doc/plustek/Plustek-USB-TODO.txt
sane-backends-1.0.17/doc/plustek/Plustek-USB.txt
sane-backends-1.0.17/doc/u12/
sane-backends-1.0.17/doc/u12/U12.changes
sane-backends-1.0.17/doc/u12/U12.todo
sane-backends-1.0.17/doc/umax/
sane-backends-1.0.17/doc/umax/negative-types.txt
sane-backends-1.0.17/doc/umax/sane-logo.jpg
sane-backends-1.0.17/doc/umax/sane-umax-advanced.jpg
sane-backends-1.0.17/doc/umax/sane-umax-advanced-options-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-astra-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-config-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-histogram.jpg
sane-backends-1.0.17/doc/umax/sane-umax.jpg
sane-backends-1.0.17/doc/umax/sane-umax-mirage-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-not-listed-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-others-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-parport-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-powerlook-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-scanner-clones-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-speed-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-standard.jpg
sane-backends-1.0.17/doc/umax/sane-umax-standard-options-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-text2.jpg
sane-backends-1.0.17/doc/umax/sane-umax-text4.jpg
sane-backends-1.0.17/doc/umax/sane-umax-text.jpg
sane-backends-1.0.17/doc/umax/sane-umax-uc-doc.html
sane-backends-1.0.17/doc/umax/sane-umax-vista-doc.html
sane-backends-1.0.17/doc/umax/umax.BUGS
sane-backends-1.0.17/doc/umax/umax.CHANGES
sane-backends-1.0.17/doc/umax/umax.FAQ
sane-backends-1.0.17/doc/umax/umax.TODO
sane-backends-1.0.17/doc/sceptre/
sane-backends-1.0.17/doc/sceptre/s1200.txt
sane-backends-1.0.17/doc/teco/
sane-backends-1.0.17/doc/teco/teco1.txt
sane-backends-1.0.17/doc/teco/teco2.txt
sane-backends-1.0.17/doc/teco/teco3.txt
sane-backends-1.0.17/doc/gt68xx/
sane-backends-1.0.17/doc/gt68xx/gt68xx.CHANGES
sane-backends-1.0.17/doc/gt68xx/gt68xx.TODO
sane-backends-1.0.17/doc/niash/
sane-backends-1.0.17/doc/niash/niash.TODO
sane-backends-1.0.17/doc/mustek_usb2/
sane-backends-1.0.17/doc/mustek_usb2/mustek_usb2.CHANGES
sane-backends-1.0.17/doc/mustek_usb2/mustek_usb2.TODO
sane-backends-1.0.17/doc/icons/
sane-backends-1.0.17/doc/icons/contents.gif
sane-backends-1.0.17/doc/icons/index.gif
sane-backends-1.0.17/doc/icons/next.gif
sane-backends-1.0.17/doc/icons/next_gr.gif
sane-backends-1.0.17/doc/icons/previous.gif
sane-backends-1.0.17/doc/icons/previous_gr.gif
sane-backends-1.0.17/doc/icons/references.gif
sane-backends-1.0.17/doc/icons/references_gr.gif
sane-backends-1.0.17/doc/icons/up.gif
sane-backends-1.0.17/doc/icons/up_gr.gif
sane-backends-1.0.17/doc/figs/
sane-backends-1.0.17/doc/figs/area.eps
sane-backends-1.0.17/doc/figs/area.fig
sane-backends-1.0.17/doc/figs/flow.eps
sane-backends-1.0.17/doc/figs/flow.fig
sane-backends-1.0.17/doc/figs/hierarchy.eps
sane-backends-1.0.17/doc/figs/hierarchy.fig
sane-backends-1.0.17/doc/figs/image-data.eps
sane-backends-1.0.17/doc/figs/image-data.fig
sane-backends-1.0.17/doc/figs/xfer.eps
sane-backends-1.0.17/doc/figs/xfer.fig
sane-backends-1.0.17/doc/descriptions/
sane-backends-1.0.17/doc/descriptions/abaton.desc
sane-backends-1.0.17/doc/descriptions/agfafocus.desc
sane-backends-1.0.17/doc/descriptions/apple.desc
sane-backends-1.0.17/doc/descriptions/artec.desc
sane-backends-1.0.17/doc/descriptions/artec_eplus48u.desc
sane-backends-1.0.17/doc/descriptions/as6e.desc
sane-backends-1.0.17/doc/descriptions/avision.desc
sane-backends-1.0.17/doc/descriptions/bh.desc
sane-backends-1.0.17/doc/descriptions/canon630u.desc
sane-backends-1.0.17/doc/descriptions/canon.desc
sane-backends-1.0.17/doc/descriptions/canon_pp.desc
sane-backends-1.0.17/doc/descriptions/coolscan2.desc
sane-backends-1.0.17/doc/descriptions/coolscan.desc
sane-backends-1.0.17/doc/descriptions/dc210.desc
sane-backends-1.0.17/doc/descriptions/dc240.desc
sane-backends-1.0.17/doc/descriptions/dc25.desc
sane-backends-1.0.17/doc/descriptions/dll.desc
sane-backends-1.0.17/doc/descriptions/dmc.desc
sane-backends-1.0.17/doc/descriptions/epson.desc
sane-backends-1.0.17/doc/descriptions/fujitsu.desc
sane-backends-1.0.17/doc/descriptions/genesys.desc
sane-backends-1.0.17/doc/descriptions/gphoto2.desc
sane-backends-1.0.17/doc/descriptions/gt68xx.desc
sane-backends-1.0.17/doc/descriptions/hp4200.desc
sane-backends-1.0.17/doc/descriptions/hp5400.desc
sane-backends-1.0.17/doc/descriptions/hp.desc
sane-backends-1.0.17/doc/descriptions/hpsj5s.desc
sane-backends-1.0.17/doc/descriptions/ibm.desc
sane-backends-1.0.17/doc/descriptions/leo.desc
sane-backends-1.0.17/doc/descriptions/lexmark.desc
sane-backends-1.0.17/doc/descriptions/ma1509.desc
sane-backends-1.0.17/doc/descriptions/matsushita.desc
sane-backends-1.0.17/doc/descriptions/microtek2.desc
sane-backends-1.0.17/doc/descriptions/microtek.desc
sane-backends-1.0.17/doc/descriptions/mustek.desc
sane-backends-1.0.17/doc/descriptions/mustek_pp.desc
sane-backends-1.0.17/doc/descriptions/mustek_usb2.desc
sane-backends-1.0.17/doc/descriptions/mustek_usb.desc
sane-backends-1.0.17/doc/descriptions/nec.desc
sane-backends-1.0.17/doc/descriptions/net.desc
sane-backends-1.0.17/doc/descriptions/niash.desc
sane-backends-1.0.17/doc/descriptions/pie.desc
sane-backends-1.0.17/doc/descriptions/pint.desc
sane-backends-1.0.17/doc/descriptions/plustek.desc
sane-backends-1.0.17/doc/descriptions/plustek_pp.desc
sane-backends-1.0.17/doc/descriptions/pnm.desc
sane-backends-1.0.17/doc/descriptions/qcam.desc
sane-backends-1.0.17/doc/descriptions/ricoh.desc
sane-backends-1.0.17/doc/descriptions/s9036.desc
sane-backends-1.0.17/doc/descriptions/sceptre.desc
sane-backends-1.0.17/doc/descriptions/sharp.desc
sane-backends-1.0.17/doc/descriptions/sm3600.desc
sane-backends-1.0.17/doc/descriptions/sm3840.desc
sane-backends-1.0.17/doc/descriptions/snapscan.desc
sane-backends-1.0.17/doc/descriptions/sp15c.desc
sane-backends-1.0.17/doc/descriptions/st400.desc
sane-backends-1.0.17/doc/descriptions/tamarack.desc
sane-backends-1.0.17/doc/descriptions/teco1.desc
sane-backends-1.0.17/doc/descriptions/teco2.desc
sane-backends-1.0.17/doc/descriptions/teco3.desc
sane-backends-1.0.17/doc/descriptions/template.desc.
sane-backends-1.0.17/doc/descriptions/test.desc
sane-backends-1.0.17/doc/descriptions/u12.desc
sane-backends-1.0.17/doc/descriptions/umax1220u.desc
sane-backends-1.0.17/doc/descriptions/umax.desc
sane-backends-1.0.17/doc/descriptions/umax_pp.desc
sane-backends-1.0.17/doc/descriptions/unsupported.desc
sane-backends-1.0.17/doc/descriptions/v4l.desc
sane-backends-1.0.17/doc/descriptions-external/
sane-backends-1.0.17/doc/descriptions-external/brother2.desc
sane-backends-1.0.17/doc/descriptions-external/brother.desc
sane-backends-1.0.17/doc/descriptions-external/brother-mfc4600.desc
sane-backends-1.0.17/doc/descriptions-external/epkowa.desc
sane-backends-1.0.17/doc/descriptions-external/geniusvp2.desc
sane-backends-1.0.17/doc/descriptions-external/hp3500.desc
sane-backends-1.0.17/doc/descriptions-external/hp3770.desc
sane-backends-1.0.17/doc/descriptions-external/hp8200.desc
sane-backends-1.0.17/doc/descriptions-external/hpaio.desc
sane-backends-1.0.17/doc/descriptions-external/hpoj.desc
sane-backends-1.0.17/doc/descriptions-external/hp_rts88xx.desc
sane-backends-1.0.17/doc/descriptions-external/lhii.desc
sane-backends-1.0.17/doc/descriptions-external/mustek_a3p1.desc
sane-backends-1.0.17/doc/descriptions-external/primascan.desc
sane-backends-1.0.17/doc/descriptions-external/primax.desc
sane-backends-1.0.17/doc/descriptions-external/samsung.desc
sane-backends-1.0.17/doc/descriptions-external/scanwit.desc
sane-backends-1.0.17/doc/descriptions-external/stv680.desc
sane-backends-1.0.17/doc/descriptions-external/template.desc.
sane-backends-1.0.17/doc/descriptions-external/v4l2.desc
sane-backends-1.0.17/doc/descriptions-external/viceo.desc
sane-backends-1.0.17/doc/Makefile.in
sane-backends-1.0.17/doc/backend-writing.txt
sane-backends-1.0.17/doc/descriptions.txt
sane-backends-1.0.17/doc/doxygen-sanei.conf.in
sane-backends-1.0.17/doc/html.sty
sane-backends-1.0.17/doc/net.tex
sane-backends-1.0.17/doc/releases.txt
sane-backends-1.0.17/doc/sane-abaton.man
sane-backends-1.0.17/doc/sane-agfafocus.man
sane-backends-1.0.17/doc/sane-apple.man
sane-backends-1.0.17/doc/sane-artec.man
sane-backends-1.0.17/doc/sane-as6e.man
sane-backends-1.0.17/doc/sane-avision.man
sane-backends-1.0.17/doc/sane-bh.man
sane-backends-1.0.17/doc/sane-canon.man
sane-backends-1.0.17/doc/sane-canon630u.man
sane-backends-1.0.17/doc/sane-config.man
sane-backends-1.0.17/doc/sane-coolscan.man
sane-backends-1.0.17/doc/sane-coolscan2.man
sane-backends-1.0.17/doc/sane-dc210.man
sane-backends-1.0.17/doc/sane-dc240.man
sane-backends-1.0.17/doc/sane-dc25.man
sane-backends-1.0.17/doc/sane-dll.man
sane-backends-1.0.17/doc/sane-dmc.man
sane-backends-1.0.17/doc/sane-epson.man
sane-backends-1.0.17/doc/sane-find-scanner.man
sane-backends-1.0.17/doc/sane-fujitsu.man
sane-backends-1.0.17/doc/sane-gphoto2.man
sane-backends-1.0.17/doc/sane-hp.man
sane-backends-1.0.17/doc/sane-logo.png
sane-backends-1.0.17/doc/sane-logo2.jpg
sane-backends-1.0.17/doc/sane-matsushita.man
sane-backends-1.0.17/doc/sane-microtek.man
sane-backends-1.0.17/doc/sane-leo.man
sane-backends-1.0.17/doc/sane-lexmark.man
sane-backends-1.0.17/doc/sane-microtek2.man
sane-backends-1.0.17/doc/sane-mustek.man
sane-backends-1.0.17/doc/sane-mustek_pp.man
sane-backends-1.0.17/doc/sane-mustek_usb.man
sane-backends-1.0.17/doc/sane-nec.man
sane-backends-1.0.17/doc/sane-net.man
sane-backends-1.0.17/doc/sane-pie.man
sane-backends-1.0.17/doc/sane-pint.man
sane-backends-1.0.17/doc/sane-plustek.man
sane-backends-1.0.17/doc/sane-pnm.man
sane-backends-1.0.17/doc/sane-qcam.man
sane-backends-1.0.17/doc/sane-ricoh.man
sane-backends-1.0.17/doc/sane-s9036.man
sane-backends-1.0.17/doc/sane-scsi.man
sane-backends-1.0.17/doc/sane-sharp.man
sane-backends-1.0.17/doc/sane-sm3600.man
sane-backends-1.0.17/doc/sane-snapscan.man
sane-backends-1.0.17/doc/sane-st400.man
sane-backends-1.0.17/doc/sane-tamarack.man
sane-backends-1.0.17/doc/sane-umax.man
sane-backends-1.0.17/doc/sane-umax1220u.man
sane-backends-1.0.17/doc/sane-umax_pp.man
sane-backends-1.0.17/doc/sane-usb.man
sane-backends-1.0.17/doc/sane-v4l.man
sane-backends-1.0.17/doc/sane.man
sane-backends-1.0.17/doc/sane.png
sane-backends-1.0.17/doc/sane.tex
sane-backends-1.0.17/doc/saned.man
sane-backends-1.0.17/doc/scanimage.man
sane-backends-1.0.17/doc/sane-sceptre.man
sane-backends-1.0.17/doc/sane-canon_pp.man
sane-backends-1.0.17/doc/sane-teco1.man
sane-backends-1.0.17/doc/sane-teco2.man
sane-backends-1.0.17/doc/sane-teco3.man
sane-backends-1.0.17/doc/sane-test.man
sane-backends-1.0.17/doc/sane-sp15c.man
sane-backends-1.0.17/doc/sane-hpsj5s.man
sane-backends-1.0.17/doc/gamma4scanimage.man
sane-backends-1.0.17/doc/sane-gt68xx.man
sane-backends-1.0.17/doc/sane-artec_eplus48u.man
sane-backends-1.0.17/doc/sane-ma1509.man
sane-backends-1.0.17/doc/sane-ibm.man
sane-backends-1.0.17/doc/sane-hp5400.man
sane-backends-1.0.17/doc/sane-plustek_pp.man
sane-backends-1.0.17/doc/sane-u12.man
sane-backends-1.0.17/doc/sane-niash.man
sane-backends-1.0.17/doc/sane-sm3840.man
sane-backends-1.0.17/doc/sane-genesys.man
sane-backends-1.0.17/doc/sane-hp4200.man
sane-backends-1.0.17/doc/sane-mustek_usb2.man
sane-backends-1.0.17/po/
sane-backends-1.0.17/po/Makefile.in
sane-backends-1.0.17/po/README
sane-backends-1.0.17/po/template.po
sane-backends-1.0.17/po/sane-backends.bg.po
sane-backends-1.0.17/po/sane-backends.cs.po
sane-backends-1.0.17/po/sane-backends.da.po
sane-backends-1.0.17/po/sane-backends.de.po
sane-backends-1.0.17/po/sane-backends.es.po
sane-backends-1.0.17/po/sane-backends.fi.po
sane-backends-1.0.17/po/sane-backends.fr.po
sane-backends-1.0.17/po/sane-backends.it.po
sane-backends-1.0.17/po/sane-backends.nl.po
sane-backends-1.0.17/po/sane-backends.no.po
sane-backends-1.0.17/po/sane-backends.pl.po
sane-backends-1.0.17/po/sane-backends.pt.po
sane-backends-1.0.17/po/sane-backends.ru.po
sane-backends-1.0.17/po/sane-backends.sv.po
sane-backends-1.0.17/japi/
sane-backends-1.0.17/japi/ImageCanvas.java
sane-backends-1.0.17/japi/ImageCanvasClient.java
sane-backends-1.0.17/japi/Jscanimage.java
sane-backends-1.0.17/japi/Makefile.in
sane-backends-1.0.17/japi/README.JAVA
sane-backends-1.0.17/japi/Sane.c
sane-backends-1.0.17/japi/Sane.java
sane-backends-1.0.17/japi/SaneDevice.java
sane-backends-1.0.17/japi/SaneOption.java
sane-backends-1.0.17/japi/SaneParameters.java
sane-backends-1.0.17/japi/SaneRange.java
sane-backends-1.0.17/japi/ScanIt.java
sane-backends-1.0.17/japi/Test.java
sane-backends-1.0.17/testsuite/
sane-backends-1.0.17/testsuite/Makefile.in
sane-backends-1.0.17/testsuite/README
sane-backends-1.0.17/testsuite/testfile.pnm
clive@ubuntu:~$ cd  sane-backends-1.0.17
clive@ubuntu:~/sane-backends-1.0.17$ sudo cp -r backend /usr/share
clive@ubuntu:~/sane-backends-1.0.17$ cd /usr/share/doc/libsane/plustek
clive@ubuntu:/usr/share/doc/libsane/plustek$ sudo ./MakeModule.sh
This script will try and build a suitable kernel-module for your system.
If you'd like to make the module WITH debug output, restart this script
with as follows:
./MakeModule.sh DEBUG=y
Press <ENTER> to continue or <CTRL><C> to cancel.

Check for root - done.

Check for kernelversion:
Using makefile for kernel 2.6.x
Build-directory:
/usr/share/doc/libsane/plustek/build
Removing build-directory - done.
Creating build-directory - done.

Linking source files...ls: /usr/share/doc/libsane/plustek/../../backend/plustek-pp_*.c: No such file or directory
ls: /usr/share/doc/libsane/plustek/../../backend/plustek-pp_*.h: No such file or directory
 - done.
Copying Makefile to build-directory - done.
Making the module...
make: *** /lib/modules/2.6.12-10-686/build/: No such file or directory.  Stop.
There were some build errors..
clive@ubuntu:/usr/share/doc/libsane/plustek$

In the dir /usr/share/doc/libsane/plustek there is a folder "build" in there is makefile and 2 plustek-pp_* are there? both are file owner root if that helps.

---

### Post by Pragmatist on 2006-03-14
Wow! we're really fumbling through this together :)  Ok, more wrong advice from me, sorry :cry:

```
 cd  sane-backends-1.0.17 
``` ```
./configure
``` ```
make
``` ```
sudo make install
``` 
When it is done, try scanimage again:
```
scanimage -L
```

NOTE: These steps take time, especially the second command "make".  Don't worry about "warnings"  If there are "errors" paste them here if possible.

---

### Post by CameronCalver on 2006-03-14
i have a cannon fd330p does anyone no if they can work on linux ubuntu

---

### Post by evilc on 2006-03-14
[QUOTE=Pragmatist]Wow! we're really fumbling through this together :)  Ok, more wrong advice from me, sorry :cry:

```
 cd  sane-backends-1.0.17 
``` ```
./configure
``` ```
make
``` ```
sudo make install
``` 
When it is done, try scanimage again:
```
scanimage -L
```

NOTE: These steps take time, especially the second command "make".  Don't worry about "warnings"  If there are "errors" paste them here if possible.[/QUOTE]

Did not get past ./configure.......

clive@ubuntu:~$ cd  sane-backends-1.0.17
clive@ubuntu:~/sane-backends-1.0.17$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
clive@ubuntu:~/sane-backends-1.0.17$



EDIT

Installed some updates and got it to run this was the last bit I think this was the only errors?
Tried scanimage -L still not there.

installing sane.ps in /usr/local/doc/sane-1.0.17/sane.ps...
/usr/bin/install: cannot stat `sane.ps': No such file or directory
installing sane.dvi in /usr/local/doc/sane-1.0.17/sane.dvi...
/usr/bin/install: cannot stat `sane.dvi': No such file or directory
installing sane-backends.html in /usr/local/doc/sane-1.0.17/sane-backends.html...
installing sane-backends-external.html in /usr/local/doc/sane-1.0.17/sane-backends-external.html...
installing sane-mfgs.html in /usr/local/doc/sane-1.0.17/sane-mfgs.html...
installing sane-mfgs-external.html in /usr/local/doc/sane-1.0.17/sane-mfgs-external.html...
make[1]: Leaving directory `/home/clive/sane-backends-1.0.17/doc'
making install in po
make[1]: Entering directory `/home/clive/sane-backends-1.0.17/po'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/clive/sane-backends-1.0.17/po'
clive@ubuntu:~/sane-backends-1.0.17

---

### Post by Sef on 2006-03-14
> i have a cannon fd330p does anyone no if they can work on linux ubuntu

Please start a new thread for your question, and it will get answered.

---

### Post by Pragmatist on 2006-03-14
Please give us the output of this:
First update your locate database so you can use the locate command (this will take a couple of minutes so just wait till it finishes):
```
sudo updatedb
``` Now try this and give us the output:
```
locate gcc | grep bin
``` ```
echo $PATH
``` 
What do you mean when you say that you: 
> Installed some updates Which ones and for what?  Please be specific.
Note: Now, I am doing on my system what I'm recommending you do on yours (except I don't have a scanner) :) So, for comparison, my system got MUCH further on the configure. This is good news, as it just means we have to configure your system--which will probably help you with other things too.

---

### Post by evilc on 2006-03-14
[QUOTE=Pragmatist]Please give us the output of this:
First update your locate database so you can use the locate command (this will take a couple of minutes so just wait till it finishes):
```
sudo updatedb
``` Now try this and give us the output:
```
locate gcc | grep bin
``` ```
echo $PATH
``` 
What do you mean when you say that you: 
 Which ones and for what?  Please be specific.
Note: Now, I am doing on my system what I'm recommending you do on yours (except I don't have a scanner) :) So, for comparison, my system got MUCH further on the configure. This is good news, as it just means we have to configure your system--which will probably help you with other things too.[/QUOTE]

1/
clive@ubuntu:~$ sudo updatedb
Password:
clive@ubuntu:~$ 

2/
clive@ubuntu:~$ locate gcc | grep bin
/usr/bin/gcc-4.0
/usr/bin/i486-linux-gnu-gcc
/usr/bin/gccbug-4.0
/usr/bin/i486-linux-gnu-gcc-4.0
/usr/bin/gccbug
/usr/bin/gcc
clive@ubuntu:~$ 

3/

clive@ubuntu:~$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
clive@ubuntu:~$

The updates were from the red icon notification by clock. No idea what ones as I don't know the packages total of 73 went in, I think it's synaptic package manager?

The edit bit was the outcome of sudo make install I re-run your command after the updates and got through it all.

---

### Post by Pragmatist on 2006-03-14
So you were able to get though the compile (make)?
And did you run ```
sudo make install
```
If you did all of that, what do you get after a reboot and:
```
scanimage -L
```

---

### Post by evilc on 2006-03-14
[QUOTE=Pragmatist]So you were able to get though the compile (make)?
And did you run ```
sudo make install
```
If you did all of that, what do you get after a reboot and:
```
scanimage -L
```[/QUOTE]

Still the same,

clive@ubuntu:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
clive@ubuntu:~$

---

### Post by evilc on 2006-03-15
I have been thinking, if the program is installed could it be the printer port not being seen by Ubuntu, how can I check to see if the port is reconised and if permission to access it is right?

Would the error's that I shown in previous post (under EDIT) have anything to do with it?

---

### Post by Pragmatist on 2006-03-15
Sorry about that, I took a break for awhile.  I'm looking at the various README files from that package we both downloaded.  Please give me the output of these:
```
cat /etc/modules.conf | grep scanner
```
```
locate parport
```

---

### Post by Pragmatist on 2006-03-15
Make sure you run ```
sudo updatedb
``` one time, before running any of the locate commands I gave you
And this:
```
locate libieee
```

---

### Post by evilc on 2006-03-15
No problems you need a break trying to solve this.
Here is the full output:

clive@ubuntu:~$ sudo updatedb
Password:
clive@ubuntu:~$ locate libieee
/var/lib/dpkg/info/libieee1284-3.shlibs
/var/lib/dpkg/info/libieee1284-3.list
/var/lib/dpkg/info/libieee1284-3.postinst
/var/lib/dpkg/info/libieee1284-3.postrm
/var/lib/dpkg/info/libieee1284-3.md5sums
/usr/share/doc/libieee1284-3
/usr/share/doc/libieee1284-3/copyright
/usr/share/doc/libieee1284-3/README
/usr/share/doc/libieee1284-3/TODO
/usr/share/doc/libieee1284-3/changelog.Debian.gz
/usr/share/doc/libieee1284-3/changelog.gz
/usr/lib/libieee1284.so.3.2.2
/usr/lib/libieee1284.so.3
/usr/lib/libieee.a

clive@ubuntu:~$ cat /etc/modules.conf | grep scanner
cat: /etc/modules.conf: No such file or directory

clive@ubuntu:~$ locate parport
/etc/pcmcia/parport.opts
/etc/pcmcia/parport
/lib/modules/2.6.12-10-686/kernel/drivers/i2c/busses/i2c-parport-light.ko
/lib/modules/2.6.12-10-686/kernel/drivers/i2c/busses/i2c-parport.ko
/lib/modules/2.6.12-10-686/kernel/drivers/parport
/lib/modules/2.6.12-10-686/kernel/drivers/parport/parport_cs.ko
/lib/modules/2.6.12-10-686/kernel/drivers/parport/parport.ko
/lib/modules/2.6.12-10-686/kernel/drivers/parport/parport_serial.ko
/lib/modules/2.6.12-10-686/kernel/drivers/parport/parport_pc.ko
/usr/share/doc/libsane/umax/sane-umax-parport-doc.html
/usr/include/linux/parport.h
/usr/include/linux/parport_pc.h
/usr/include/asm/parport.h
/usr/include/asm-i386/parport.h
/usr/include/asm-x86_64/parport.h
/usr/local/doc/sane-1.0.17/umax/sane-umax-parport-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-parport-doc.html
clive@ubuntu:~$

---

### Post by Pragmatist on 2006-03-15
Ok, you don't have an /etc/modules.conf file.  I searched the forum and found a few others that didn't have it and I don't think it is cause for alarm as the information can be in alternate places. so...more info :)
```
ls -l /etc/mod*
```
```
lspci
```
```
lsmod
```

---

### Post by evilc on 2006-03-15
Here you are: I had to put in an old sound card, on-board sounds stopped working no idea why but not worried.

clive@ubuntu:~$ ls -l /etc/mod*
-rw-r--r--  1 root root  466 2006-03-15 10:32 /etc/modules
-rw-r--r--  1 root root  215 2006-03-14 16:51 /etc/modules~
-rw-r--r--  1 root root  357 2006-03-15 08:34 /etc/modules_backup_200603150834

/etc/modprobe.d:
total 48
-rw-r--r--  1 root root  4405 2005-09-20 11:09 aliases
-rw-r--r--  1 root root 12305 2005-09-30 00:12 alsa-base
drwxr-xr-x  2 root root  4096 2006-03-14 16:47 arch
lrwxrwxrwx  1 root root     9 2006-03-14 16:47 arch-aliases -> arch/i386
-rw-r--r--  1 root root   484 2005-10-03 19:12 bluez
-rw-r--r--  1 root root    38 2005-10-12 22:42 ibm_acpi.modprobe
-rw-r--r--  1 root root   399 2005-10-05 02:39 isapnp
-rw-r--r--  1 root root    29 2005-07-27 01:23 nvidia-kernel-nkc
-rw-r--r--  1 root root    41 2005-10-12 22:42 toshiba_acpi.modprobe

/etc/modutils:
total 32
-rw-r--r--  1 root root 8646 2005-09-30 00:12 alsa-base
-rw-r--r--  1 root root   97 2005-04-15 18:41 apm
-rw-r--r--  1 root root  233 2005-10-03 19:12 bluez
-rw-r--r--  1 root root   29 2005-07-22 12:19 evms
-rw-r--r--  1 root root  121 2000-12-27 08:58 lvm-common
-rw-r--r--  1 root root   28 2005-07-27 01:23 nvidia-kernel-nkc
clive@ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0258
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1258
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2258
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3258
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4258
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7258
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0c.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
clive@ubuntu:~$ lsmod
Module                  Size  Used by
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4316  0
cpufreq_stats           5252  0
freq_table              4388  1 cpufreq_stats
cpufreq_powersave       1696  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
radeon                 78080  1
drm                    64884  2 radeon
video                  15748  0
tc1100_wmi              6692  0
sony_acpi               5324  0
pcc_acpi               11104  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
ipv6                  251232  6
af_packet              21768  2
floppy                 59124  0
pcspkr                  3396  0
rtc                    12344  0
usblp                  12640  0
i2c_viapro              7920  0
i2c_core               21200  2 i2c_acpi_ec,i2c_viapro
snd_cs46xx             86088  0
gameport               14824  2 snd_cs46xx
snd_ac97_codec         83932  1 snd_cs46xx
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10600  2 snd_cs46xx,snd_pcm
shpchp                 96996  0
pci_hotplug            27508  1 shpchp
via_agp                 9632  1
agpgart                34792  2 drm,via_agp
dm_mod                 57692  1
snd_seq_dummy           3620  0
snd_seq_oss            33600  0
tsdev                   7776  0
snd_seq_midi            9088  0
snd_rawmidi            24704  2 snd_cs46xx,snd_seq_midi
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
snd_seq                50736  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24164  2 snd_pcm,snd_seq
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
evdev                   9664  0
snd                    54884  10 snd_cs46xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9600  1 snd
piix                   10372  0
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  1
lp                     12292  0
parport                35912  2 parport_pc,lp
md                     45584  0
ext3                  136264  2
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
via_rhine              22564  0
mii                     5696  1 via_rhine
ehci_hcd               34248  0
uhci_hcd               31184  0
usbcore               118044  4 usblp,ehci_hcd,uhci_hcd
ide_cd                 41572  0
cdrom                  39616  1 ide_cd
ide_disk               18464  5
ide_generic             1376  0
via82cxxx              13436  1
ide_core              138772  5 piix,ide_cd,ide_disk,ide_generic,via82cxxx
unix                   26896  574
vesafb                  7992  0
capability              4712  0
commoncap               6816  1 capability
vga16fb                12584  1
vgastate                9664  1 vga16fb
softcursor              2272  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3872  2 vesafb,vga16fb
cfbcopyarea             4608  2 vesafb,vga16fb
fbcon                  38496  72
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon
clive@ubuntu:~$

---

### Post by Pragmatist on 2006-03-15
Good.  Ok, now I need to see those modules files.  So please use **cat** to get the output and paste it here.  For **/etc/modules /etc/modules~ /etc/modules_backup_200603150834** 

/etc/modules and /etc/modules~ are probably the same file but the one with the ~ is a most recent version that didn't get saved.  Anyway, try all of them.

I see you have the various parport modules and you have the ieee libraries.  Things are shaping up well :)  

What is the output of:
```
lshal > output_lshal
```
This command will make a file called **output_lshal** then just attach the file to your next post.

---

### Post by evilc on 2006-03-16
the cat file.

clive@ubuntu:~$ cat /etc/modules /etc/modules~ /etc/modules_backup_200603150834
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse

alias char-major-40 pt_drv
pre-install pt_drv modprobe -k parport
options pt_drv lampoff=180 warmup=15 port=0x378 lOffonEnd=0 mov=0 slowIO=1
piix
ide-core
ide-cd
ide-disk
ide-generic
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse

alias char-major-40 pt_drv
pre-install pt_drv modprobe -k parport
options pt_drv lampoff=180 warmup=15 port=0x378 lOffonEnd=0 mov=0 slowIO=1

the lshal file
clive@ubuntu:~$ lshal > output_lshal
lshal version 0.5.3
clive@ubuntu:~$

---

### Post by Pragmatist on 2006-03-16
You need to attach that file called: output_lshal 

also let me see this:
```
cat /etc/modprobe.d/* | grep pt_drv
``` 
```
modprobe pt_drv
``` ```
modprobe -k parport
``` ```
lsmod
``` 
If you need root permissions, just preface the above commands with **sudo**

---

### Post by evilc on 2006-03-16
clive@ubuntu:~$ cat /etc/modprobe.d/* | grep pt_drv
cat: /etc/modprobe.d/arch: Is a directory
clive@ubuntu:~$

clive@ubuntu:~$ sudo modprobe pt_drv
FATAL: Module pt_drv not found.

clive@ubuntu:~$ sudo modprobe -k parport
clive@ubuntu:~$ lsmod
Module                  Size  Used by
isofs                  35960  1
udf                    90820  0
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4316  0
cpufreq_stats           5252  0
freq_table              4388  1 cpufreq_stats
cpufreq_powersave       1696  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
radeon                 78080  1
drm                    64884  2 radeon
video                  15748  0
tc1100_wmi              6692  0
sony_acpi               5324  0
pcc_acpi               11104  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
ipv6                  251232  6
af_packet              21768  2
floppy                 59124  0
pcspkr                  3396  0
rtc                    12344  0
usblp                  12640  0
i2c_viapro              7920  0
i2c_core               21200  2 i2c_acpi_ec,i2c_viapro
snd_cs46xx             86088  1
gameport               14824  2 snd_cs46xx
snd_ac97_codec         83932  1 snd_cs46xx
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10600  2 snd_cs46xx,snd_pcm
shpchp                 96996  0
pci_hotplug            27508  1 shpchp
via_agp                 9632  1
agpgart                34792  2 drm,via_agp
dm_mod                 57692  1
snd_seq_dummy           3620  0
snd_seq_oss            33600  0
snd_seq_midi            9088  0
snd_rawmidi            24704  2 snd_cs46xx,snd_seq_midi
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
snd_seq                50736  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24164  2 snd_pcm,snd_seq
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tsdev                   7776  0
evdev                   9664  0
snd                    54884  12 snd_cs46xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9600  1 snd
piix                   10372  0
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  1
lp                     12292  0
parport                35912  2 parport_pc,lp
md                     45584  0
ext3                  136264  2
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
via_rhine              22564  0
mii                     5696  1 via_rhine
ehci_hcd               34248  0
uhci_hcd               31184  0
usbcore               118044  4 usblp,ehci_hcd,uhci_hcd
ide_cd                 41572  1
cdrom                  39616  1 ide_cd
ide_disk               18464  5
ide_generic             1376  0
via82cxxx              13436  1
ide_core              138772  5 piix,ide_cd,ide_disk,ide_generic,via82cxxx
unix                   26896  626
vesafb                  7992  0
capability              4712  0
commoncap               6816  1 capability
vga16fb                12584  1
vgastate                9664  1 vga16fb
softcursor              2272  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3872  2 vesafb,vga16fb
cfbcopyarea             4608  2 vesafb,vga16fb
fbcon                  38496  72
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon
clive@ubuntu:~$

---

### Post by Pragmatist on 2006-03-16
We need still more info:
```
cat /etc/sane.d/plustek_pp.conf
```
```
cat /etc/sane.d/dll.conf
```

Good news so far:
1.) Your computer recognizes your parallel port
2.) The installations you did led to entries in your /etc/modules files that show it expects a kernel module named pt_drv  The confusion has to do with a combination of changes in how the plustek backend/driver situation has worked over time and unclear documentation.  As I understand it, previously you had an option to use the backend or use the backend to create a kernel driver (pt_drv).  To confuse things further, in the past (2.4 kernel and before--i.e. before early 2004)this process involved compiling SANE from source code which could be a pain.The first thing I had you do was to create a kernel module.  Then I found out that this is no longer necessary.  However, much of the documentation is from before 2004!  So this is confusing.  The web has some newer information, but the plustek site will have some information from 2005 but leave its howtos from 2003!!  A real mess.

The light at the end of the tunnel:
Worse comes to worse this is what we do--uninstall everything we did and any scanner packages you had from before we started.  In other words we start from scratch.  If it was just me, I would have done that a couple of days ago, because it is actually the easiest, cleanest, and fastest approach.

Bottom line: I'm certain that you can get this scanner working with the following caveats:
1.) your scanner isn't some weird, after market, OEM, chipset variation of the 9630p.  From what I've read, the only way to tell is by opening the scanner and reading the writing on the chips to determine the chipset. I'm assuming yours isn't one of these weird ones, but if it was me, I'd check.

2.) There isn't something really strange about your computer that would negate this.  This is much more unlikely than number 1 that I'm not at all concerned about it.

Of course, as I'm sure you can already see, this is time-consuming when I am here and you need to send me information and endure my experiments.  Anyway, I'm still game if you are.

---

### Post by evilc on 2006-03-16
clive@ubuntu:~$ cat /etc/sane.d/plustek_pp.conf
# Plustek-PP SANE Backend configuration file
# For use with Plustek parallel-port scanners
#

#
# user either [direct] or [kernel] to access the scanner
# when using [kernel], device specifies the device-node, which is created
# by the kernel-module loader (applies only to Linux)
# when using [direct], device is used to set the parallel-port base address
# or a device-name suitable for libieee1284, i.e. parport0
#
[direct]
device 0x378

#
# leave the default values as specified in /etc/modules.conf
#
option warmup    -1
option lOffOnEnd -1
option lampOff   -1

# model override switch, mostly for cosmetic changes, if the autodetection
# does not work or could not work correctly
#option mov 7

#
# example for accessing the scanner via libieee1284
#
[direct]
device parport0

#
# example for accessing the scanner via the kernel module
#
#[kernel]
#device /dev/pt_drv
#
#option warmup    -1
#option lOffOnEnd -1
#option lampOff   -1
clive@ubuntu:~$ cat /etc/sane.d/dll.conf
# /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader
#
# On Debian systems, the dll backend will also look for pieces of configuration
# in the /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory.
#

# enable the next line if you want to allow access through the network:
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
#canon_pp
coolscan
coolscan2
#dc25
#dc210
#dc240
dmc
epson
fujitsu
#gphoto2
gt68xx
hp
hpsj5s
hp5400
ibm
leo
ma1509
matsushita
microtek
microtek2
mustek
#mustek_pp
mustek_usb
nec
niash
pie
plustek
#plustek_pp
#pnm
qcam
ricoh
s9036
sceptre
sharp
sm3600
snapscan
sp15c
#st400
tamarack
teco1
teco2
teco3
#test
u12
umax
#umax_pp
umax1220u
v4l

# The HP OfficeJet backend is not part of the SANE distribution
# but is provided by the hpoj Debian package
hpoj

# The hpaio backend (hplip package) supports HP multifunction
# devices. It is intended as a replacement for hpoj, choose
# whichever works best for you
hpaio
clive@ubuntu:~$

Glad one of us knows what we are doing:D  I can see where you are coming from would have no chance on my own. Will copy all these posts when finished and try to work it all out (good learning experience)

---

### Post by Ramses on 2006-03-16
I have plustek optic pro 12000 scanner connected to parallel port. All I had to do to get it work was to edit /etc/sane.d/plustek_pp.conf: ```
#plustek_pp
``` to ```
plustek_pp
```

There is still some permission issue in Breezy, because scanner only works with sudo. In Hoary scanner worked without sudo. So test with ```
sudo scanimage -L
```

---

### Post by Pragmatist on 2006-03-16
Definitely try that.  If it doesn't work, I read somewhere that you can comment out (preface the line with a **# **) all of backends EXCEPT **plustek_pp**  The backend entries start here:
>  # enable the next line if you want to allow access through the network:
** net**
and end here:
>  **v4l**
 
 # The HP OfficeJet backend is not part of the SANE distribution

---

### Post by evilc on 2006-03-16
Tried what you suggested (Pragmatist) no difference, with Ramses suggestion there is no reference to #plustek_pp (see my last post).

One thing I noticed the lpt port in device manager to me seems strange (only worked with dos/windows 30 years no linux) in bios lpt port address  is 378 in the device manager ?? see attached file.

---

### Post by Pragmatist on 2006-03-16
Lets see this:
```
cat /proc/ioports
```

---

### Post by evilc on 2006-03-16
378 shows as parport0


clive@ubuntu:~$ cat /proc/ioports
0000-001f : dma1
0020-0021 : pic1
0040-0043 : timer0
0050-0053 : timer1
0060-006f : keyboard
0070-0077 : rtc
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
00f0-00ff : fpu
0170-0177 : ide1
01f0-01f7 : ide0
0376-0376 : ide1
0378-037a : parport0
037b-037f : parport0
03c0-03df : vga+
03f6-03f6 : ide0
03f8-03ff : serial
0400-0407 : viapro-smbus
0800-0803 : PM1a_EVT_BLK
0804-0805 : PM1a_CNT_BLK
0808-080b : PM_TMR
0820-0823 : GPE0_BLK
0cf8-0cff : PCI conf1
c000-cfff : PCI Bus #01
  c800-c8ff : 0000:01:00.0
dc00-dcff : 0000:00:12.0
  dc00-dcff : via-rhine
e000-e01f : 0000:00:10.0
  e000-e01f : uhci_hcd
e400-e41f : 0000:00:10.1
  e400-e41f : uhci_hcd
e800-e81f : 0000:00:10.2
  e800-e81f : uhci_hcd
ec00-ec1f : 0000:00:10.3
  ec00-ec1f : uhci_hcd
fc00-fc0f : 0000:00:0f.0
  fc00-fc07 : ide0
  fc08-fc0f : ide1
clive@ubuntu:~$

---

### Post by Pragmatist on 2006-03-16
Nothing wrong with the port itself. Linux recognizes its location at 0x378:
** 0378**-037a : parport0

Try commenting out every backend but **plustek_pp** in both of these files:
/etc/sane.d/dll.conf
/etc/sane.d/plustek_pp.conf

Then reboot.  Then run **scanimage -L**

---

### Post by evilc on 2006-03-16
Still the same :cry: 

clive@ubuntu:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
clive@ubuntu:~$

---

### Post by Pragmatist on 2006-03-16
Hang in there :)  Ok, now lets work some more on the **/etc/sane.d/plustek_pp.conf** file
I'd like you to comment out everything but the lines I've put in **bold**:
# Plustek-PP SANE Backend configuration file
# For use with Plustek parallel-port scanners
#

#
# user either [direct] or [kernel] to access the scanner
# when using [kernel], device specifies the device-node, which is created
# by the kernel-module loader (applies only to Linux)
# when using [direct], device is used to set the parallel-port base address
# or a device-name suitable for libieee1284, i.e. parport0
#
[B][direct]
device 0x378[/B]

#
# leave the default values as specified in /etc/modules.conf
#
[B]option warmup    -1
option lOffOnEnd -1
option lampOff   -1[/B]

---

### Post by evilc on 2006-03-17
Same as previous message

---

### Post by Pragmatist on 2006-03-17
We've got more tools!  Download and run this.  It will give you a brief break from the command line:
[http://www.meier-geinitz.de/sane/sts/](http://www.meier-geinitz.de/sane/sts/)

---

### Post by Ramses on 2006-03-17
Try running scanimage with sudo if you didn't previously.

---

### Post by evilc on 2006-03-17
Run the file it says I have 2 sane locations also not the latest version I suggest we uninstall sane and reinstall with latest version. The last part gave this:

"The backend "plustek_pp" is not listed in /usr/local/etc/sane.d/dll.conf. Maybe it is commented out? Please edit this file (as root) and add plustek_pp to it. Or, if it's already there, remove the comment sign (#). After that, restart me."

In this folder there are 55 files in /etc/sane.d/ there are 59 files and 2 dir.

I think (going by dos) there may be conflict? I will wait your reply before removing sane. 
Also if I remove via Synaptic if any folders still remain somewhere can I just delete them.

---

### Post by evilc on 2006-03-17
Further to last message, seems sane looks at user/local/etc/sane.d & user/local directories I changed the plusteck_pp files in these dir and got further the last one shows this.

I was able to load the backend and call some of its functions, so your SANE installation seems to be ok. I think your scanner is connected through a Parport (SPP, EPP) interface, so I'll see if I can find out more about that interface when you go ahead.

I know the bios is set for EPP unfortunately the prog stops here :(

---

### Post by Pragmatist on 2006-03-17
> I'll see if I can find out more about that interface when you go ahead.
I think it may mean that you open a frontend like xsane and try to use access the scanner through it.  Just a guess, though.

You read my mind about removing the duplicate install.  I read somewhere about a nice use of the **find **command to look for the different sane files.  **locate **should be just as good.  I'm going to have you locate the sane files and create an attachment like you did for **lshal** a few posts before.
```
sudo updatedb
```
```
locate sane > output_file
```
Also, go into **synaptic** and look for all packages related to sane:
```
sudo synaptic
```
use search feature with keyword: **sane**  Then post the results here.

---

### Post by evilc on 2006-03-17
Nothing happened:  Have attached synaptic sane file, in 3 parts 0,1 &2

clive@ubuntu:~$ sudo updatedb
Password:
clive@ubuntu:~$ locate sane > output_file
clive@ubuntu:~$

---

### Post by Pragmatist on 2006-03-17
[SIZE=2]What happened with the **locate** command?

For the synaptic packages, I would "**completely remove**" these packages:
[B]libsane
sane-utils
xsane
xsane-common
python2.4-imaging-sane
[/B][/SIZE][SIZE=2][B]python-imaging-sane

[/B]You can always add them back, and we have a record here of what your removing.

Since you didn't do the locate command before, we might as well first remove the above packages, then run **sudo updatedb **and then run **locate sane**
[/SIZE]

---

### Post by evilc on 2006-03-17
All removed:  opp's forgot locate lshal remade after removing files and included.
Here is terminal locate sane.

/home/clive/sane-backends-1.0.17/tools/hotplug-ng/libsane.hotplug
/home/clive/sane-backends-1.0.17/tools/hotplug-ng/README
/home/clive/sane-backends-1.0.17/tools/udev
/home/clive/sane-backends-1.0.17/tools/udev/convert-usermap.sh
/home/clive/sane-backends-1.0.17/tools/Makefile.in
/home/clive/sane-backends-1.0.17/tools/RenSaneDlls.cmd
/home/clive/sane-backends-1.0.17/tools/README
/home/clive/sane-backends-1.0.17/tools/libtool-get-dll-ext
/home/clive/sane-backends-1.0.17/tools/mustek600iin-off.c
/home/clive/sane-backends-1.0.17/tools/sane-config.in
/home/clive/sane-backends-1.0.17/tools/sane-desc.c
/home/clive/sane-backends-1.0.17/tools/check-usb-chip.c
/home/clive/sane-backends-1.0.17/tools/sane-find-scanner.c
/home/clive/sane-backends-1.0.17/tools/umax_pp.c
/home/clive/sane-backends-1.0.17/tools/xerox
/home/clive/sane-backends-1.0.17/tools/gamma4scanimage.c
/home/clive/sane-backends-1.0.17/tools/check-po.awk
/home/clive/sane-backends-1.0.17/tools/Makefile
/home/clive/sane-backends-1.0.17/tools/sane-config
/home/clive/sane-backends-1.0.17/tools/Makefile.bak
/home/clive/sane-backends-1.0.17/tools/sane-find-scanner.o
/home/clive/sane-backends-1.0.17/tools/check-usb-chip.o
/home/clive/sane-backends-1.0.17/tools/.libs
/home/clive/sane-backends-1.0.17/tools/sane-find-scanner
/home/clive/sane-backends-1.0.17/tools/umax_pp.o
/home/clive/sane-backends-1.0.17/tools/umax_pp
/home/clive/sane-backends-1.0.17/tools/gamma4scanimage.o
/home/clive/sane-backends-1.0.17/tools/gamma4scanimage
/home/clive/sane-backends-1.0.17/tools/sane-desc.o
/home/clive/sane-backends-1.0.17/tools/sane-desc
/home/clive/sane-backends-1.0.17/doc
/home/clive/sane-backends-1.0.17/doc/canon
/home/clive/sane-backends-1.0.17/doc/canon/canon.changes
/home/clive/sane-backends-1.0.17/doc/canon/canon.install2700F.txt
/home/clive/sane-backends-1.0.17/doc/leo
/home/clive/sane-backends-1.0.17/doc/leo/leo.txt
/home/clive/sane-backends-1.0.17/doc/matsushita
/home/clive/sane-backends-1.0.17/doc/matsushita/matsushita.txt
/home/clive/sane-backends-1.0.17/doc/mustek
/home/clive/sane-backends-1.0.17/doc/mustek/mustek.CHANGES
/home/clive/sane-backends-1.0.17/doc/mustek_usb
/home/clive/sane-backends-1.0.17/doc/mustek_usb/mustek_usb.CHANGES
/home/clive/sane-backends-1.0.17/doc/mustek_usb/mustek_usb.TODO
/home/clive/sane-backends-1.0.17/doc/plustek
/home/clive/sane-backends-1.0.17/doc/plustek/FAQ
/home/clive/sane-backends-1.0.17/doc/plustek/Makefile.kernel24
/home/clive/sane-backends-1.0.17/doc/plustek/Makefile.kernel26
/home/clive/sane-backends-1.0.17/doc/plustek/MakeModule.sh
/home/clive/sane-backends-1.0.17/doc/plustek/Plustek-PARPORT.changes
/home/clive/sane-backends-1.0.17/doc/plustek/Plustek-PARPORT-TODO.txt
/home/clive/sane-backends-1.0.17/doc/plustek/Plustek-PARPORT.txt
/home/clive/sane-backends-1.0.17/doc/plustek/Plustek-USB.changes
/home/clive/sane-backends-1.0.17/doc/plustek/Plustek-USB-TODO.txt
/home/clive/sane-backends-1.0.17/doc/plustek/Plustek-USB.txt
/home/clive/sane-backends-1.0.17/doc/u12
/home/clive/sane-backends-1.0.17/doc/u12/U12.changes
/home/clive/sane-backends-1.0.17/doc/u12/U12.todo
/home/clive/sane-backends-1.0.17/doc/umax
/home/clive/sane-backends-1.0.17/doc/umax/negative-types.txt
/home/clive/sane-backends-1.0.17/doc/umax/sane-logo.jpg
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-advanced.jpg
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-advanced-options-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-astra-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-config-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-histogram.jpg
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax.jpg
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-mirage-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-not-listed-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-others-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-parport-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-powerlook-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-scanner-clones-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-speed-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-standard.jpg
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-standard-options-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-text2.jpg
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-text4.jpg
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-text.jpg
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-uc-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/sane-umax-vista-doc.html
/home/clive/sane-backends-1.0.17/doc/umax/umax.BUGS
/home/clive/sane-backends-1.0.17/doc/umax/umax.CHANGES
/home/clive/sane-backends-1.0.17/doc/umax/umax.FAQ
/home/clive/sane-backends-1.0.17/doc/umax/umax.TODO
/home/clive/sane-backends-1.0.17/doc/sceptre
/home/clive/sane-backends-1.0.17/doc/sceptre/s1200.txt
/home/clive/sane-backends-1.0.17/doc/teco
/home/clive/sane-backends-1.0.17/doc/teco/teco1.txt
/home/clive/sane-backends-1.0.17/doc/teco/teco2.txt
/home/clive/sane-backends-1.0.17/doc/teco/teco3.txt
/home/clive/sane-backends-1.0.17/doc/gt68xx
/home/clive/sane-backends-1.0.17/doc/gt68xx/gt68xx.CHANGES
/home/clive/sane-backends-1.0.17/doc/gt68xx/gt68xx.TODO
/home/clive/sane-backends-1.0.17/doc/niash
/home/clive/sane-backends-1.0.17/doc/niash/niash.TODO
/home/clive/sane-backends-1.0.17/doc/mustek_usb2
/home/clive/sane-backends-1.0.17/doc/mustek_usb2/mustek_usb2.CHANGES
/home/clive/sane-backends-1.0.17/doc/mustek_usb2/mustek_usb2.TODO
/home/clive/sane-backends-1.0.17/doc/icons
/home/clive/sane-backends-1.0.17/doc/icons/contents.gif
/home/clive/sane-backends-1.0.17/doc/icons/index.gif
/home/clive/sane-backends-1.0.17/doc/icons/next.gif
/home/clive/sane-backends-1.0.17/doc/icons/next_gr.gif
/home/clive/sane-backends-1.0.17/doc/icons/previous.gif
/home/clive/sane-backends-1.0.17/doc/icons/previous_gr.gif
/home/clive/sane-backends-1.0.17/doc/icons/references.gif
/home/clive/sane-backends-1.0.17/doc/icons/references_gr.gif
/home/clive/sane-backends-1.0.17/doc/icons/up.gif
/home/clive/sane-backends-1.0.17/doc/icons/up_gr.gif
/home/clive/sane-backends-1.0.17/doc/figs
/home/clive/sane-backends-1.0.17/doc/figs/area.eps
/home/clive/sane-backends-1.0.17/doc/figs/area.fig
/home/clive/sane-backends-1.0.17/doc/figs/flow.eps
/home/clive/sane-backends-1.0.17/doc/figs/flow.fig
/home/clive/sane-backends-1.0.17/doc/figs/hierarchy.eps
/home/clive/sane-backends-1.0.17/doc/figs/hierarchy.fig
/home/clive/sane-backends-1.0.17/doc/figs/image-data.eps
/home/clive/sane-backends-1.0.17/doc/figs/image-data.fig
/home/clive/sane-backends-1.0.17/doc/figs/xfer.eps
/home/clive/sane-backends-1.0.17/doc/figs/xfer.fig
/home/clive/sane-backends-1.0.17/doc/descriptions
/home/clive/sane-backends-1.0.17/doc/descriptions/abaton.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/agfafocus.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/apple.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/artec.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/artec_eplus48u.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/as6e.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/avision.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/bh.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/canon630u.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/canon.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/canon_pp.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/coolscan2.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/coolscan.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/dc210.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/dc240.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/dc25.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/dll.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/dmc.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/epson.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/fujitsu.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/genesys.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/gphoto2.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/gt68xx.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/hp4200.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/hp5400.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/hp.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/hpsj5s.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/ibm.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/leo.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/lexmark.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/ma1509.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/matsushita.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/microtek2.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/microtek.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/mustek.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/mustek_pp.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/mustek_usb2.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/mustek_usb.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/nec.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/net.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/niash.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/pie.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/pint.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/plustek.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/plustek_pp.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/pnm.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/qcam.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/ricoh.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/s9036.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/sceptre.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/sharp.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/sm3600.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/sm3840.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/snapscan.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/sp15c.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/st400.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/tamarack.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/teco1.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/teco2.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/teco3.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/template.desc.
/home/clive/sane-backends-1.0.17/doc/descriptions/test.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/u12.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/umax1220u.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/umax.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/umax_pp.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/unsupported.desc
/home/clive/sane-backends-1.0.17/doc/descriptions/v4l.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external
/home/clive/sane-backends-1.0.17/doc/descriptions-external/brother2.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/brother.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/brother-mfc4600.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/epkowa.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/geniusvp2.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/hp3500.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/hp3770.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/hp8200.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/hpaio.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/hpoj.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/hp_rts88xx.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/lhii.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/mustek_a3p1.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/primascan.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/primax.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/samsung.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/scanwit.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/stv680.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/template.desc.
/home/clive/sane-backends-1.0.17/doc/descriptions-external/v4l2.desc
/home/clive/sane-backends-1.0.17/doc/descriptions-external/viceo.desc
/home/clive/sane-backends-1.0.17/doc/Makefile.in
/home/clive/sane-backends-1.0.17/doc/backend-writing.txt
/home/clive/sane-backends-1.0.17/doc/descriptions.txt
/home/clive/sane-backends-1.0.17/doc/doxygen-sanei.conf.in
/home/clive/sane-backends-1.0.17/doc/html.sty
/home/clive/sane-backends-1.0.17/doc/net.tex
/home/clive/sane-backends-1.0.17/doc/releases.txt
/home/clive/sane-backends-1.0.17/doc/sane-abaton.man
/home/clive/sane-backends-1.0.17/doc/sane-agfafocus.man
/home/clive/sane-backends-1.0.17/doc/sane-apple.man
/home/clive/sane-backends-1.0.17/doc/sane-artec.man
/home/clive/sane-backends-1.0.17/doc/sane-as6e.man
/home/clive/sane-backends-1.0.17/doc/sane-avision.man
/home/clive/sane-backends-1.0.17/doc/sane-bh.man
/home/clive/sane-backends-1.0.17/doc/sane-canon.man
/home/clive/sane-backends-1.0.17/doc/sane-canon630u.man
/home/clive/sane-backends-1.0.17/doc/sane-config.man
/home/clive/sane-backends-1.0.17/doc/sane-coolscan.man
/home/clive/sane-backends-1.0.17/doc/sane-coolscan2.man
/home/clive/sane-backends-1.0.17/doc/sane-dc210.man
/home/clive/sane-backends-1.0.17/doc/sane-dc240.man
/home/clive/sane-backends-1.0.17/doc/sane-dc25.man
/home/clive/sane-backends-1.0.17/doc/sane-dll.man
/home/clive/sane-backends-1.0.17/doc/sane-dmc.man
/home/clive/sane-backends-1.0.17/doc/sane-epson.man
/home/clive/sane-backends-1.0.17/doc/sane-find-scanner.man
/home/clive/sane-backends-1.0.17/doc/sane-fujitsu.man
/home/clive/sane-backends-1.0.17/doc/sane-gphoto2.man
/home/clive/sane-backends-1.0.17/doc/sane-hp.man
/home/clive/sane-backends-1.0.17/doc/sane-logo.png
/home/clive/sane-backends-1.0.17/doc/sane-logo2.jpg
/home/clive/sane-backends-1.0.17/doc/sane-matsushita.man
/home/clive/sane-backends-1.0.17/doc/sane-microtek.man
/home/clive/sane-backends-1.0.17/doc/sane-leo.man
/home/clive/sane-backends-1.0.17/doc/sane-lexmark.man
/home/clive/sane-backends-1.0.17/doc/sane-microtek2.man
/home/clive/sane-backends-1.0.17/doc/sane-mustek.man
/home/clive/sane-backends-1.0.17/doc/sane-mustek_pp.man
/home/clive/sane-backends-1.0.17/doc/sane-mustek_usb.man
/home/clive/sane-backends-1.0.17/doc/sane-nec.man
/home/clive/sane-backends-1.0.17/doc/sane-net.man
/home/clive/sane-backends-1.0.17/doc/sane-pie.man
/home/clive/sane-backends-1.0.17/doc/sane-pint.man
/home/clive/sane-backends-1.0.17/doc/sane-plustek.man
/home/clive/sane-backends-1.0.17/doc/sane-pnm.man
/home/clive/sane-backends-1.0.17/doc/sane-qcam.man
/home/clive/sane-backends-1.0.17/doc/sane-ricoh.man
/home/clive/sane-backends-1.0.17/doc/sane-s9036.man
/home/clive/sane-backends-1.0.17/doc/sane-scsi.man
/home/clive/sane-backends-1.0.17/doc/sane-sharp.man
/home/clive/sane-backends-1.0.17/doc/sane-sm3600.man
/home/clive/sane-backends-1.0.17/doc/sane-snapscan.man
/home/clive/sane-backends-1.0.17/doc/sane-st400.man
/home/clive/sane-backends-1.0.17/doc/sane-tamarack.man
/home/clive/sane-backends-1.0.17/doc/sane-umax.man
/home/clive/sane-backends-1.0.17/doc/sane-umax1220u.man
/home/clive/sane-backends-1.0.17/doc/sane-umax_pp.man
/home/clive/sane-backends-1.0.17/doc/sane-usb.man
/home/clive/sane-backends-1.0.17/doc/sane-v4l.man
/home/clive/sane-backends-1.0.17/doc/sane.man
/home/clive/sane-backends-1.0.17/doc/sane.png
/home/clive/sane-backends-1.0.17/doc/sane.tex
/home/clive/sane-backends-1.0.17/doc/saned.man
/home/clive/sane-backends-1.0.17/doc/scanimage.man
/home/clive/sane-backends-1.0.17/doc/sane-sceptre.man
/home/clive/sane-backends-1.0.17/doc/sane-canon_pp.man
/home/clive/sane-backends-1.0.17/doc/sane-teco1.man
/home/clive/sane-backends-1.0.17/doc/sane-teco2.man
/home/clive/sane-backends-1.0.17/doc/sane-teco3.man
/home/clive/sane-backends-1.0.17/doc/sane-test.man
/home/clive/sane-backends-1.0.17/doc/sane-sp15c.man
/home/clive/sane-backends-1.0.17/doc/sane-hpsj5s.man
/home/clive/sane-backends-1.0.17/doc/gamma4scanimage.man
/home/clive/sane-backends-1.0.17/doc/sane-gt68xx.man
/home/clive/sane-backends-1.0.17/doc/sane-artec_eplus48u.man
/home/clive/sane-backends-1.0.17/doc/sane-ma1509.man
/home/clive/sane-backends-1.0.17/doc/sane-ibm.man
/home/clive/sane-backends-1.0.17/doc/sane-hp5400.man
/home/clive/sane-backends-1.0.17/doc/sane-plustek_pp.man
/home/clive/sane-backends-1.0.17/doc/sane-u12.man
/home/clive/sane-backends-1.0.17/doc/sane-niash.man
/home/clive/sane-backends-1.0.17/doc/sane-sm3840.man
/home/clive/sane-backends-1.0.17/doc/sane-genesys.man
/home/clive/sane-backends-1.0.17/doc/sane-hp4200.man
/home/clive/sane-backends-1.0.17/doc/sane-mustek_usb2.man
/home/clive/sane-backends-1.0.17/doc/Makefile
/home/clive/sane-backends-1.0.17/doc/doxygen-sanei.conf
/home/clive/sane-backends-1.0.17/doc/scanimage.1
/home/clive/sane-backends-1.0.17/doc/sane-config.1
/home/clive/sane-backends-1.0.17/doc/sane-find-scanner.1
/home/clive/sane-backends-1.0.17/doc/gamma4scanimage.1
/home/clive/sane-backends-1.0.17/doc/sane-abaton.5
/home/clive/sane-backends-1.0.17/doc/sane-agfafocus.5
/home/clive/sane-backends-1.0.17/doc/sane-apple.5
/home/clive/sane-backends-1.0.17/doc/sane-as6e.5
/home/clive/sane-backends-1.0.17/doc/sane-dll.5
/home/clive/sane-backends-1.0.17/doc/sane-dc25.5
/home/clive/sane-backends-1.0.17/doc/sane-dmc.5
/home/clive/sane-backends-1.0.17/doc/sane-epson.5
/home/clive/sane-backends-1.0.17/doc/sane-hp.5
/home/clive/sane-backends-1.0.17/doc/sane-gphoto2.5
/home/clive/sane-backends-1.0.17/doc/sane-leo.5
/home/clive/sane-backends-1.0.17/doc/sane-lexmark.5
/home/clive/sane-backends-1.0.17/doc/sane-matsushita.5
/home/clive/sane-backends-1.0.17/doc/sane-microtek.5
/home/clive/sane-backends-1.0.17/doc/sane-microtek2.5
/home/clive/sane-backends-1.0.17/doc/sane-mustek.5
/home/clive/sane-backends-1.0.17/doc/sane-nec.5
/home/clive/sane-backends-1.0.17/doc/sane-net.5
/home/clive/sane-backends-1.0.17/doc/sane-pie.5
/home/clive/sane-backends-1.0.17/doc/sane-pint.5
/home/clive/sane-backends-1.0.17/doc/sane-pnm.5
/home/clive/sane-backends-1.0.17/doc/sane-umax.5
/home/clive/sane-backends-1.0.17/doc/sane-qcam.5
/home/clive/sane-backends-1.0.17/doc/sane-scsi.5
/home/clive/sane-backends-1.0.17/doc/sane-artec.5
/home/clive/sane-backends-1.0.17/doc/sane-fujitsu.5
/home/clive/sane-backends-1.0.17/doc/sane-sharp.5
/home/clive/sane-backends-1.0.17/doc/sane-s9036.5
/home/clive/sane-backends-1.0.17/doc/sane-tamarack.5
/home/clive/sane-backends-1.0.17/doc/sane-ricoh.5
/home/clive/sane-backends-1.0.17/doc/sane-avision.5
/home/clive/sane-backends-1.0.17/doc/sane-plustek.5
/home/clive/sane-backends-1.0.17/doc/sane-st400.5
/home/clive/sane-backends-1.0.17/doc/sane-mustek_pp.5
/home/clive/sane-backends-1.0.17/doc/sane-dc210.5
/home/clive/sane-backends-1.0.17/doc/sane-v4l.5
/home/clive/sane-backends-1.0.17/doc/sane-snapscan.5
/home/clive/sane-backends-1.0.17/doc/sane-canon.5
/home/clive/sane-backends-1.0.17/doc/sane-coolscan.5
/home/clive/sane-backends-1.0.17/doc/sane-bh.5
/home/clive/sane-backends-1.0.17/doc/sane-dc240.5
/home/clive/sane-backends-1.0.17/doc/sane-umax_pp.5
/home/clive/sane-backends-1.0.17/doc/sane-umax1220u.5
/home/clive/sane-backends-1.0.17/doc/sane-sm3600.5
/home/clive/sane-backends-1.0.17/doc/sane-usb.5
/home/clive/sane-backends-1.0.17/doc/sane-mustek_usb.5
/home/clive/sane-backends-1.0.17/doc/sane-sceptre.5
/home/clive/sane-backends-1.0.17/doc/sane-canon_pp.5
/home/clive/sane-backends-1.0.17/doc/sane-canon630u.5
/home/clive/sane-backends-1.0.17/doc/sane-teco1.5
/home/clive/sane-backends-1.0.17/doc/sane-teco2.5
/home/clive/sane-backends-1.0.17/doc/sane-teco3.5
/home/clive/sane-backends-1.0.17/doc/sane-test.5
/home/clive/sane-backends-1.0.17/doc/sane-sp15c.5
/home/clive/sane-backends-1.0.17/doc/sane-coolscan2.5
/home/clive/sane-backends-1.0.17/doc/sane-hpsj5s.5
/home/clive/sane-backends-1.0.17/doc/sane-gt68xx.5
/home/clive/sane-backends-1.0.17/doc/sane-artec_eplus48u.5
/home/clive/sane-backends-1.0.17/doc/sane-ma1509.5
/home/clive/sane-backends-1.0.17/doc/sane-ibm.5
/home/clive/sane-backends-1.0.17/doc/sane-hp5400.5
/home/clive/sane-backends-1.0.17/doc/sane-plustek_pp.5
/home/clive/sane-backends-1.0.17/doc/sane-u12.5
/home/clive/sane-backends-1.0.17/doc/sane-niash.5
/home/clive/sane-backends-1.0.17/doc/sane-sm3840.5
/home/clive/sane-backends-1.0.17/doc/sane-genesys.5
/home/clive/sane-backends-1.0.17/doc/sane-hp4200.5
/home/clive/sane-backends-1.0.17/doc/sane-mustek_usb2.5
/home/clive/sane-backends-1.0.17/doc/sane.7
/home/clive/sane-backends-1.0.17/doc/saned.8
/home/clive/sane-backends-1.0.17/doc/sane-backends.html
/home/clive/sane-backends-1.0.17/doc/sane-backends-external.html
/home/clive/sane-backends-1.0.17/doc/sane-mfgs.html
/home/clive/sane-backends-1.0.17/doc/sane-mfgs-external.html
/home/clive/sane-backends-1.0.17/po
/home/clive/sane-backends-1.0.17/po/Makefile.in
/home/clive/sane-backends-1.0.17/po/README
/home/clive/sane-backends-1.0.17/po/template.po
/home/clive/sane-backends-1.0.17/po/sane-backends.bg.po
/home/clive/sane-backends-1.0.17/po/sane-backends.cs.po
/home/clive/sane-backends-1.0.17/po/sane-backends.da.po
/home/clive/sane-backends-1.0.17/po/sane-backends.de.po
/home/clive/sane-backends-1.0.17/po/sane-backends.es.po
/home/clive/sane-backends-1.0.17/po/sane-backends.fi.po
/home/clive/sane-backends-1.0.17/po/sane-backends.fr.po
/home/clive/sane-backends-1.0.17/po/sane-backends.it.po
/home/clive/sane-backends-1.0.17/po/sane-backends.nl.po
/home/clive/sane-backends-1.0.17/po/sane-backends.no.po
/home/clive/sane-backends-1.0.17/po/sane-backends.pl.po
/home/clive/sane-backends-1.0.17/po/sane-backends.pt.po
/home/clive/sane-backends-1.0.17/po/sane-backends.ru.po
/home/clive/sane-backends-1.0.17/po/sane-backends.sv.po
/home/clive/sane-backends-1.0.17/po/Makefile
/home/clive/sane-backends-1.0.17/japi
/home/clive/sane-backends-1.0.17/japi/ImageCanvas.java
/home/clive/sane-backends-1.0.17/japi/ImageCanvasClient.java
/home/clive/sane-backends-1.0.17/japi/Jscanimage.java
/home/clive/sane-backends-1.0.17/japi/Makefile.in
/home/clive/sane-backends-1.0.17/japi/README.JAVA
/home/clive/sane-backends-1.0.17/japi/Sane.c
/home/clive/sane-backends-1.0.17/japi/Sane.java
/home/clive/sane-backends-1.0.17/japi/SaneDevice.java
/home/clive/sane-backends-1.0.17/japi/SaneOption.java
/home/clive/sane-backends-1.0.17/japi/SaneParameters.java
/home/clive/sane-backends-1.0.17/japi/SaneRange.java
/home/clive/sane-backends-1.0.17/japi/ScanIt.java
/home/clive/sane-backends-1.0.17/japi/Test.java
/home/clive/sane-backends-1.0.17/japi/Makefile
/home/clive/sane-backends-1.0.17/testsuite
/home/clive/sane-backends-1.0.17/testsuite/Makefile.in
/home/clive/sane-backends-1.0.17/testsuite/README
/home/clive/sane-backends-1.0.17/testsuite/testfile.pnm
/home/clive/sane-backends-1.0.17/testsuite/Makefile
/home/clive/sane-backends-1.0.17/config.log
/home/clive/sane-backends-1.0.17/Makefile
/home/clive/sane-backends-1.0.17/libtool
/home/clive/sane-backends-1.0.17/config.status
/home/clive/downloads/sane-troubleshoot-2005-09-08.tar.gz
/home/clive/downloads/sane-troubleshoot
/home/clive/downloads/sane-troubleshoot/sane.h
/home/clive/downloads/sane-troubleshoot/Makefile
/home/clive/downloads/sane-troubleshoot/sane-troubleshoot.c
/home/clive/downloads/sane-troubleshoot/README
/home/clive/downloads/sane-troubleshoot/sane-troubleshoot.o
/home/clive/downloads/sane-troubleshoot/descriptions
/home/clive/downloads/sane-troubleshoot/descriptions/abaton.desc
/home/clive/downloads/sane-troubleshoot/descriptions/agfafocus.desc
/home/clive/downloads/sane-troubleshoot/descriptions/apple.desc
/home/clive/downloads/sane-troubleshoot/descriptions/artec.desc
/home/clive/downloads/sane-troubleshoot/descriptions/artec_eplus48u.desc
/home/clive/downloads/sane-troubleshoot/descriptions/as6e.desc
/home/clive/downloads/sane-troubleshoot/descriptions/avision.desc
/home/clive/downloads/sane-troubleshoot/descriptions/bh.desc
/home/clive/downloads/sane-troubleshoot/descriptions/canon630u.desc
/home/clive/downloads/sane-troubleshoot/descriptions/canon.desc
/home/clive/downloads/sane-troubleshoot/descriptions/canon_pp.desc
/home/clive/downloads/sane-troubleshoot/descriptions/coolscan2.desc
/home/clive/downloads/sane-troubleshoot/descriptions/coolscan.desc
/home/clive/downloads/sane-troubleshoot/descriptions/dc210.desc
/home/clive/downloads/sane-troubleshoot/descriptions/dc240.desc
/home/clive/downloads/sane-troubleshoot/descriptions/dc25.desc
/home/clive/downloads/sane-troubleshoot/descriptions/dll.desc
/home/clive/downloads/sane-troubleshoot/descriptions/dmc.desc
/home/clive/downloads/sane-troubleshoot/descriptions/epson.desc
/home/clive/downloads/sane-troubleshoot/descriptions/fujitsu.desc
/home/clive/downloads/sane-troubleshoot/descriptions/genesys.desc
/home/clive/downloads/sane-troubleshoot/descriptions/gphoto2.desc
/home/clive/downloads/sane-troubleshoot/descriptions/gt68xx.desc
/home/clive/downloads/sane-troubleshoot/descriptions/hp5400.desc
/home/clive/downloads/sane-troubleshoot/descriptions/hp.desc
/home/clive/downloads/sane-troubleshoot/descriptions/hpsj5s.desc
/home/clive/downloads/sane-troubleshoot/descriptions/ibm.desc
/home/clive/downloads/sane-troubleshoot/descriptions/leo.desc
/home/clive/downloads/sane-troubleshoot/descriptions/ma1509.desc
/home/clive/downloads/sane-troubleshoot/descriptions/matsushita.desc
/home/clive/downloads/sane-troubleshoot/descriptions/microtek2.desc
/home/clive/downloads/sane-troubleshoot/descriptions/microtek.desc
/home/clive/downloads/sane-troubleshoot/descriptions/mustek.desc
/home/clive/downloads/sane-troubleshoot/descriptions/mustek_pp.desc
/home/clive/downloads/sane-troubleshoot/descriptions/mustek_usb.desc
/home/clive/downloads/sane-troubleshoot/descriptions/nec.desc
/home/clive/downloads/sane-troubleshoot/descriptions/net.desc
/home/clive/downloads/sane-troubleshoot/descriptions/niash.desc
/home/clive/downloads/sane-troubleshoot/descriptions/pie.desc
/home/clive/downloads/sane-troubleshoot/descriptions/pint.desc
/home/clive/downloads/sane-troubleshoot/descriptions/plustek.desc
/home/clive/downloads/sane-troubleshoot/descriptions/plustek_pp.desc
/home/clive/downloads/sane-troubleshoot/descriptions/pnm.desc
/home/clive/downloads/sane-troubleshoot/descriptions/qcam.desc
/home/clive/downloads/sane-troubleshoot/descriptions/ricoh.desc
/home/clive/downloads/sane-troubleshoot/descriptions/s9036.desc
/home/clive/downloads/sane-troubleshoot/descriptions/sceptre.desc
/home/clive/downloads/sane-troubleshoot/descriptions/sharp.desc
/home/clive/downloads/sane-troubleshoot/descriptions/sm3600.desc
/home/clive/downloads/sane-troubleshoot/descriptions/sm3840.desc
/home/clive/downloads/sane-troubleshoot/descriptions/snapscan.desc
/home/clive/downloads/sane-troubleshoot/descriptions/sp15c.desc
/home/clive/downloads/sane-troubleshoot/descriptions/st400.desc
/home/clive/downloads/sane-troubleshoot/descriptions/tamarack.desc
/home/clive/downloads/sane-troubleshoot/descriptions/teco1.desc
/home/clive/downloads/sane-troubleshoot/descriptions/teco2.desc
/home/clive/downloads/sane-troubleshoot/descriptions/teco3.desc
/home/clive/downloads/sane-troubleshoot/descriptions/test.desc
/home/clive/downloads/sane-troubleshoot/descriptions/u12.desc
/home/clive/downloads/sane-troubleshoot/descriptions/umax1220u.desc
/home/clive/downloads/sane-troubleshoot/descriptions/umax.desc
/home/clive/downloads/sane-troubleshoot/descriptions/umax_pp.desc
/home/clive/downloads/sane-troubleshoot/descriptions/unsupported.desc
/home/clive/downloads/sane-troubleshoot/descriptions/v4l.desc
/home/clive/downloads/sane-troubleshoot/sane-troubleshoot
/home/clive/downloads/sane-troubleshoot/descriptions.c
/home/clive/downloads/sane-troubleshoot/COPYING
/home/clive/downloads/sane-troubleshoot/descriptions.o
/home/clive/downloads/sane-troubleshoot/descriptions.h
/home/clive/.sane
/home/clive/.sane/xsane
clive@ubuntu:~$

---

### Post by evilc on 2006-03-23
Seem's to come to a stop, as I must have a scanner and printer to work I am forced to installed Winxp on 2nd harddrive (not dual boot). Decided to use the USB scanner and both were picked up and working.
It's a pity that they won't work in Linux as I wanted to move away from MS, all I work with is photographs (edit,scan and print) I am not prepared to buy an alternative printer/scanner as from what I have read there's no sure way they will work in linux. 
I will leave Ubuntu on for now and continue to try and find the answers for scanner & printer.
Thanks for your help Pragmatist

---

### Post by 3david on 2006-05-09
I followed this thread, and I've had the exact same problems you had, after a few hours I managed to get it working (although not as a normal user, haven't figured out how to do that yet)

Here's a link to the guide I wrote (see "OpticPro 4800"):

  [http://www.ee.bgu.ac.il/~elentok/pmwiki/index.php?n=Linux.UbuntuGuide#ntoc34](http://www.ee.bgu.ac.il/~elentok/pmwiki/index.php?n=Linux.UbuntuGuide#ntoc34)


David.

---

### Post by evilc on 2006-05-09
Thanks David will give that a try.

---

### Post by skunkpit on 2006-06-01
hey 
iv been following along the posts

i have a plustek 9630 it seems supported / i have everything going its just the kernel module ti just seems like its not there the pt_drv

really sucks because iv had this scanner for like 7 years now still works and works well

make: *** /lib/modules/2.6.15-23-k7/build/: No such file or directory.  Stop.

i made a build directoy to make it happy 
now im just thinking is it posible to symlink /lib/modules/2.6.15-23-k7/build/ to where ever it needs to be?


peace

---

