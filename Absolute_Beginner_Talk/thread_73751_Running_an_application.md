---
title: "Running an application"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by Eldon on 2005-10-09
I'm trying to install my oscilliscope software from [here]("http://www.bitscope.net/download/?p=1").  I've downloaded version 1.2 for Linux and extracted the dso folder to my home folder.  Within the dso folder is the Dso executable which Linux realizes is an executable but double clicking it or calling it from the command line does nothing.  I've moved it into /usr/bin/dso now and same result.   Here's the ls -l from /usr/bin/dso:

/usr/bin/dso$ ls -l
total 1140
-rw-r--r--  1 ep ep    2524 2005-06-01 00:18 BitScope.prb
-rwxr-xr-x  1 ep ep 1067972 2005-06-06 01:59 Dso
-rw-r--r--  1 ep ep   59078 2005-04-29 02:22 FIX.txt
-rw-r--r--  1 ep ep    2123 2005-02-17 20:59 LICENSE.txt
-rw-r--r--  1 ep ep     813 2005-03-16 22:00 MANIFEST.txt
-rw-r--r--  1 ep ep   11735 2005-06-06 01:58 README.txt
-rw-r--r--  1 ep ep    1985 2004-08-29 13:03 SYDNEY.txt

I'm sure I'm missing something really basic here, any ideas what that might be?  What steps do I need to do to run an executable?

---

### Post by aysiu on 2005-10-09
I noticed [in my Synaptic that bitscope was in multiverse](http://i22.photobucket.com/albums/b337/psychocats/52e2f0ad.png).
Just follow [these directions](http://www.psychocats.net/sources.html).

Then, type this in a terminal ```
sudo apt-get update
sudo apt-get install bitscope
```

---

### Post by heimo on 2005-10-09
EDIT: Oh, see the post above. Should be easier. (aysiu always knows what he's talking about) :)

What does this do?
```
cd /usr/bin/dso
./Dso

``` Nothing? How about:
```
 file Dso
```Something like *Dsi: ELF 32-bit executable*...?

---

### Post by Eldon on 2005-10-10
Thanks for the quick replies guys.  I've tried both suggestions now, installing with apt-get gave me an icon in my applications menu but clicking it flashes a small window which closes before I can see anything.  Is there someplace I can look for more information on why its not opening like an application log?  I've looked in the auth.log, syslog, daemon.log, kern.log, user.log, debug and messages logs but nothing related to the application failing is registered.

Here's the info from suggestion 2:

ep@pos17:~$ cd /usr/bin/dso
ep@pos17:/usr/bin/dso$ ./Dso
./Dso: symbol lookup error: ./Dso: undefined symbol: initPAnsiStrings
ep@pos17:/usr/bin/dso$ file Dso
Dso: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped
ep@pos17:/usr/bin/dso$ sudo apt-get install bitscope
Reading package lists... Done
Building dependency tree... Done
bitscope is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by cwaldbieser on 2005-10-10
[QUOTE=Eldon]Thanks for the quick replies guys.  I've tried both suggestions now, installing with apt-get gave me an icon in my applications menu but clicking it flashes a small window which closes before I can see anything.  Is there someplace I can look for more information on why its not opening like an application log?  I've looked in the auth.log, syslog, daemon.log, kern.log, user.log, debug and messages logs but nothing related to the application failing is registered.

Here's the info from suggestion 2:

ep@pos17:~$ cd /usr/bin/dso
ep@pos17:/usr/bin/dso$ ./Dso
./Dso: symbol lookup error: ./Dso: undefined symbol: initPAnsiStrings
ep@pos17:/usr/bin/dso$ file Dso
Dso: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped
ep@pos17:/usr/bin/dso$ sudo apt-get install bitscope
Reading package lists... Done
Building dependency tree... Done
bitscope is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.[/QUOTE]
Try running the version you installed with synaptic in the console.  E.g.
```

$ dso
OR
$ /usr/bin/dso

```
The errors should end up being printed to the console so you can read them.

---

### Post by Eldon on 2005-10-10
I think I've covered what you asked me to do here cwaldbieser, let me know if I botched it:
ep@pos17:~$ Dso
bash: Dso: command not found
ep@pos17:~$ dso
bash: dso: command not found
ep@pos17:~$ cd /usr/bin/dso
ep@pos17:/usr/bin/dso$ ls
BitScope.prb  Dso  FIX.txt  LICENSE.txt  MANIFEST.txt  README.txt  SYDNEY.txt
ep@pos17:/usr/bin/dso$ Dso
bash: Dso: command not found
ep@pos17:/usr/bin/dso$ dso
bash: dso: command not found
ep@pos17:/usr/bin/dso$ /usr/bin/dso/Dso
/usr/bin/dso/Dso: symbol lookup error: /usr/bin/dso/Dso: undefined symbol: initPAnsiStrings
ep@pos17:/usr/bin/dso$

---

### Post by heimo on 2005-10-10
How about running:
```
bitscope
```

Side note: If you're running binary from a current working directory and it's not in PATH environment variable (never mind what this means...) - you always need to prefix it with ./ (dot stands for current directory), for example: 
```
./Dso
```
Using just Dso will result in "command not found".

---

### Post by aysiu on 2005-10-10
How about ```
man bitscope
```?

---

### Post by Eldon on 2005-10-10
Heh so it turns out that the bitscope installed with apt-get isn't the oscilloscope but some sort of media player.  I guess its back to the original .tar.gz I extracted to /usr/bin/dso.

no man's for bitscope, dso or Dso.

Thanks for the side note Heimo, I didn't know that :)  learning slowly.

Just to be clear, is what I'm trying to do ok?  Can I run a program for generic "Linux" on Ubuntu?  Or does it have to be compiled by Ubuntu or am I just SOL/confused?

---

### Post by aysiu on 2005-10-10
[QUOTE=Eldon]Heh so it turns out that the bitscope installed with apt-get isn't the oscilloscope but some sort of media player.  I guess its back to the original .tar.gz I extracted to /usr/bin/dso.[/quote]

Apparently the following statement is not true:

[quote=heimo]aysiu always knows what he's talking about[/quote]

> 
Just to be clear, is what I'm trying to do ok?  Can I run a program for generic "Linux" on Ubuntu?  Or does it have to be compiled by Ubuntu or am I just SOL/confused? No, installing a generic program is fine if it's installed from source.

According to the Readme file, you need to do this before launching the dso file: > Install the libborqt-6.9-qt2.3.so library.
     
     This application  runs under X  Windows and requires  a modified
     QT2  library (libborqt-6.9-qt2.3.so).   If you  don't  have this
     library it is available as an RPM, DEB or TGZ archive:
     
     [http://kylixlibs.sourceforge.net/down.html](http://kylixlibs.sourceforge.net/down.html)
     
     The library  installs in  its own directory  in /usr/lib,  so it
     will  not interfere  with anything  else already  installed that
     uses your Linux distribution's own version of the Qt library (if
     installed). If you download a .deb version, just ```
sudo dpkg -i libborqt-6.9-qt2.3.so.deb
``` and it should be installed.

---

### Post by heimo on 2005-10-10
Let's see if I got all the steps... (I'm in a hurry, going to be late from work... 15 mins...)[LIST=1]
[*]Download  kylixlibs3-borqt-3.0-2.tar.gz from here [http://kylixlibs.sourceforge.net/down.html]("http://kylixlibs.sourceforge.net/down.html")
[*]extract and install
[*]tar xzvf [kylixlibs3-borqt-3.0-2.tar.gz]("http://prdownloads.sourceforge.net/kylixlibs/kylixlibs3-borqt-3.0-2.tar.gz?download")
[*]cd kylixlibs3-borqt
[*]sudo ./install
[*]Run: ```
export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/lib/kylix3/
```
[*]Run ./Dso[/LIST]Worked for me. :)

EDIT: .deb package didn't work for me

---

### Post by aysiu on 2005-10-10
Actually, this is weird. I went to that website. There were no files of that name there, so I went with the closest one I could find:
```
sudo dpkg -i kylixlibs3-borqt_3.0-1_i386.deb
dpkg-deb: `kylixlibs3-borqt_3.0-1_i386.deb' is not a debian format archive
dpkg: error processing kylixlibs3-borqt_3.0-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 kylixlibs3-borqt_3.0-1_i386.deb
``` Even though it looks like a .deb, dpkg doesn't acknowledge it as a .deb. Hm. Anyone have any ideas? I'm stumped.

**Edit**: heimo beat me to it, and did it successfully!

---

### Post by Eldon on 2005-10-10
It worked!!
Awesome, thanks a ton for all your help.  I still feel silly for not reading the readme file (this time around) but honestly I never would have got through that kylix install alive.  I don't even want to tell you about all the errors I had and ignored while installing it.. whatever, it works now :D

Edit:  Ok I will ask :)
This is the install.sh file:
#! /bin/sh

install -d /usr/lib/kylix3/
install -m 755 libborqt-6.9.0-qt2.3.so /usr/lib/kylix3/libborqt-6.9.0-qt2.3.so

cd /usr/lib/kylix3/
cp -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so

grep -q "^/usr/lib/kylix3\$" /etc/ld.so.conf
if [ $? == 1 ]; then
  echo /usr/lib/kylix3 >> /etc/ld.so.conf
fi

/sbin/ldconfig

It references etc/ld.so.conf which doesn't exist on my system.  Is this config file called something else on my system?  Should I worry that this info wasn't entered?

And what does Aysiu mean when he says "its ok if its installed from source."  

Thanks again... whats lacking from forums is a way to buy those who help you a beer.

---

### Post by heimo on 2005-10-10
[quote=Eldon]
It references etc/ld.so.conf which doesn't exist on my system. Is this config file called something else on my system? Should I worry that this info wasn't entered?
[/quote] Hmm... not really, but the script should have created the file if it didn't exist. Oh, by the way, you probably need to add that export-line to your ~/.bashrc file - or run manually every time before running the Dso.
My /etc/ld.so.conf's contents:
```

/usr/X11R6/lib
/usr/lib/kylix3

``` 
[quote=Eldon]
And what does Aysiu mean when he says "its ok if its installed from source."  
[/quote] All the free software (free as speech) includes source code - and you get the binary version by compiling the "source" - the actual code that some programmer wrote. But the version we installed was already compiled / binary.

[quote=Eldon]
Thanks again... whats lacking from forums is a way to buy those who help you a beer.[/quote] Is Kassetra around? I have a suggestion how to improve forums. ;-P Or maybe there's Ubuntu gathering in near future? :D

---

### Post by Eldon on 2005-10-10
> Oh, by the way, you probably need to add that export-line to your ~/.bashrc file
You're one step ahead of me, I had just figured out I need to run that export command each time and was coming back to figure out where I needed to add it for permanence.  
Thanks for the source clarification.  I still need to figure out compiling source but thats a task for another batch of free time.  \\:D/   (where's the beer smiley?)

---

### Post by Endolith on 2008-06-02
> **aysiu said:**
> I noticed [in my Synaptic that bitscope was in multiverse](http://i22.photobucket.com/albums/b337/psychocats/52e2f0ad.png).

That bitscope has nothing to do with the oscilloscope. :)  The bitscope package is for analyzing 32-bit JACK audio signals for errors.   The BitScope is a hardware device with software called "dso".  Just for the record.

I've had the dso program installed and working for a while, but I can't get it to connect to my scope hardware.  Does anyone know how to do this?  


The README says:

> 
[3a] Connect your BitScope to the PC.                           (USB)
     
     If you're using  a USB BitScope with a  Kernel older than 2.4.20
     you may need to install the FTDI USB drivers:
     
     [http://ftdi-usb-sio.sourceforge.net/](http://ftdi-usb-sio.sourceforge.net/)
     
     Otherwise the BitScope should  be detected by the usbmgr process
     (if running) and configured to a device.
     
     BitScope  appears  as a  virtual  serial  device  and should  be
     accessible as /dev/ttyUSB0 or  similar.  If your distibution has
     not created  the USB  serial devices, they  have major  a device
     number  188  and can  be  created  with  a command  like  "mknod
     /dev/ttyUSB0 c 188 0".

...

 [5] Optionally click the SETUP button.
     
     This step configures the application  to talk to your device. If
     you have  a USB  BitScope, chances are  that it will  already be
     configured (you can skip this step).
     
     If you have an RS-232 or Ethernet BitScope, or if the USB driver
     installed the  device somewhere  other than at  /dev/ttyUSB0 you
     will need to tell the DSO where it is.

But it certainly seems to be at ttyUSB0:

```
Jun  2 00:24:53 Inspiron kernel: [184255.379056] usb 1-1: new full speed USB device using uhci_hcd and address 89
Jun  2 00:24:53 Inspiron kernel: [184255.586894] usb 1-1: configuration #1 chosen from 1 choice
Jun  2 00:24:53 Inspiron kernel: [184255.595133] ftdi_sio 1-1:1.0: FTDI USB Serial Device converter detected
Jun  2 00:24:53 Inspiron kernel: [184255.595197] /build/buildd/linux-2.6.24/drivers/usb/serial/ftdi_sio.c: Detected FT232BM
Jun  2 00:24:53 Inspiron kernel: [184255.595395] usb 1-1: FTDI USB Serial Device converter now attached to ttyUSB0
Jun  2 00:24:53 Inspiron NetworkManager: <debug> [1212380693.865586] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_403_6001_BSC8I0Q9'). 
Jun  2 00:24:54 Inspiron NetworkManager: <debug> [1212380694.010207] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_403_6001_BSC8I0Q9_if0'). 
Jun  2 00:24:54 Inspiron NetworkManager: <debug> [1212380694.028324] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_403_6001_BSC8I0Q9_if0_serial_usb_0').
```

---

### Post by Endolith on 2008-06-02
Oh never mind I just figured it out!  :)  You have to press SETUP button and where it says "IP Address or Port", replace "COM1" with "/dev/ttyUSB0".  I was replacing it with "ttyUSB0" and that wasn't working.

---

### Post by Endolith on 2008-06-07
Also, you probably want to get the kylixlibs3-borqt_3.0.2bs-1_i386.deb file directly from BitScope website.

[http://www.bitscope.net/download/?p=1](http://www.bitscope.net/download/?p=1)

---

