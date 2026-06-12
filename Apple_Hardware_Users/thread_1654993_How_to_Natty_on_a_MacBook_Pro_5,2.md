---
title: "How to Natty on a MacBook Pro 5,2"
date: 2010-12-29
forum: Apple Hardware Users
---

### Post by thinktyler on 2010-12-29
**Introduction:** I wrote a very extensive and quantified tutorial and informational guide aiming to upgrade the latent information from the wiki's on MacBook Pro 5,2. An accidental toe tap ended with me bumping my head and pressing the X button on firefox. What happen had to be 1 out of a billionth of a chance. So this version will be simple and to the point, until I can muster enough patience to detail it all out again. Please correct any errors.

**sudo apt-get install pommed** - To get backlight keyboard working.
**sudo apt-get install cheese** - To get iSight working.
***sudo apt-get install lirc*** - to get remote working (tested in XBMC)
**[B][B]*[B]sudo apt-get install bluemon***[/B][/B][/B] - Pairs Mighty Mouse and Wireless Keyboard (optional)


System > Administration > Additional Drivers > Enable Nvidia Drivers

**[https://launchpad.net/ubuntu/natty/+package/firmware-b43-installer](https://launchpad.net/ubuntu/natty/+package/firmware-b43-installer)** - To get Wireless working.

System > Administration > Additional Drivers > Enable Wireless STA, or B43 **WILL NOT WORK.** 

You must download the drivers above specifically I used: **[https://launchpad.net/ubuntu/natty/amd64/firmware-b43-installer/4.150.10.5-5](https://launchpad.net/ubuntu/natty/amd64/firmware-b43-installer/4.150.10.5-5)**

**Sensors**
Already work, test by typing in terminal:

**dmesg | grep apple**

Sound works out of box
Bluetooth works out of box

Please feel free to add any additional information. From my experience over the last year, the MacBook Pro gets hot, but setting manual fan speeds are worthless compared to auto fan. Ventilation and lowering brightness are the only ways to keep temp down. 

Final Run down of MacBook 5,2 on Natty. (Most if not all of this information is true on 10.04 meerkat as well)

**Sensors (temps & fans)** - Works (See Above)
**Suspend & Hibernate **- Works
Reboot - Works, long gone are the days of 9.04
**Desktop Effects (Compiz)**- Works with Nvidia Drivers (See Above)
**CD/DVD Writing **- Works
**Bluetooth -** Works *(Optionally, I've had better luck with Bluetooth manager from Ubuntu Software Center, but this is an opinion, as the default works fine)*
**Screen brightness adjustment **- Works
**Keyboard functions (Brightness, volume, etc)** - Works (See Above)
**Sound **- Works
**Microphone** - Works
**External Monitor** - works
**Wireless** (AirPort) - Works (See Above)
**Trackpad** - Works
**Webcam/iSight Works** (See Above)
**Apple Remote Contro**l - Works (See Above)

---

### Post by manang on 2011-01-14
i have installed pommed, but i don't see the light function of my keyboard.
i have a macbook 5,1. i beleave it is the same...

---

### Post by manang on 2011-01-14
i have this output
if you have any idea...thank you

manang@Marconi:~$ sudo pommed
[sudo] password for manang: 
No protocol specified
xcb_connection_has_error() returned true

---

### Post by andresimi on 2011-05-01
How could you install Natty on Macbook 5,2?
I've used bootcamp to shrink MacOsx partition, Refit and Installed Natty 64bits with the Grub on the Linux partition. But, when I try to boot Ubuntu from HD, it stops on a black screen and doesn't start.

Also tryed to put apci=off and maxcpus=1 on the grub, but nothing changes

I've tested 10.04, 10.10 and the same problem ocurs.

Thank ou for the help.

---

### Post by alexmurray on 2011-05-01
Boot with the kernel command line option:

nouveau.noaccel=1

And you should be okay

---

### Post by LuisGMarine on 2011-05-01
Good guide!  I'm also following this on a MacbookPro 5,3 and it's all working like normal.

The only thing is getting used to not using the Command key for everything!  I'm testing out as much as I can right now, everything seems to be working ok.  I have to admit that I was not able to do a fresh install of Ubuntu 11.04 on my machine, so I had to install 10.10 and upgrade from there.  

Trackpad works ok, I'm a bit upset that the 3 finger scroll or 4 finger doesn't work!  But I'm sure there is an app for that.

The last thing is when I run the command for the sensors all of them say "fail" for some reason I don't think that is good, check it out ...

```
illuminati@illuminati-MacBookPro:~$ dmesg | grep apple
[   16.617761] applesmc: IG0CE-&#65533;&#65533;}: read arg fail
[   16.685497] apple 0003:05AC:8242.0001: hiddev0,hidraw0: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:04.0-5/input0
[   17.512551] apple 0003:05AC:0236.0002: input,hidraw1: USB HID v1.11 Keyboard [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input0
[   17.521090] apple 0003:05AC:0236.0003: hidraw2: USB HID v1.11 Device [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input1
[   17.655173] applesmc: key=330 fan=2 temp=19 acc=1 lux=2 kbd=1
[   17.655175] applesmc: init_smcreg() took 50 ms
[   17.678753] input: applesmc as /devices/platform/applesmc.768/input/input6
[   18.068536] applesmc: light sensor data length set to 10
[   43.090654] applesmc: FS! : read arg fail
[  586.223545] applesmc: F1Mn: write arg fail
[  701.913806] applesmc: FS! : read arg fail
[ 1536.873317] applesmc: FS! : read arg fail
[ 1582.161134] applesmc: FS! : read arg fail
[ 2055.108518] applesmc: F0Mn: write arg fail
[ 2341.787165] applesmc: TC0F: read data fail
[ 2558.089298] applesmc: FS! : read arg fail
[ 2804.467595] applesmc: TTF0: read arg fail

```

---

### Post by andresimi on 2011-05-01
> **alexmurray said:**
> Boot with the kernel command line option:

nouveau.noaccel=1

And you should be okay

Thanks for answering.

I put this parametes but unfortunately I still cant boot from HD.
I've installed using ubuntu-11.04-desktop-amd64+mac.iso and netbootin. That&#347; ok to boot from the LivePendrive, but not from HD. 

One thing I noticed was that when I tried 10.10, the black screen was after the Grub. But now, the grub does not show up..

Thanks
Andre

---

### Post by adarkenigma on 2011-05-02
hello, i really want to try 11.04 but after i had bad experience with 10.04 i haven't tried it on my Macbook pro 5,2 ....

what i really want to know is how hot does it run?  can it run on 2000 rpm like snow leopard? 

will someone share their rpm settings?  like does it run okay on 2000 rpm or do we have to go upto 3500 which i think will drain battery like no other

---

### Post by Houdeng on 2011-05-03
> **LuisGMarine said:**
> Good guide!  I'm also following this on a MacbookPro 5,3 and it's all working like normal.

The only thing is getting used to not using the Command key for everything!  I'm testing out as much as I can right now, everything seems to be working ok.  I have to admit that I was not able to do a fresh install of Ubuntu 11.04 on my machine, so I had to install 10.10 and upgrade from there.  

Trackpad works ok, I'm a bit upset that the 3 finger scroll or 4 finger doesn't work!  But I'm sure there is an app for that.

The last thing is when I run the command for the sensors all of them say "fail" for some reason I don't think that is good, check it out ...

```
illuminati@illuminati-MacBookPro:~$ dmesg | grep apple
[   16.617761] applesmc: IG0CE-&#65533;&#65533;}: read arg fail
[   16.685497] apple 0003:05AC:8242.0001: hiddev0,hidraw0: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:04.0-5/input0
[   17.512551] apple 0003:05AC:0236.0002: input,hidraw1: USB HID v1.11 Keyboard [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input0
[   17.521090] apple 0003:05AC:0236.0003: hidraw2: USB HID v1.11 Device [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input1
[   17.655173] applesmc: key=330 fan=2 temp=19 acc=1 lux=2 kbd=1
[   17.655175] applesmc: init_smcreg() took 50 ms
[   17.678753] input: applesmc as /devices/platform/applesmc.768/input/input6
[   18.068536] applesmc: light sensor data length set to 10
[   43.090654] applesmc: FS! : read arg fail
[  586.223545] applesmc: F1Mn: write arg fail
[  701.913806] applesmc: FS! : read arg fail
[ 1536.873317] applesmc: FS! : read arg fail
[ 1582.161134] applesmc: FS! : read arg fail
[ 2055.108518] applesmc: F0Mn: write arg fail
[ 2341.787165] applesmc: TC0F: read data fail
[ 2558.089298] applesmc: FS! : read arg fail
[ 2804.467595] applesmc: TTF0: read arg fail

```
Great to meet a 5,3 user ! I could not install from 11.04 neither ; reading the dvd seemed not easy. 
I am sure we could change the keyboard to use the Command Key ; and I am getting used to the trackpad, even if an Apple-type set up would be nice.
Everything works fine excepted the webcam ; cheese is installed but no webcam is detected.

Do y ou have an idea ?


Thank you

Fred.

---

### Post by JohnAtilano on 2011-05-03
> **andresimi said:**
> How could you install Natty on Macbook 5,2?
I've used bootcamp to shrink MacOsx partition, Refit and Installed Natty 64bits with the Grub on the Linux partition. But, when I try to boot Ubuntu from HD, it stops on a black screen and doesn't start.

Also tryed to put apci=off and maxcpus=1 on the grub, but nothing changes

I've tested 10.04, 10.10 and the same problem ocurs.

Thank ou for the help.

andresimi, I just installed 11.04 64-bit on my MacBook Pro 5,1.  When you boot from the LiveCD and get to the point where you are given the option to "Try Ubuntu, install, etc." Press F6, arrow down to "nomodeset", press enter to place an "x" next to it, press "ESC" then "Try Ubuntu."  Let the system boot completely then install.  Worked like a charm.

Good Luck!

---

### Post by unagimiyagi on 2011-05-10
> **alexmurray said:**
> Boot with the kernel command line option:

nouveau.noaccel=1

And you should be okay


Hi, I've managed to install ubuntu 11 on my macbook pro 5,2.  However, I can't reboot back into the installed ubuntu partition.  Refit analyze partition tables tells me that my tables are synced.  

So I turn off the computer, see refit boot menu, and select Linux.  Then I get that purple screen, select my ubuntu, and then I get a black screen with a _ at the top left and that's it.

Any ideas on how to proceed?

Thanks!

---

### Post by clakes on 2011-05-12
Hi guys!

I've tried to install 11.04 64-bit on my MacBook 5,1 to no avail: can't get it to boot at all.

[...blabla...]

/edit: SOLVED
Some further googling got me to this godsent post:
[http://ubuntuforums.org/archive/index.php/t-1549174.html](http://ubuntuforums.org/archive/index.php/t-1549174.html)

At a quick glance, it looks that 10.6 doesn't like (new) bootloaders to screw with the MBR.
Following those instructions and downgrading GRUB did the trick: happily riding a Perfect Ten now.  =)
Not sure about upgrading to Natty: a clean install on my ext4 partition totally killed my wireless adapter (!?!) although a previous upgrade to 11.04 on another MBP didn't show such a naughty (or... uhm... natty) bug...

---

### Post by unagimiyagi on 2011-05-12
What kind of power optimizations can there be?  I am noticing much less battery life on mine in ubuntu compared to mac os x.  Which mactel-support ppa packages should be installed for the macbook pro 5,2?

Thanks

Edit:  I've decided that 11.04 is not stable enough, or my 5,2 is too old to be worth the hassle right now for ubuntu.  Trying to walk away from low level command line voodoo that I don't understand and is getting me very sidetracked from writing software.
Going back to Ubuntu 10 because of unreliable booting.
Lack the ability to find a fix.  But am now more forgiving of Microsoft for all their supposed incompatibility problems.  It must be a major pain trying to support so many different pieces of hardware.  
First and foremost I need an ubuntu laptop that boots reliably.  It seems that the Lenovo machines are much more compatible right now.

---

### Post by lovalloj on 2011-05-21
Booting Natty, hit 'E' with the first entry selected in GRUB. Then at the bottom of the boot parameters add a new line saying
```
nouveau.noaccel=1
```
This fixed booting on my 5,1. I believe you can also set this parameter while installing from the alternate installation disk. I'm booting 64-bit Natty on my 5,1 stably and reliably.

---

### Post by thinktyler on 2011-05-28
Installing 10.10 and upgrading to 11.04 seems to be the best way to go.

Something is broken with 11.04 and the grub. Downgrading to legacy grub is the best bet.

If your feeling risky try this:

6) Boot from Ubuntu CD and select 'rescue a broken system'
7) continue through setup and get a shell in the installer environment:
8) now, chroot into the existing (unbootable) system
# /mkdir /mnt/r
# mount /dev/sda3 /mnt/r
# mount --bind /dev /mnt/r/dev
# mount --bind /proc /mnt/r/proc
# chroot /mnt/r

9) ** Downgrade grub **. I never expected this to work, but it seems to have done
the trick
# apt-get purge grub-common grub-pc
at the same time, move the /boot/grub folder somewhere else as backup
then install grub legacy:
# apt-get install grub
# update-grub
(do a sanity check that the menu.lst looks like its pointing to the correct place)
# grub-install /dev/sda 
(onto the MBR)

10) reboot.

---

### Post by andresimi on 2011-07-18
I have dualboot with MacOsx and Ubuntu on a Macbook 5,1.
I was trying to update to Natty, and the instalation proccess was ok but when it finished I  couldn't make it boot on ubuntu anymore (it frozened on a black screen only with a flashing "_"). Tried to get back to Maverick but the same problem continued. 

Because I thought it was dued to a firmware update on MacOsx, I didn't touch anymore on Ubuntu partition for 3 weeks.

For my surprise, on last weekend I tried to boot on ubuntu again and it booted normaly. After that, a upgraded to naty via Update Manager and now I have Natty on a Macbook 5,1.

I don't know what happened, but it worked.

---

