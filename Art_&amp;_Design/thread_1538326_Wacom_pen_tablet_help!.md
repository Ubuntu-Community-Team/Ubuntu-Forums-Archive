---
title: "Wacom pen tablet help?!"
date: 2010-07-24
forum: Art &amp; Design
---

### Post by Kurtless on 2010-07-24
So I just put Ubuntu on my computer, its really amazing and all, but now my tablet isn't exactly working. I've downloaded a Wacom driver in the software center, but it didn't do anything. I went to the Wacom website, and they have a page where they have drivers for Linux, but my delimma is how to set it up.

I'm used to exe stuff on windows, and I've tried to figure things out with Ubuntu but I need some help.

Has anyone had the same problem as me, and would like to help me?

---

### Post by Favux on 2010-07-25
Hi Kurtless,

Welcome to Ubuntu forums!

What wacom tablet do you have (+ model number)?  What release of Ubuntu are you using?

---

### Post by Kurtless on 2010-07-25
> **Favux said:**
> Hi Kurtless,

Welcome to Ubuntu forums!

What wacom tablet do you have (+ model number)?  What release of Ubuntu are you using?

Hey Thanks!

I have a Wacom Bamboo Pen tablet, the model number is CTL-460.
My version of Ubuntu is 10.04 (lucid).

If you can help me, awesome :P

---

### Post by TheStroj on 2010-07-25
I'm guessing you downloaded a .bin file (whatever it is, it should run this way).

Open up terminal (Alt + F2 -> xterm -> hit Enter):

- navigate to the directory containing your 'drivers file' by using command 'cd directory_name' (without quotes)
- run it by using './drivers_file_name' (without quotes ofcourse :D)
- if it says to run with root privilegies, just add sudo in the begining like this

```
sudo ./drivers_file_name
```

Then type your password (it won't show up, don't worry, you're still typing).

If navigating makes problems, move file to home directory because  Terminal navigates to it by default.

---

### Post by Favux on 2010-07-25
Hi Kurtless,

OK, see the [Bamboo HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  Just remember for the .xsetwacom.sh you only need the stylus section, the other three you can delete.

Good luck!

---

### Post by Kurtless on 2010-07-27
So I followed the how to on the Lucid installation thing for the driver I needed, I plugged in my tablet, but it still didn't work! Help?

---

### Post by Favux on 2010-07-27
Hi Kurtless,

Check and see if the new compiled wacom.ko is auto-loading:
```
lsmod | grep wacom
```
If you don't see wacom add it to the bottom of the list in modules in /etc/:
```
gksudo gedit /etc/modules
```
and reboot.

---

### Post by Kurtless on 2010-07-28
I have to be doing something wrong, I think I downloaded a different driver from what I needed before because I found the lucid one after I downloaded the driver. And what did you say about stylus stuff?

I'm new to this Ubuntu thing, sorry.

---

### Post by Favux on 2010-07-28
Hi Kurtless,

Don't worry about being new.  I don't understand what you just said, you have to expand it a little.  And did you try the lsmod stuff I said?  What happened?

Just read/skim through stuff a couple of times so you have an idea about what you're doing.

---

### Post by Kurtless on 2010-08-02
Ok, I think I downloaded a driver for a different version of Linux, so I've heard installing different drivers, thats not made for your system, might stall the installed driver, the one I want to work.

I've done I think, everything you've said, I just, am not very good at this I guess. Maybe I'll read over it a couple more times, maybe one time, it'll make sense.

---

### Post by digitalis_vulgaris on 2010-08-02
@Kurtless What "but now my tablet isn't exactly working" means? You can move cursor, but it doesn't have pressure sensitivity in GIMP? Or it's not working at all?

---

### Post by Kurtless on 2010-08-03
Its not working at all.

---

### Post by Farmer of Bricks on 2010-08-11
Kurtless, a very easy set of instructions can be found at [http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/]("http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/"). Follow the instructions given there:

```
First, install some compiling tools and header files:
[CODE]sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
```

Next, download the latest linuxwacom driver (0.8.8-8 at the moment of writing):
```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.8-8.tar.bz2
```

Now unpack, configure compile and install it:
```
tar -xf linuxwacom-0.8.8-8.tar.bz2
cd linuxwacom-0.8.6
./configure --enable-wacom
cd src/2.6.30/ 
make
sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/
sudo rmmod wacom
sudo modprobe wacom
```[/CODE]
sudo rmmod wacom will barf at you, saying something like "module not found". That's good; it means that your Wacom driver is not enabled. The next line enables it. 

I performed this instructionset today, and it worked immediately, giving me mouse functionality. I haven't gotten pressure sensitivity inyet.

If you want your wacom driver to be enabled when you start your computer, run the following command and add 'wacom' on its own line at the end of the file. 
```
sudo cp /etc/modules /etc/modules.bak
sudo gedit /etc/modules
```

Your file will look something like this in the end:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
sbp2
wacom

```

This should work for you: I'm using Kubuntu 10.04 as well.

Edit: sources:
[http://ubuntuforums.org/showthread.php?t=1471226&highlight=bamboo](http://ubuntuforums.org/showthread.php?t=1471226&highlight=bamboo)
[http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/](http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/)

---

