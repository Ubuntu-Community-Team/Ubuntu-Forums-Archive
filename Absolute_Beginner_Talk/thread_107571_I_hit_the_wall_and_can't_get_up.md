---
title: "I hit the wall and can't get up"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by Brigrat on 2005-12-23
I am in the learning process of switching from winblows to UBUNTU.  So far so good, i have several addition performed and they are running well.  Where I hit the wall is making changes to source files and then compliing the end result to load and get it to work.  Here is where I need the help to understand "linux"

when do I/You need to complie?

Most important HOW DO U COMPILE?:confused:

---

### Post by cwaldbieser on 2005-12-23
[QUOTE=Brigrat]I am in the learning process of switching from winblows to UBUNTU.  So far so good, i have several addition performed and they are running well.  Where I hit the wall is making changes to source files and then compliing the end result to load and get it to work.  Here is where I need the help to understand "linux"

when do I/You need to complie?

Most important HOW DO U COMPILE?:confused:[/QUOTE]
You only need to compile if you want to use a program that is not in the repositories, or if you want to use a more recent program.  Compiling is a lengthy topic, but typical cases are covered here:
[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

---

### Post by az on 2005-12-23
It depends on what you want to compile.

To begin, you need to install the toolchain.  That is the basic suite of compiler tools.  Install the build-essential package and that will bring everything it.

To build an application from a tarball, you go to that directory

cd /home
cd Desktop

if the tarball is called foo.tar.gz

tar xvzf foo.tar.gz

cd foo
./configure
make
make install

Now you should read the README provided with the tarball to know what libraries you need to compile it with.  You may need libgtk2.0-dev, for example to compile something which uses the gtk2 shared libraries.

---

### Post by Brigrat on 2005-12-23
What i am trying to do is get the program for talking to my nokia phone working correctly.  I have the google hits with the instructions on what to do printed but after making the changes do I need to re-complie the code?

---

### Post by az on 2005-12-23
[QUOTE=Brigrat] but after making the changes do I need to re-complie the code?[/QUOTE]
Yes.


If you will be compiling a kernel module, you will also need to install the linux-headers-2.6.12-10-386 (or another version if that is what you are running - check your linux-image version in synaptic) and the gcc-3.4 compiler.  Do you know if you need to recompile a kernel module with that?

---

### Post by Totzo on 2005-12-23
which program are you using? I use gnokii and gnome-phone-manager with a bluetooth connection (all from the repositories) and they both work fine. If you backup the contacts with gnokki (as a vcf file) you can then import the file to your address book

---

### Post by Brigrat on 2005-12-23
totzo,
      gnokii is the program but with the nokia 6015i if you google that you will find the info about the changes that need to be made to see the phone.  He listed the changes in the info.  Can i cut and past them in?  Do I need to compile anything after I make the changes?

---

### Post by Totzo on 2005-12-24
you shouldn't have to re-compile the program, I would guess that you just have to edit your .gnokiirc file which should be in your home directory. Mine looks like this:

```
[global]
port = 00:12:62:d4:56:4a
#Gnokii treats the 6230 as a 6510; similar, but not everything works on it.
model = 6510
initlength = default
connection = bluetooth
use_locking = no
serial_baudrate = 19200
rfcomm_channel = 1
smsc_timeout = 10
```


I think it treats your phone (mine is a 6310 with a bluetooth connection) the same as a 6510 as well, are you using a cable or bluetooth connection? The real trick is getting the hardware recognised and identifying where it is.

---

### Post by Nightwind on 2005-12-24
SO what you really want to know is A: can you just add the lines of code without compiling. B: What compiler(s) you might need, and step by step instructions or a link to that, correct? A few more details might be helpful so that we can help a little bit better

---

### Post by Brigrat on 2005-12-24
Yes just like "kevin" in the gnokii thread below.  I have searched for the directories but have either not searced right or do not have everything installed right.  I have cut and pasted the thread in so that you can see what the individual edited.  I"ll be on all day and checking the thread from time to time.  I appreciate the answers and your time.




Nokia 6015i support

--------------------------------------------------------------------------------
From:  gnokii 
Subject:  Nokia 6015i support 
Date:  Wed, 16 Nov 2005 19:49:37 -0500 
User-agent:  Mutt/1.5.9i 

--------------------------------------------------------------------------------

I just got my Nokia 6015i working with gnokii today.  I'm using a
clone of a DKU-5 cable (it's a TUSB3410 one with ID 0451:3410).  In
order to get the cable to work I had to add the script that's in the
driver source file:

[http://www.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=drivers/usb/serial/ti_usb_3410_5052.c](http://www.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=drivers/usb/serial/ti_usb_3410_5052.c)

to the /etc/hotplug.d/usb directory.

Then when I plugged it in, dmesg would tell me that it was connected
as /dev/ttyUSB0.

I then edited my .gnokiirc to contain:

---
[global]
port = /dev/ttyUSB0
model = 6510
---

Thinking that this would be sufficient to talk to the phone (being
that the Nokia website tells me it uses the same SDK as the 3510i,
which gnokii treats like a 6510).  Found out that this wasn't
sufficient, so I had to make the following change to the current CVS
tree (the RH-55 came initially from a random website, but was
confirmed by the "Type: RH-55" printed in the battery compartment of
the phone):

Index: misc.c
===================================================================
RCS file: /cvsroot/gnokii/gnokii/common/misc.c,v
retrieving revision 1.103
diff -u -r1.103 misc.c
--- misc.c      28 Oct 2005 17:17:38 -0000      1.103
+++ misc.c      17 Nov 2005 00:32:40 -0000
@@ -196,6 +196,7 @@
        {"6010",  "NPM-10", 0 },
        {"6010",  "NPM-10X", 0 },
        {"6011",  "RTE-2RH", 0 },
+       {"6015i", "RH-55", PM_CALENDAR | PM_SPEEDDIAL | PM_EXTPBK | PM_SMS | 
PM_FOLDERS },
        {"6020",  "RM-30", PM_CALLERGROUP | PM_CALENDAR | PM_SPEEDDIAL
        | PM_NETMONITOR | PM_EXTPBK | PM_SMS | PM_FOLDERS },
        {"6021",  "RM-94", PM_CALLERGROUP | PM_CALENDAR | PM_SPEEDDIAL
        | PM_NETMONITOR | PM_EXTPBK | PM_SMS | PM_FOLDERS },
        {"6050",  "NME-1", 0 },
Index: phones/nk6510.c
===================================================================
RCS file: /cvsroot/gnokii/gnokii/common/phones/nk6510.c,v
retrieving revision 1.188
diff -u -r1.188 nk6510.c
--- phones/nk6510.c     22 Oct 2005 18:15:51 -0000      1.188
+++ phones/nk6510.c     17 Nov 2005 00:32:40 -0000
@@ -230,7 +230,7 @@
        pgen_incoming_default,
        /* Mobile phone information */
        {
- 
"6510|6310|8310|6310i|6360|6610|6100|5100|3510|3510i|3595|6800|6810|6820|6820b|6610i|6230|6650|7210|7250|7250i|7600|6170|6020|6230i|5140|5140i|6021|6500|6220|3120b|3100|3120",
 /* Supported models */
+ 
"6510|6310|8310|6310i|6360|6610|6100|5100|3510|3510i|3595|6800|6810|6820|6820b|6610i|6230|6650|7210|7250|7250i|7600|6170|6020|6230i|5140|5140i|6021|6500|6220|3120b|3100|3120|6015i",
 /* Supported models */
                7,                     /* Max RF Level */
                0,                     /* Min RF Level */
                GN_RF_Percentage,      /* RF level units */


After doing this, compiling, and installing, I could change the
.gnokiirc to read:

---
[global]
port = /dev/ttyUSB0
model = 6015i
---

and then was able to do a "gnokii --identify" which gave me back:

$ gnokii --identify
GNOKII Version 0.6.10
IMEI         : (unknown)
Manufacturer : Nokia
Model        : R
Revision     : V M125_03w24_49_12.

So, now I can download and save my addressbook, and retrieve and write
calendar events.  I was quite happy to see that I can effectively use
the cable and phone combo with Linux (in this case, Debian and
Ubuntu).

Cheers,

Kevin.

---

### Post by Nightwind on 2005-12-24
Totzo, Did you find anything on using a USB connection  for the phone. I understood that you used bluetooth.

---

### Post by Totzo on 2005-12-24
for setting up bluetooth check this out

[https://wiki.ubuntu.com/BluetoothSetup?highlight=%28bluetooth%29](https://wiki.ubuntu.com/BluetoothSetup?highlight=%28bluetooth%29)[HTML][/HTML]

I have no idea about using a usb connection for the phone but I would guess that it should be recognised automatically. Try installing usbview and run it to see if your phone shows up. Beyond that I'm not sure, just keep googling and you'll get there eventually! Merry xmas.

---

