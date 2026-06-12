---
title: "Asus G750JW inoperative right mouse button"
date: 2013-07-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by CliveMcCarthy on 2013-07-31
I'm running Ubuntu 13.04 on a new Asus Haswell laptop and can't get the right mouse button to work. The left button is OK and and tapping the touchpad is OK too, as is two-finger scrolling. Just no right button.

I have read sundry posts about editing the conf files but still no joy.

---

### Post by Michael_Tanner on 2013-08-01
I have the same issue.  A two-fingered tap on the touchpad acts as a right mouse click.  But I still have not figured out how to get the actual button to work.

---

### Post by darkmike00x on 2013-10-23
hello ,
my touchpad ETPS / 2 Elantech v4 protocol using the same company as shown here: [ https://www.kernel.org/doc/Documentation/input/elantech.txt ]( https://www.kernel.org/doc/Documentation/input/elantech.txt )
and I have 2 implementation issue . either:
1 . the right button does not work . In fact, I could fix it in the kernel . ( I 'd like to commit in the trunk but I do not know how to do it ) .
2 . Sometimes, the left button is the right button . I must touch the touchpad and left  clicj to make plays revive my left button as it should work. I suspect a problem with the implemetation of the protocol.


1 . The patch is here: [ http://superuser.com/questions/619582/right-elantech-touchpad-button-not-working-in-linux ]( http://superuser.com/questions/619582/right-elantech-touchpad-button-not-working-in-linux )
This reactive patch button right . This right button is turn off in linux source code by someone who is using a Mac... For cons , I do not have a Mac and I have a touchpad with the same version of firmware is version 4. I try to automate the build with dkms but without success.
Regarding the DKMS , here's what I did ( not the tar.gz provided does not work and is more prepared exactly as I prepare here) :
- I created the folder /usr/src/psmouse-elantech-v7right
- I was looking for the official source of my kernel rpm and I copied the following folder of the source drivers/input/mouse to /usr/src/psmouse-elantech-v7right/src
- I created the following sources dkms file name /usr/src/psmouse-elantech-v7right/dkms.conf :
 PACKAGE_NAME = " psmouse "
Package_version = " Elantech - v7right "
CLEAN = " rm- f * . * O "

BUILT_MODULE_NAME [0 ] = " psmouse "
MAKE [0 ] = " make-C $ M = $ kernel_source_dir dkms_tree/$ PACKAGE_NAME/$package_version/build/src/psmouse.ko "
BUILT_MODULE_LOCATION [0] = "src"
DEST_MODULE_LOCATION [0] = "/updates"

AUTOINSTALL = "yes [/code]
Only it comes to me as an error ( 0 module builted )
```

DKMS make.log for psmouse - Elantech - v7mike for kernel - 302.fc20.x86_64 3.11.5 (x86_64 )
Fri Oct. 18 2013 7:50:11 EDT
make: Entering directory `/ usr/src/kernels/3.11.5-302.fc20.x86_64 '
**DC / var/lib/dkms/psmouse/elantech-v7mike/build/src/psmouse-base.o
**DC / var/lib/dkms/psmouse/elantech-v7mike/build/src/synaptics.o
**DC / var/lib/dkms/psmouse/elantech-v7mike/build/src/alps.o
**DC / var/lib/dkms/psmouse/elantech-v7mike/build/src/elantech.o
**DC / var/lib/dkms/psmouse/elantech-v7mike/build/src/logips2pp.o
**DC / var/lib/dkms/psmouse/elantech-v7mike/build/src/lifebook.o
**DC / var/lib/dkms/psmouse/elantech-v7mike/build/src/sentelic.o
**DC / var/lib/dkms/psmouse/elantech-v7mike/build/src/trackpoint.o
**DC / var/lib/dkms/psmouse/elantech-v7m echo 0x02 | sudo dd of = debugike/build/src/cypress_ps2.o
**LD / var/lib/dkms/psmouse/elantech-v7mike/build/src/psmouse.o
**MODPOST 0 modules
make: Leaving directory `/ usr/src/kernels/3.11.5-302.fc20.x86_64 
```
I did a little research and I realized that psmouse is built statically into the kernel without a default module . It would be an error because DKMS DKMS needs not detect psmouse.ko as dynamic module ... Well, why I will not play in the kernel source and the builder ? Because that's what I want to avoid because it is long .... (but it works! ) . I 'd like to commit to the Linux Foundation. Maybe Fedora developers can help me integrate as soon as possible ? (I use Fedora 20 updates- testing # justsayin ')

2 . Regarding the second point I am trying to debug indeed the protocol of Elantech and I can not make a match of the debug module packets with source code or the protocol .
Just like that, to put an psmouse driver based on ( this is the case with most mice ) to debug , you must go to the following folder: /sys/bus/serio/drivers/psmouse/serio{1,2,3.4}/
and to
```
 echo 0x02 | sudo dd of=debug 
```

Anyway, to conclude, I would like to know where I can find a suitable spot aka wiki to document my laptop and my equipment .


Sincerely,
Michael

PS : I'm a french talker. My original post is there : [http://forums.fedora-fr.org/viewtopic.php?pid=528384](http://forums.fedora-fr.org/viewtopic.php?pid=528384)

---

