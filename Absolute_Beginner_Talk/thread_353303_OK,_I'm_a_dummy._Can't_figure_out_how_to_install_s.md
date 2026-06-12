---
title: "OK, I'm a dummy. Can't figure out how to install scanner driver"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-02-04
Yesterday I bought a new HP Scanjet 4370, went to SANE and got the proper driver, and downloaded it to my desktop: /home/kliljedahl/Desktop/backend-20060304.tar.gz
 I then extracted it to my desktop: /home/kliljedahl/Desktop/backend
, and after searching several similar threads still haven't been able to get it done.

---

### Post by tribaal on 2007-02-04
Hum silly question, but did you try to fire up XSane without doing anything else than plugging the scanner in? My HP scanner worked out of the box :)

- trib'

---

### Post by kliljedahl on 2007-02-04
> **tribaal said:**
> Hum silly question, but did you try to fire up XSane without doing anything else than plugging the scanner in? My HP scanner worked out of the box :)

- trib'

Yes I did, tried that first: "No devices available"

---

### Post by gjtoth on 2007-02-04
> **kliljedahl said:**
> Yes I did, tried that first: "No devices available"

As a "work-around" try 'gksu xsane' and see if it picks up on it

---

### Post by Bachstelze on 2007-02-04
In a terminal, run *sane-find-scanner* and see if your scanner is detected. If it is not, try running it wirh sudo.

---

### Post by kliljedahl on 2007-02-04
> **gjtoth said:**
> As a "work-around" try 'gksu xsane' and see if it picks up on it

After heeding the warning that it was dangerous to run Sane as root still got :
"No devices available"

---

### Post by kliljedahl on 2007-02-04
> **HymnToLife said:**
> In a terminal, run *sane-find-scanner* and see if your scanner is detected. If it is not, try running it wirh sudo.

Got: 
kliljedahl@kliljedahl-desktop:~$ sane-find-scanner 
bash: sane-find-scanner: command not found
kliljedahl@kliljedahl-desktop:~$ sudo sane-find-scanner 
sudo: sane-find-scanner: command not found

---

### Post by Bachstelze on 2007-02-04
You don't have the SANE backends installed, so no wonder your scanner isn't detected ;)

```
sudo apt-get install sane-utils
```

---

### Post by kliljedahl on 2007-02-04
> **HymnToLife said:**
> You don't have the SANE backends installed, so no wonder your scanner isn't detected ;)

```
sudo apt-get install sane-utils
```

Did that, then rebooted (old Windoze habit, just in case), then got:
found USB scanner (vendor=0x03f0 [hewlett packard], product=0x4105 [hp scanjet], chip=RTS8822L-01H) at libusb:005:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
kliljedahl@kliljedahl-desktop:~$ scanimage -L 

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
kliljedahl@kliljedahl-desktop:~$

---

### Post by Bachstelze on 2007-02-04
And if you run *sudo scanimage -L* ?

---

### Post by kliljedahl on 2007-02-04
> **HymnToLife said:**
> And if you run *sudo scanimage -L* ?

sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

Looks like I need to install the driver on my desktop. How to?

---

### Post by Bachstelze on 2007-02-04
You shouldn't need to install it, try to run *sudo sane-find-scanner* and then *sudo scanimage -L*.

---

### Post by kliljedahl on 2007-02-04
> **HymnToLife said:**
> You shouldn't need to install it, try to run *sudo sane-find-scanner* and then *sudo scanimage -L*.

Not working. BTW, thank you for your patience with this newbie, same result as before:
kliljedahl@kliljedahl-desktop:~$ sudo sane-find-scanner
Password:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [hewlett packard], product=0x4105 [hp scanjet], chip=RTS8822L-01H) at libusb:005:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
kliljedahl@kliljedahl-desktop:~$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
kliljedahl@kliljedahl-desktop:~$ 

It's plugged in. goes through the warm-up cycle when I reboot, so I know it's somewhat detected.

---

### Post by Bachstelze on 2007-02-04
Maybe you'll need to install your backend then... Where did you get it from ? You should also have instructions about how to install it in the archive.

---

### Post by kliljedahl on 2007-02-04
> **HymnToLife said:**
> Maybe you'll need to install your backend then... Where did you get it from ? You should also have instructions about how to install it in the archive.

Tried everything here, before I posted the thread, Got nothing bit error messages, and I did try to modify the commands to fit me. I guess I need to change the kernell code? : 
This bundle supplies a sane-patch and a simple testtool
to test the basic functions of your NIASH flatbed scanner

Models are:
HP ScanJet 3300c, 3400c, 4300c
Agfa Snapscan Touch

--------------- PRE-REQUISITES --------------------------------

before trying to make your scanner work, call:
$ less /proc/bus/usb/devices
("q" will exit, cursor up and down will scroll)

if your scanning device is not listed by name, you probably
have a 3400C or 4300C and difficulties with the kernel-usb.
The forum will give you information, how to change the
kernel code, to make your scanner work.

--------------- THE TEST TOOL ----------------------------------

to compile the testtool type:
$ make

to invoke it:
$ ./testtool

The testtool will exclusively use "libusb"
(take care that libusb is installed),
because the "scanner" module is deprecated in the 2.6-kernels.

If your system is complaining about not being able to
access the USB port "ERROR: usb_claim_interface failed"
make sure, that the scanner kernel-module is not loaded
(when using older kernels). If
$ /sbin/lsmod | grep scanner
shows "scanner ...." unload the module by
$ sudo /sbin/rmmod scanner
followed by the root-password&#8207;

if you still don't have access to the USB port, make sure that
your "/proc/bus/usb" interfaces have write access rights for everybody.
Grant write access rights by:
$ sudo chmod a+rw -R /proc/bus/usb/00*
followed by the root-password

if you still have problems, please check the cables!

--------------- SANE -------------------------------------------

To make your scanner system wide available,
you will need to "patch" SANE (http:/sane-project.org)

to patch the sane backends
get the latest sane-backend-sources from http:/sane-project.org,
unpack them and call:

$ ./patch-sane.sh /path/to/the/sane/sources/sane-backends-1.0.XX
$ cd /path/to/the/sane/sources/sane-backends-1.0.XX
$ ./configure --prefix=/usr # can be different on various systems
$ make
$ sudo make install
followed by the root-password

NOTE:
when you already have a sane-version installed on your system,
the correct --prefix can be retrieved by analizing the output of
$ ls -l `which scanimage`
Strip away everything from the output starting with "/bin/scanimage".
It might be a good idea to uninstall the older sane version first.

Have fun

---

### Post by aaronfulton on 2007-02-04
Did you extract the backend to your desktop or to /etc/sane.d/ ?

---

### Post by aaronfulton on 2007-02-04
The backends should be in your /usr/lib/sane/ folder and the corresponding config file is located in /etc/sane.d/. Once that the correct backend is there SANE should be able to find the scanner. I also have been having some problems with SANE but the heuristic it uses to locate the scanner is pretty nice and can find almost anything aslong as it has the correct backend and config file.

---

### Post by kliljedahl on 2007-02-04
> **aaronfulton said:**
> Did you extract the backend to your desktop or to /etc/sane.d/ ?

To my desktop, as I said in my original post. I'm less than a month at this after abandoning Windoze, so I still have much to learn.

---

### Post by kliljedahl on 2007-02-04
> **aaronfulton said:**
> The backends should be in your /usr/lib/sane/ folder and the corresponding config file is located in /etc/sane.d/. Once that the correct backend is there SANE should be able to find the scanner. I also have been having some problems with SANE but the heuristic it uses to locate the scanner is pretty nice and can find almost anything aslong as it has the correct backend and config file.

OK, what do I put where, and how the heck do I get it there? 
](*,) ](*,)

I admitted it i the first post, I'm a dummy. Maybe I should reinstall Windoze and go back to dual boot. I'd rather not, but this is too frustrating.

---

### Post by shareMenaPeace on 2007-02-04
Browse to the folder with nautilus and copy the "conf" and "backend".

Choose for the conf file

> Places -> Computer -> (now nautilus file browser ops up).

Navigate to 

> /etc/sane.d

Go to the folder where you extracted to - rightclick the "conf" file and copy it to the sane.d folder(rightclick the sane.d folder and choose past to folder). I guess this is a single file ending with ".conf".


Do the same for the "backend" to the folder
/usr/lib/sane/ 

And don't give up :)

---

### Post by kliljedahl on 2007-02-05
Here's what's in that  folder: /home/kliljedahl/Desktop/backend/INSTALL
/home/kliljedahl/Desktop/backend/libsane.usermap.add
/home/kliljedahl/Desktop/backend/main.c
/home/kliljedahl/Desktop/backend/Makefile
/home/kliljedahl/Desktop/backend/niash.c
/home/kliljedahl/Desktop/backend/niash.desc
/home/kliljedahl/Desktop/backend/niash.TODO
/home/kliljedahl/Desktop/backend/niash_core.c
/home/kliljedahl/Desktop/backend/niash_core.h
/home/kliljedahl/Desktop/backend/niash_libusb.c
/home/kliljedahl/Desktop/backend/niash_libusb.h
/home/kliljedahl/Desktop/backend/niash_xfer.c
/home/kliljedahl/Desktop/backend/niash_xfer.h
/home/kliljedahl/Desktop/backend/patch-sane.sh
/home/kliljedahl/Desktop/backend/README
/home/kliljedahl/Desktop/backend/sane-niash.man
/home/kliljedahl/Desktop/backend/testtool_xfer.c
 no .conf file though

---

### Post by xhabitat4humanityx on 2007-02-05
hello all,

i am also having this problem. I also have a HP 4370 and am patiently trying everything thus far...will try to move the files into respective folders.

---

### Post by shareMenaPeace on 2007-02-05
> **kliljedahl said:**
> Here's what's in that  folder: /home/kliljedahl/Desktop/backend/INSTALL
/home/kliljedahl/Desktop/backend/libsane.usermap.add
/home/kliljedahl/Desktop/backend/main.c
/home/kliljedahl/Desktop/backend/Makefile
/home/kliljedahl/Desktop/backend/niash.c
/home/kliljedahl/Desktop/backend/niash.desc
/home/kliljedahl/Desktop/backend/niash.TODO
/home/kliljedahl/Desktop/backend/niash_core.c
/home/kliljedahl/Desktop/backend/niash_core.h
/home/kliljedahl/Desktop/backend/niash_libusb.c
/home/kliljedahl/Desktop/backend/niash_libusb.h
/home/kliljedahl/Desktop/backend/niash_xfer.c
/home/kliljedahl/Desktop/backend/niash_xfer.h
/home/kliljedahl/Desktop/backend/patch-sane.sh
/home/kliljedahl/Desktop/backend/README
/home/kliljedahl/Desktop/backend/sane-niash.man
/home/kliljedahl/Desktop/backend/testtool_xfer.c
 no .conf file though
This is a source code you need to compile before you can use it.
Sorry i cant help you rightnow with compiling but im sure someone else ....
Wasnt there instructions on the website where you downloaded the code?
Can you post a link to where you downlaoded the source code?

---

### Post by kliljedahl on 2007-02-06
OK, I found a deb file here: [http://sourceforge.net/project/showfiles.php?group_id=150599&package_id=166435&release_id=453913]("http://sourceforge.net/project/showfiles.php?group_id=150599&package_id=166435&release_id=453913")
.But now when I try to access XSane I get: Failed to open device 'HP3900:libusb:004:002':
Access to resource has been denied

---

### Post by tmastran on 2007-02-06
Maybe this will help someone.

I kept getting "No scanners were identified" from scanimage -L. But, I know my SCSI canon canoscan FS2710 works because I use it with VueScan from Hamrick software on Edgy all day long.

So here's what I did to get it to also work with sane applications.
These are my rough notes and nothing polished...

=====================================
01/21/2007
Canon Canoscan FS2710

Got SCSI film scanner to work without doing anything
using the Vuescan software from hamrick.

Was NOT recognized by other software that uses SANE.
$ sudo apt-get install sane sane-utils

sane-find-scanner or scanimage -L reported No devices.
Setting this displays more info: export SANE_DEBUG_CANON=4
This told me it could not open device /dev/scanner

Issued this to find out how my scanner was connected:
cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3120026AS      Rev: 3.05
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD1600JD-32H Rev: 08.0
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi2 Channel: 00 Id: 04 Lun: 00
  Vendor: CANON    Model: IX-27025E        Rev: 1.13
  Type:   Scanner                          ANSI SCSI revision: 02

This says it's on Id 4, but that did not really help.
Doing this I guessed from the group "scanner" it is /dev/sg2:

 ls -l /dev/s*
brw-rw---- 1 root disk     8,   0 2007-01-24 17:50 /dev/sda
brw-rw---- 1 root disk     8,   1 2007-01-24 17:50 /dev/sda1
brw-rw---- 1 root disk     8,   2 2007-01-24 17:50 /dev/sda2
brw-rw---- 1 root disk     8,   3 2007-01-24 17:50 /dev/sda3
brw-rw---- 1 root disk     8,   4 2007-01-24 17:50 /dev/sda4
brw-rw---- 1 root disk     8,  16 2007-01-24 17:50 /dev/sdb
brw-rw---- 1 root disk     8,  17 2007-01-24 17:50 /dev/sdb1
brw-rw---- 1 root disk     8,  21 2007-01-24 23:51 /dev/sdb5
brw-rw---- 1 root disk     8,  22 2007-01-24 17:50 /dev/sdb6
brw-rw---- 1 root disk     8,  23 2007-01-24 23:51 /dev/sdb7
crw-rw---- 1 root audio   14,   1 2007-01-24 23:51 /dev/sequencer
crw-rw---- 1 root audio   14,   8 2007-01-24 23:51 /dev/sequencer2
crw-rw---- 1 root root    21,   0 2007-01-24 23:51 /dev/sg0
crw-rw---- 1 root root    21,   1 2007-01-24 23:51 /dev/sg1
crw-rw---- 1 root scanner 21,   2 2007-01-24 23:51 /dev/sg2
crw-rw---- 1 root root    10, 231 2007-01-24 17:50 /dev/snapshot

So then I editted /etc/sane.d/canon.conf and replaced
/dev/scanner with /dev/sg2 and it works!

---

### Post by alienexplorers on 2007-02-06
When you loaded xsane did you also select libsane and libsane-extras.  I needed all of these to get my Microtek 4800 running.

---

### Post by kliljedahl on 2007-02-06
> **alienexplorers said:**
> When you loaded xsane did you also select libsane and libsane-extras.  I needed all of these to get my Microtek 4800 running.

I only did what was suggested on this thread. I'm a complete total newbie, who intends to stay here Micro$oft free and eventually learn the code. For now, in the words of Blanche Duboiis, "Whoever you are, I have always depended on the kindness of strangers. "

---

