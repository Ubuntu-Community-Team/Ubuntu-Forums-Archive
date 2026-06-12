---
title: "Wacom Bamboo Pen and Touch with Ubuntu 10.04 Lucid, not recognizing some gestures"
date: 2011-05-14
forum: Art &amp; Design
---

### Post by Kurtless on 2011-05-14
So I upgraded recently to 10.04, and I wanted my Wacom pen and touch tablet to work on it so I could get to drawing and everything. After hours of trying to install packages in the terminal, and having none of them work with my tablet, I came across this "dkms" install.

I followed the instructions on the site (here: [http://blog.brettalton.com/2010/08/28/install-the-wacom-bamboo-driver-in-ubuntu-10-04-lucid-lynx-using-ppas-tutorialhowto/](http://blog.brettalton.com/2010/08/28/install-the-wacom-bamboo-driver-in-ubuntu-10-04-lucid-lynx-using-ppas-tutorialhowto/)), its not the original site, but I basically did what it says here).

After rebooting, the tablet worked! Yet something was amiss, I could move the cursor around, but once I tapped something (in gimp, the desktop, etc.) It wouldn't move until I wiggled the pen for 2 or 3 seconds or when I went to the edge of the tablet, it was functional, but I couldn't draw anything in Gimp, which is what I need this for.

I've read that what I have installed is the best for 10.04 at the moment, and that things will be updated in the future (soon I hope), and then finally I can use my tablet to it's fullest capacity.

Am I at the best dkms version for my tablet? Is there anyway I can make it work better? Help please! I want this to work completely! It used to work awesomely when I was on a lower version of my OS (I used the install guide for lucid here on Ubuntu forums), but when I updated (as in erased everything, then installed the new OS), it stopped working!

---

### Post by Favux on 2011-05-14
What model of the Bamboo P&T are you using in Lucdid?  Enter in a terminal *lsusb* and post the line in the output with Wacom.

If it is freezing when you use the stylus you should be able to do better than that.  The stylus should be working perfectly.  See the [Wacom Pen and Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by Kurtless on 2011-05-16
So here is what pops up when I type in lsusb:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 056a:00d4 Wacom Co., Ltd 
Bus 003 Device 002: ID 045e:006a Microsoft Corp. Wireless Optical Mouse (IntelliPoint)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I believe I bought the medium sized tablet, its just a regular Pen and touch, not a high tech or "fun" edition or anything. 

And its not that it freezes, its just that when I tap it, usually you can just guide the cursor by having the pen held a little above the tablet, but after I press down on the tablet I can't guide the cursor anymore by holding the pen above the tablet, I have to hold down the pen on the pad to move it anywhere after that, or if I, like I said, wiggle the pen a little bit.

I'll look into that guide, thanks.

---

### Post by Kurtless on 2011-05-26
> **Favux said:**
> What model of the Bamboo P&T are you using in Lucdid?  Enter in a terminal *lsusb* and post the line in the output with Wacom.

If it is freezing when you use the stylus you should be able to do better than that.  The stylus should be working perfectly.  See the [Wacom Pen and Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

On top of my last message, I tried what you told me, I did all of this in that "How To", here is what I did: 

"For Lucid only update to xorg-macros v. 1.8 (you only need to do this once). You do not need to update xorg-macros in Maverick, it already has v. 1.8.
Code:
wget [http://xorg.freedesktop.org/releases/individual/util/util-macros-1.8.0.tar.bz2](http://xorg.freedesktop.org/releases/individual/util/util-macros-1.8.0.tar.bz2)

sudo cp /usr/share/aclocal/xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4.bak

tar xjvf util-macros-1.8.0.tar.bz2

cd util-macros-1.8.0

./configure --prefix=/usr

make

sudo make install

cd ..
b) Now compile xf86-input-wacom-0.11.0 (download, compile, and install xf86-input-wacom):
Code:
cd ./Desktop

wget [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2)

sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev

sudo apt-get upgrade

tar xjvf xf86-input-wacom-0.11.0.tar.bz2

cd xf86-input-wacom-0.11.0

./configure --prefix=/usr

make

sudo make install
Now reboot."

And after all of this, the stylus still only does what it did, as I described before, the website I mentioned in the first post seemed to get my tablet working, but in a way that I said in my 2nd post, should I just wait for another update from that website, is all hope lost?!

---

### Post by Favux on 2011-05-26
Hi Kurtless,

What's happening is the wacom.ko dkms from the PPA is still there and is over riding your attempt to install the one you just compiled.  You need to remove it.  Look in the /usr/src directory.  There should be something named wacom-version #.  Please post the name so I can give you the command to uninstall it.  You might want to remove the PPA first.

---

### Post by Kurtless on 2011-05-27
> **Favux said:**
> Hi Kurtless,

What's happening is the wacom.ko dkms from the PPA is still there and is over riding your attempt to install the one you just compiled.  You need to remove it.  Look in the /usr/src directory.  There should be something named wacom-version #.  Please post the name so I can give you the command to uninstall it.  You might want to remove the PPA first.

Oh ok that makes sense, I did what you told me and I got "wacom-0.8.10.2", it was a folder in the src directory. Thanks for helping me I really appreciate it.

---

### Post by cracker89 on 2011-05-27
thinking of getting a bamboo... is it any good? as in for sketching purposes? nd obviously, if linux is working out good for u on it?

---

### Post by Kurtless on 2011-05-27
> **cracker89 said:**
> thinking of getting a bamboo... is it any good? as in for sketching purposes? nd obviously, if linux is working out good for u on it?


Yeah! When I had it working on a earlier Ubuntu version, it was great! If you just want to sketch, it has a really good pressure sensing feature, and it can definitely be used for that, it just takes a bit to get used to a tablet, I still am getting used to it. I just hope I can get my tablet to work soon, its a bit more effort to get it to work with Linux/Ubuntu, but when it does work, Gimp, Inkscape, or whatever art program, is great to use. The Pen and Touch is my first tablet ever, and it is working very nicely, when I get it working with Ubuntu again that is XD

---

### Post by Favux on 2011-05-27
Hi Kurtless,

The version number is 0.8.10.2 so this command should remove it:
```
sudo dkms remove -m wacom -v 0.8.10.2 --all
```
Then go back to your input-wacom folder (from part I. of the HOW TO) and repeat the copy command:
```
sudo cp ./2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
That should get your newly compiled wacom.ko into place.

---

### Post by Kurtless on 2011-05-27
> **Favux said:**
> Hi Kurtless,

The version number is 0.8.10.2 so this command should remove it:
```
sudo dkms remove -m wacom -v 0.8.10.2 --all
```
Then go back to your input-wacom folder (from part I. of the HOW TO) and repeat the copy command:
```
sudo cp ./2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
That should get your newly compiled wacom.ko into place.

Thanks, so I removed the dkms, and that seemed to work, but the other command you gave me, just had this pop up when I put it in:

"kurtless@kurtless-desktop:~$ sudo cp ./2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
[sudo] password for kurtless: 
cp: cannot stat `./2.6.30/wacom.ko': No such file or directory
kurtless@kurtless-desktop:~$ "

Am I doing something wrong? The tablet won't even work now.

---

### Post by Favux on 2011-05-27
Did you do part I. in the Bamboo Pen and Touch HOW TO?  That's to compile and install the usb kernel driver wacom.ko from input-wacom.  If you did there should be an input-wacom folder on you Desktop.  For the command to work while in the terminal you have to change directories into the folder before you run the command.

---

### Post by Kurtless on 2011-05-27
> **Favux said:**
> Did you do part I. in the Bamboo Pen and Touch HOW TO?  That's to compile and install the usb kernel driver wacom.ko from input-wacom.  If you did there should be an input-wacom folder on you Desktop.  For the command to work while in the terminal you have to change directories into the folder before you run the command.


Thanks for helping me through this. So how do I "change directories into the folder"? Do I put that input folder in that folder where the dkms was before?

And yes I did part 1 of that How to.

---

### Post by Favux on 2011-05-27
Well if you still have the input-wacom folder on the Desktop I'll break it into two steps like in the HOW TO.  The terminal starts in the /home/yourusername directory by default so:
```
cd Desktop

cd input-wacom-0.11.0

```
Then you can run the copy command since the directories will now be what it expects.  It should just return the prompt, $, and you shouldn't see the stat error.

---

### Post by Kurtless on 2011-05-27
> **Favux said:**
> Well if you still have the input-wacom folder on the Desktop I'll break it into two steps like in the HOW TO.  The terminal starts in the /home/yourusername directory by default so:
```
cd Desktop

cd input-wacom-0.11.0

```
Then you can run the copy command since the directories will now be what it expects.  It should just return the prompt, $, and you shouldn't see the stat error.

Ok, I think I got everything right until I got to the copy command, is this what it is supposed to look like?

"
kurtless@kurtless-desktop:~$ cd Desktop
kurtless@kurtless-desktop:~/Desktop$ cd xf86-input-wacom-0.11.0
kurtless@kurtless-desktop:~/Desktop/xf86-input-wacom-0.11.0$ sudo cp ./2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
cp: cannot stat `./2.6.30/wacom.ko': No such file or directory
kurtless@kurtless-desktop:~/Desktop/xf86-input-wacom-0.11.0$"

That "cannot stat" seems to be telling me I'm doing something wrong. The original " cd input-wacom-0.11.0", you gave me didn't work because the folder on the desktop was called "xf86-input-wacom-0.11.0", so I put that name in, then I put in the command you gave me "sudo cp ./2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko", but it came up with what is above. 

Thank you for being so patient with me, I'm trying to figure this all out.

---

### Post by Favux on 2011-05-27
It's looking like you only did part II.  That's the Wacom X driver xf86-input-wacom.  Paired with it is the usb kernel driver from input-wacom.  That's why you're getting the stat.  The X driver doesn't make the wacom.ko so it isn't there to copy.  I know, the names are confusing because they are so similar.

---

### Post by Kurtless on 2011-05-27
> **Favux said:**
> It's looking like you only did part II.  That's the Wacom X driver xf86-input-wacom.  Paired with it is the usb kernel driver from input-wacom.  That's why you're getting the stat.  The X driver doesn't make the wacom.ko so it isn't there to copy.  I know, the names are confusing because they are so similar.

Thanks for the insight, I believe I did the first step, because I have this file on my desktop: "input-wacom-0.11.0.tar.bz2". To try something else, I extracted the folder from this tar.bz2, which was named "input-wacom-0.11.0", to the desktop, which seems to be the right name that you told me, so I plugged it in, and this is what I got again:


kurtless@kurtless-desktop:~$ cd Desktop
kurtless@kurtless-desktop:~/Desktop$ cd input-wacom-0.11.0
kurtless@kurtless-desktop:~/Desktop/input-wacom-0.11.0$ sudo cp ./2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
cp: cannot stat `./2.6.30/wacom.ko': No such file or directory
kurtless@kurtless-desktop:~/Desktop/input-wacom-0.11.0$ 


There is still a "cannot stat" thing. Should I go over step 1 again just to be sure, or am I doing the right thing, thanks again.

---

### Post by Favux on 2011-05-27
If the folder was still compressed my guess is you did not actually do part I. and compile the wacom.ko.  Or else if you did you deleted the folder with the compiled wacom.ko.  So the new uncompressed input-wacom folder won't have the wacom.ko until you compile it and that's why the copy command won't work.

---

### Post by Kurtless on 2011-05-27
> **Favux said:**
> If the folder was still compressed my guess is you did not actually do part I. and compile the wacom.ko.  Or else if you did you deleted the folder with the compiled wacom.ko.  So the new uncompressed input-wacom folder won't have the wacom.ko until you compile it and that's why the copy command won't work.

Ok that certainly makes sense, I did step 1 again, and I think it worked, heres what I get when I put those commands in now:

kurtless@kurtless-desktop:~$ cd Desktop
kurtless@kurtless-desktop:~/Desktop$ cd input-wacom-0.11.0
kurtless@kurtless-desktop:~/Desktop/input-wacom-0.11.0$ sudo cp ./2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
[sudo] password for kurtless: 
kurtless@kurtless-desktop:~/Desktop/input-wacom-0.11.0$ 

It went back to "kurtless@kurtless-desktop:~/Desktop/input-wacom-0.11.0$", after that sudo command and my password, but it seems my pen tablet still is not working...hmmmmm. Its been great having your help, is there anything else I can do to get my tablet to work?

---

### Post by Favux on 2011-05-27
Did you reboot?

In Lucid the wacom.conf is in a non-standard place so check if you have a 10-wacom.conf at /usr/lib/X11/xorg.conf.d.  The xf86-input-wacom you compiled in part II. won't install a wacom.conf in a non-standard location.  Use Nautilus/Places to check. If it is there post the contents.  If not install the sample version in part III. a).  Then reboot.

---

### Post by Kurtless on 2011-05-27
> **Favux said:**
> Did you reboot?

In Lucid the wacom.conf is in a non-standard place so check if you have a 10-wacom.conf at /usr/lib/X11/xorg.conf.d.  The xf86-input-wacom you compiled in part II. won't install a wacom.conf in a non-standard location.  Use Nautilus/Places to check. If it is there post the contents.  If not install the sample version in part III. a).  Then reboot.

I put "10-wacom.conf", in the directory you told me, I put in that .conf file step 3's stuff, which is this: 

"Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
#	Option "ForceDevice" "ISDV4"  # deprecated starting with
#        xf86-input-wacom-0.10.8
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection"

I made a .conf file with the right name, and pasted all the information above in it, and saved it to the right directory.

After I made that file in that directory, I rebooted, and plugged in my tablet, the tablet still doesn't work. Did I do something wrong? Thanks for helping me, gosh, this is taking a bit huh?

---

### Post by Favux on 2011-05-27
Yep, a little bit.

Alright, since there was a compiled wacom.ko that you were able to copy into place and the dkms is removed that should mean you have usb communication established to your tablet.

It sounds like there wasn't a 10-wacom.conf where it should have been.  Is that correct?  Now that you have one udev can match to the tablet and put it on the Wacom X driver.

So that leaves a problem with the Wacom X driver xf86-input-wacom in part II.  Did that compile without errors and did it seem to install OK?  You might want to redo part II.

Or the other possibility is that your system is not auto-loading the usb driver.  Let's check on that too.  Enter in a terminal:
```
lsmod | grep wacom
```
You should see 'wacom' in the terminal followed by some numbers.

---

### Post by Kurtless on 2011-05-27
> **Favux said:**
> Yep, a little bit.

Alright, since there was a compiled wacom.ko that you were able to copy into place and the dkms is removed that should mean you have usb communication established to your tablet.

It sounds like there wasn't a 10-wacom.conf where it should have been.  Is that correct?  Now that you have one udev can match to the tablet and put it on the Wacom X driver.

So that leaves a problem with the Wacom X driver xf86-input-wacom in part II.  Did that compile without errors and did it seem to install OK?  You might want to redo part II.

Or the other possibility is that your system is not auto-loading the usb driver.  Let's check on that too.  Enter in a terminal:
```
lsmod | grep wacom
```
You should see 'wacom' in the terminal followed by some numbers.

When I put in that Ismod thing, it just went to kurtless@kurtless, etc, and no numbers popped up, just for the sake of checking, I went through step 2 again, here is all of my proceedings: 


```
kurtless@kurtless-desktop:~$ wget [http://xorg.freedesktop.org/releases/individual/util/util-macros-1.8.0.tar.bz2](http://xorg.freedesktop.org/releases/individual/util/util-macros-1.8.0.tar.bz2)
--2011-05-27 16:46:15--  [http://xorg.freedesktop.org/releases/individual/util/util-macros-1.8.0.tar.bz2](http://xorg.freedesktop.org/releases/individual/util/util-macros-1.8.0.tar.bz2)
Resolving xorg.freedesktop.org... 131.252.210.176
Connecting to xorg.freedesktop.org|131.252.210.176|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 63867 (62K) [application/x-bzip2]
Saving to: `util-macros-1.8.0.tar.bz2.2'

100%[===================================>] 63,867      5.94K/s   in 11s     

2011-05-27 16:46:33 (5.94 KB/s) - `util-macros-1.8.0.tar.bz2.2' saved [63867/63867]

kurtless@kurtless-desktop:~$ sudo cp /usr/share/aclocal/xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4.bak
[sudo] password for kurtless: 
kurtless@kurtless-desktop:~$ sudo cp /usr/share/aclocal/xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4.bak
kurtless@kurtless-desktop:~$ tar xjvf util-macros-1.8.0.tar.bz2
tar: Record size = 8 blocks
util-macros-1.8.0/
util-macros-1.8.0/xorg-macros.pc.in
util-macros-1.8.0/COPYING
util-macros-1.8.0/aclocal.m4
util-macros-1.8.0/Makefile.am
util-macros-1.8.0/missing
util-macros-1.8.0/xorgversion.m4
util-macros-1.8.0/configure
util-macros-1.8.0/xorg-macros.m4.in
util-macros-1.8.0/configure.ac
util-macros-1.8.0/Makefile.in
util-macros-1.8.0/ChangeLog
util-macros-1.8.0/README
util-macros-1.8.0/install-sh
util-macros-1.8.0/INSTALL
kurtless@kurtless-desktop:~$ cd util-macros-1.8.0
kurtless@kurtless-desktop:~/util-macros-1.8.0$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating xorg-macros.pc
config.status: creating Makefile
config.status: creating xorg-macros.m4
kurtless@kurtless-desktop:~/util-macros-1.8.0$ make
make: Nothing to be done for `all'.
kurtless@kurtless-desktop:~/util-macros-1.8.0$ sudo make install
make[1]: Entering directory `/home/kurtless/util-macros-1.8.0'
make[1]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/aclocal" || /bin/mkdir -p "/usr/share/aclocal"
 /usr/bin/install -c -m 644 'xorg-macros.m4' '/usr/share/aclocal/xorg-macros.m4'
test -z "/usr/share/util-macros" || /bin/mkdir -p "/usr/share/util-macros"
 /usr/bin/install -c -m 644 'INSTALL' '/usr/share/util-macros/INSTALL'
test -z "/usr/share/pkgconfig" || /bin/mkdir -p "/usr/share/pkgconfig"
 /usr/bin/install -c -m 644 'xorg-macros.pc' '/usr/share/pkgconfig/xorg-macros.pc'
make  install-data-hook
make[2]: Entering directory `/home/kurtless/util-macros-1.8.0'
rm -f /usr/share/aclocal/xorgversion.m4
make[2]: Leaving directory `/home/kurtless/util-macros-1.8.0'
make[1]: Leaving directory `/home/kurtless/util-macros-1.8.0'
kurtless@kurtless-desktop:~/util-macros-1.8.0$ cd ..
kurtless@kurtless-desktop:~$ cd ./Desktop
kurtless@kurtless-desktop:~/Desktop$ wget [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2)
--2011-05-27 16:51:09--  [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2)
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2/download](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2/download) [following]
--2011-05-27 16:51:19--  [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2/download](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2/download)
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2?r=&ts=1306540282&use_mirror=cdnetworks-us-2](http://downloads.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2?r=&ts=1306540282&use_mirror=cdnetworks-us-2) [following]
--2011-05-27 16:51:24--  [http://downloads.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2?r=&ts=1306540282&use_mirror=cdnetworks-us-2](http://downloads.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2?r=&ts=1306540282&use_mirror=cdnetworks-us-2)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://cdnetworks-us-2.dl.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2](http://cdnetworks-us-2.dl.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2) [following]
--2011-05-27 16:51:31--  [http://cdnetworks-us-2.dl.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2](http://cdnetworks-us-2.dl.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.11.0.tar.bz2)
Resolving cdnetworks-us-2.dl.sourceforge.net... 174.35.19.12
Connecting to cdnetworks-us-2.dl.sourceforge.net|174.35.19.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 490183 (479K) [application/x-bzip2]
Saving to: `xf86-input-wacom-0.11.0.tar.bz2'

100%[===================================>] 490,183     38.4K/s   in 15s     

2011-05-27 16:52:02 (32.9 KB/s) - `xf86-input-wacom-0.11.0.tar.bz2' saved [490183/490183]

kurtless@kurtless-desktop:~/Desktop$ sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libx11-dev is already the newest version.
libxi-dev is already the newest version.
x11proto-input-dev is already the newest version.
xserver-xorg-dev is already the newest version.
libxrandr-dev is already the newest version.
libncurses5-dev is already the newest version.
xutils-dev is already the newest version.
autoconf is already the newest version.
libtool is already the newest version.
pkg-config is already the newest version.
libudev-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kurtless@kurtless-desktop:~/Desktop$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kurtless@kurtless-desktop:~/Desktop$ tar xjvf xf86-input-wacom-0.11.0.tar.bz
tar: xf86-input-wacom-0.11.0.tar.bz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
kurtless@kurtless-desktop:~/Desktop$ cd xf86-input-wacom-0.11.0
kurtless@kurtless-desktop:~/Desktop/xf86-input-wacom-0.11.0$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc option to accept ISO C99... -std=gnu99
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for doxygen... no
configure: WARNING: doxygen not found - documentation targets will be skipped
checking for rint in -lm... yes
checking for XORG... yes
checking for X11... yes
checking for UDEV... yes
checking whether the linker supports -wrap... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating conf/Makefile
config.status: creating doc/Makefile
config.status: creating doc/doxygen.conf
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating include/Makefile
config.status: creating tools/Makefile
config.status: creating test/Makefile
config.status: creating xorg-wacom.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
kurtless@kurtless-desktop:~/Desktop/xf86-input-wacom-0.11.0$ make
make  all-recursive
make[1]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0'
Making all in conf
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/conf'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/conf'
Making all in doc
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/doc'
Making all in src
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/src'
Making all in man
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/man'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/man'
Making all in include
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/include'
Making all in tools
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/tools'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/tools'
Making all in test
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/test'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/test'
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0'
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0'
make[1]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0'
kurtless@kurtless-desktop:~/Desktop/xf86-input-wacom-0.11.0$ sudo make install
Making install in conf
make[1]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/conf'
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/conf'
make[2]: Nothing to be done for `install-exec-am'.
test -z "" || /bin/mkdir -p ""
test -z "/usr/share/hal/fdi/policy/20thirdparty" || /bin/mkdir -p "/usr/share/hal/fdi/policy/20thirdparty"
 /usr/bin/install -c -m 644 wacom.fdi '/usr/share/hal/fdi/policy/20thirdparty'
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/conf'
make[1]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/conf'
Making install in doc
make[1]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/doc'
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/doc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/doc'
make[1]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/doc'
Making install in src
make[1]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/src'
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/src'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/xorg/modules/input" || /bin/mkdir -p "/usr/lib/xorg/modules/input"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   wacom_drv.la '/usr/lib/xorg/modules/input'
libtool: install: /usr/bin/install -c .libs/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so
libtool: install: /usr/bin/install -c .libs/wacom_drv.lai /usr/lib/xorg/modules/input/wacom_drv.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/lib/xorg/modules/input
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/xorg/modules/input

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/src'
make[1]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/src'
Making install in man
make[1]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/man'
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/man'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/man/man4" || /bin/mkdir -p "/usr/share/man/man4"
 /usr/bin/install -c -m 644 wacom.4 '/usr/share/man/man4'
test -z "/usr/share/man/man1" || /bin/mkdir -p "/usr/share/man/man1"
 /usr/bin/install -c -m 644 xsetwacom.1 '/usr/share/man/man1'
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/man'
make[1]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/man'
Making install in include
make[1]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/include'
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/include/xorg" || /bin/mkdir -p "/usr/include/xorg"
 /usr/bin/install -c -m 644 Xwacom.h wacom-properties.h isdv4.h '/usr/include/xorg'
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/include'
make[1]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/include'
Making install in tools
make[1]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/tools'
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/tools'
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c xsetwacom isdv4-serial-debugger '/usr/bin'
libtool: install: /usr/bin/install -c xsetwacom /usr/bin/xsetwacom
libtool: install: /usr/bin/install -c isdv4-serial-debugger /usr/bin/isdv4-serial-debugger
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/tools'
make[1]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/tools'
Making install in test
make[1]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/test'
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/test'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/test'
make[1]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0/test'
make[1]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0'
make[2]: Entering directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/pkgconfig" || /bin/mkdir -p "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 xorg-wacom.pc '/usr/lib/pkgconfig'
make[2]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0'
make[1]: Leaving directory `/home/kurtless/Desktop/xf86-input-wacom-0.11.0'
kurtless@kurtless-desktop:~/Desktop/xf86-input-wacom-0.11.0$"
```

I can only spot one thing that seems to be adnormal, what is your take on the subject, did I successfully download the right things, and is everything working, or is it supposed to be working?

---

### Post by Favux on 2011-05-27
It looks good.  By the way the reason your uncompress (tar) command failed is you cut off the 2 so you weren't using the correct name.  You had:
```
tar xjvf xf86-input-wacom-0.11.0.tar.bz

```
instead of:
```
tar xjvf xf86-input-wacom-0.11.0.tar.bz2

```

The lsmod command is telling us the usb driver isn't auto-loading.  That happens on some systems.  We can force it to load by adding the module 'wacom' (without the quotes) to the bottom of the list in the modules file in /etc.  So to edit it use:
```
gksudo gedit /etc/modules
```
after you put *wacom* in Save and close and reboot.

---

### Post by Kurtless on 2011-05-27
> **Favux said:**
> It looks good.  By the way the reason your uncompress (tar) command failed is you cut off the 2 so you weren't using the correct name.  You had:
```
tar xjvf xf86-input-wacom-0.11.0.tar.bz

```
instead of:
```
tar xjvf xf86-input-wacom-0.11.0.tar.bz2

```

The lsmod command is telling us the usb driver isn't auto-loading.  That happens on some systems.  We can force it to load by adding the module 'wacom' (without the quotes) to the bottom of the list in the modules file in /etc.  So to edit it use:
```
gksudo gedit /etc/modules
```
after you put *wacom* in Save and close and reboot.

After hours of thought, checking, and applying things.... to things, the tablet finally works! Thank you so much Favux! I really appreciate the time you spent helping me! The word entering of "wacom", DID work, I guess I had a couple things wrong before too, but we found the problem in the end, have a great day! If I have any other problems I will contact you, thank you!!!!!

---

### Post by Favux on 2011-05-27
Great!  I'm happy you got it working.  :)

---

### Post by cracker89 on 2011-05-29
im saving this thread for later use ;) :D

---

### Post by vsbladz on 2011-10-31
Gosh I am having the same damn problem. Saving this thread definitely! I almost gave up.

---

### Post by vsbladz on 2011-11-01
Gawd this is too hard to follow. I might screw my system up.
Is there anyway I can remove everything and re-install from start?
Please don't make me give up.
For the sake of it, what is "Wacom_drv.la"??

Why can't I just simply install a prebuilt driver. I am really getting disappointed. PHAAAAAK!!!!!!!

---

### Post by Favux on 2011-11-01
Hi vsbladz,

If you are using Lucid that's because the BambooPT tablets were still new when Lucid came out and support for them didn't make it into Lucid's default drivers.  Later releases support the original 5 models.  Since Wacom has been releasing new models every October since 2009 we are on our 3rd generation of BambooPT's.  And support for them may be upstream but not yet in a distro.

So what model do you have.  On the sticker on the back of the tablet.  And product ID will be in the output of:
```
lsusb
```
Just post the Wacom line.

What did you do that you might need to remove?  Can't help you with that unless I know what you did.

---

### Post by vsbladz on 2011-11-01
Hi Favux,
I don't know where to start. I downloaded sources and compiled them with 
$./configure 
$make 
$install

I did this with couple versions of drivers without removing previous ones. That's why I need to remove all "Wacom" related out of my system so I can do a clean start. But I don't know how. 
Can Synaptic be used to uninstall?

In one of another set of instructions, it said to install some kernal-pae versions. I just don't know, I have confused myself beyond recover.:(

---

### Post by Favux on 2011-11-01
Unless one of your attempts involved DKMS you should be OK.

No, stuff you compile yourself doesn't register with Synaptic.  PPA's and Deb's do.

Still need your model and the *lsusb* output.

Pae is easy.  Just run:
```
uname -r
```
and the output should tell you what type of kernel you have.  Pae is a kernel modification that allows 32-bit kernels to handle RAM beyond the normal 3.2 GB limit they have.


Edit:  You also haven't yet told me what release of Ubuntu you are using.

---

### Post by vsbladz on 2011-11-01
Apologies Favux,
I will get you all my info tonight when I go home. Hopefully you are online around 7pm (Pacific Time) and after.

I am using Ubuntu 10.04 (Lucid)

---

### Post by vsbladz on 2011-11-01
G'day Favux,
I am using Ubuntu 
10.04 LTS

My kernel version is: 
2.6.32-35-generic

Hopefully you can help me set this up! Thanks heaps dude.

---

### Post by Favux on 2011-11-01
Sure.  In addition to the tablet model # and the *lsusb* command output please run:
```
xsetwacom -V
```
and post the output.

---

### Post by vsbladz on 2011-11-01
Hi Favux
Table : CTL-460


vsbladz@vsbladz-desktop:~$ lsusb
Bus 005 Device 002: ID 056a:00d4 Wacom Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0402:5621 ALi Corp. USB 2.0 Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
vsbladz@vsbladz-desktop:~$ 




vsbladz@vsbladz-desktop:~$ xsetwacom -V
0.10.11
Usage: xsetwacom [options] [command [arguments...]]
Options:
 -h, --help                 - usage
 -v, --verbose              - verbose output
 -V, --version              - version info
 -d, --display "display"  - override default display
 -s, --shell                - generate shell commands for 'get'
 -x, --xconf                - generate xorg.conf lines for 'get'

Commands:
 --list devices             - display detected devices
 --list parameters          - display supported parameters
 --list modifiers           - display supported modifier and specific keys for keystrokes
 --set "device name" parameter [values...] - set device parameter by name
 --get "device name" parameter [param...]  - get current device parameter(s) value by name
vsbladz@vsbladz-desktop:~$

---

### Post by Favux on 2011-11-01
Your CTL-460 or D4 is one of the original BambooPT's that came out in October 2009.  So getting it to work should be relatively straight forward.

Because it is a usb tablet there are two Wacom drivers you need.  The usb kernel driver or wacom.ko and the X driver xf86-input-wacom.

Because the models were new they didn't get added to the 2.6.32 kernel by the time Lucid came out.  So you want to follow the instructions in part I. of the [Bamboo Pen&Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") and install input-wacom-0.11.1 so you can get a wacom.ko that has your model in it.

After that, since you appear to have xf86-input-wacom-0.10.11 (the default Natty version, Lucid's is 0.10.5), your tablet should work.  But some improvement to gestures were recently added so you will probably want to clone the xf86-input-wacom git repository also.  That's part II. a) and c).  And more improvements, such as scroll/zoom are coming.

The one thing is to make sure you have a 10-wacom.conf in xorg.conf.d.  See part III. a).

---

### Post by vsbladz on 2011-11-01
Hi Favux,
I did all according to instructions but the mouse is still doing the same thing as Kurtless', it won't move until I shake the pen for few sections. 
Also my "10-wacom-conf" is totally empty. There's nothing in there.

---

### Post by Favux on 2011-11-01
So what you need to do is create one with:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
And copy and paste the contents of the sample wacom.conf into it and reboot.  That's a bug in Lucid that's been there for months.  After a few months an update in Lucid removed the 10-wacom.conf and it hasn't come back.  I posted the bug report on Launchpad months ago and no response.

---

### Post by vsbladz on 2011-11-01
WOW!!! LOL!!! Thank You So much Favux!! You have no idea what I went through dude...lol!!!
It WORKS now!!
Thanks so much man!!!

---

### Post by Favux on 2011-11-01
Great!  Nice work.  :D

Sorry I spaced with the stuff about gestures.  You have a Pen of course.

---

### Post by pieman711 on 2011-11-07
Thanks Favux for all the help! Your how to is excellent and you clearly are a fountain of Tablet knowledge! I was having the same problem as the other two with the mouse not moving after the stylus has been clicked.  I think the thing that was causing the problem for all three of us was simply the missing conf file. Could you put that in Bold in the how to or at the top or something just so anyone else following it could try in first and save a lot of compiling etc :)

I was using the ppa mentioned at the start of your how-to but switched to your full method when trying to fix this problem. I haven't set up the git clone bit yet (IIIc). Would you recommend going back to the PPA or using git to keep up to date? If it's the former how do I cleanly uninstall everything from the how to in order to just go to the PPA?

I'm going to write a letter to my local MP (I'm in England asking for Nov 7th to be Favux appreciation day. I'll let you know how I get on.

---

### Post by Favux on 2011-11-07
Hi pieman711,

Thank you.  I'm sure the MP will get right on it!  :)

I'd have to know what tablet you have and which PPA you used.  Then I'd have to check on whether or not the PPA has been updated.  If the one you used installed a wacom.ko dkms (check /usr/source) then that has to be removed first.  The PPA should show up in Synaptic Package Manager so try removing it through Synaptic.

Maybe I should place the missing 10-wacom.conf somewhere prominent.  I just never thought it would go on this long.  I finally got some activity on my Launchpad bug:  [https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/770082](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/770082)  It would be good if you and anyone else affected posted on it or at least click the "it affects me" option when signed in.

---

### Post by pieman711 on 2011-11-07
It's the wacom pen and touch (ctl-460) I was using to doctormo ppa but turned it off and uninstalled the package before using your how to. I'll go and register my vote for the bug now.

---

### Post by pieman711 on 2011-12-03
I've upgraded my kernel so the driver has stopped working again. What system would you recommend so I didn't have to recompile the driver every time I upgrade teh kernel? The PPA? Also I'm having a similar problem with my wireless card. From lspci it says:
02:08.0 Network controller: RaLink Device 3060

and from lshw:
           *-network
                description: Wireless interface
                product: RaLink
                vendor: RaLink
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: ra0
                version: 00
                serial: 80:1f:02:0f:43:1f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 ip=192.168.0.12 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
                resources: irq:16 memory:efee0000-efeeffff

I'm using the driver called "DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217" and it complies fine and runs without problem. Its just a ball ache reinstalling it every time I upgrade teh kernel

---

### Post by Favux on 2011-12-03
Hi pieman711,

Well, that's what dkms (dynamic kernel module support) is for.  See appendix 2 on the [LinuxWacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").

However I would strongly encourage you to read up on dkms before doing anything.  Read the following at a minimum:
[http://manpages.ubuntu.com/manpages/lucid/man8/dkms.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/dkms.8.html)
[https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS)
[https://wiki.ubuntu.com/Kernel/Dev/DKMSPackaging](https://wiki.ubuntu.com/Kernel/Dev/DKMSPackaging)

The key take away message is you want to know how to uninstall the dkms easily, i.e. a command.  Manually uninstalling one is a major pain.  Which is why I don't favor the PPA's that install a dkms for you.  They tend not to explain what they're doing and how to undo it.  So you end up stuck with their wacom.ko (or other kernel module) until your realize it is over writing any other wacom.ko you install until you deal with it.

I find it easier to just recompile.  Takes a couple of minutes once you've done it a couple of times.  Kernel updates don't come through that often other than maybe in the first month or two of a release.  And as you've seen easy to get rid of the results.

---

### Post by pieman711 on 2011-12-03
Ok, I'll bear that in mind. What's the cleanest way to remove some thing you've complied and installed yourself? 
You're right about it not taking too long once you've done it once or twice though, perhaps I'm making a bit of a mountain from a mole hill. I'm using the LTS 10.4 Ubuntu so it gets fairly regular updates. 
Cheers for all the help.

---

### Post by Favux on 2011-12-03
> What's the cleanest way to remove some thing you've complied and installed yourself? 
Depends on if the Makefile of whatever you're compiling has an uninstall.  We used to have a routine for linuxwacom to remove it before compiling a new version to prevent version conflicts.  But since Karmic they put in a new dependency for xserver-xorg-input-wacom, xserver-xorg-input-all.  You have to have one to have the other, and removal of one removes the other.  And you have to have xserver-xorg-input-all installed for the tablet to work.  So now days we just overwrite the previous compile with a new one or by reinstalling the default xserver-xorg-input-wacom package with Synaptic Package Manager or Software Center.

Since it is compiled it isn't registered with Synaptic Package Manager or Software Center so you can't use them to uninstall.  You could register the compile if you used checkinstall, which would also give you a "Deb".  Why I don't use checkinstall is a long story.  Or of course you could figure out the name and locations of the installed files and manually remove them, not recommended.  The default package has a list of those you can look at in Synaptic Package Manager.

---

### Post by hakura11 on 2011-12-26
Hey Favux, 
been reading your forum posts all day but to no avail. 

I have a Wacom Bamboo CTL470/k and, as I'm sure many other people experienced, I can't get it working... YET.

I'm running Ubuntu 10.10,
2.6.35-31-generic

Followed your guide on [all variants] but still doesn't work. 

Have compiled and copied the driver into the correct place.
At first the lsmod | grep wacom didn't show so I found another of your guides to auto-load it.
here is the output:

wacom                  32221  0 

output from lsusb is:

Bus 002 Device 005: ID 056a:00dd Wacom Co., Ltd 
Bus 002 Device 004: ID 064e:a115 Suyin Corp. 
Bus 002 Device 003: ID 147e:1001 Upek 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


the output from xsetwacom -V is:

0.12.0

The model is the pen only one.

Any and all help to get this thing working would be amazing.
The only thing that seems at all alive on the thing is the blue light and the fact that when i move the pen within range it gets brighter, and the fact that my computer recognises that it's plugged in.

Thanks in advance :)

---

### Post by Favux on 2011-12-26
Hi hakura11,

The problem you are having is that the Bamboo CTL470/k will not work on Maverick's 2.6.35 kernel.  Chris Bagwell's support for it only works with the 2.6.38 (Natty 11.04) kernel, because that is the first kernel to have mt.h, the multi-touch header.

Chris' support for the third generation BambooPT's requires mt.h.  He has submitted it to the 3.3 kernel and then backported it to input-wacom-0.12.0, but only for kernels compiled in input-wacom's 2.6.38 folder, i.e. 2.6.38 and 3.0 (Natty and Oneiric).

So the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") input-wacom compile instructions only work in Natty and Oneiric for your model tablet.

---

### Post by hakura11 on 2011-12-27
Ah I see... damn. Thanks for the help dude, I guess I'll update to 11.10 then :'(

Merry Christmas :)

---

