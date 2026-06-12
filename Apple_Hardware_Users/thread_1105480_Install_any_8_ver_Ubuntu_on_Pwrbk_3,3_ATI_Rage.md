---
title: "Install any 8 ver Ubuntu on Pwrbk 3,3 ATI Rage"
date: 2009-03-24
forum: Apple Hardware Users
---

### Post by truerobotech on 2009-03-24
Hello all, thanks for any and all assistance

Im have 7.10 installed my problem is in the last reply to this thread (other replies I have made were edits since no longer a problem or part of this issue).

Machine specs
Machine Name:	PowerBook G4
  Machine Model:	PowerBook3,3
  CPU Type:	PowerPC G4  (2.1)
  Number Of CPUs:	1
  CPU Speed:	667 MHz
  L2 Cache (per CPU):	256 KB
  Memory:	768 MB
  Bus Speed:	133 MHz
  Boot ROM Version:	4.2.9f1


Vid Specs
Chipset Model:	ATY,RageM6
  Type:	Display
  Bus:	AGP
  Slot:	ATI
  VRAM (Total):	16 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x4c59
  Revision ID:	0x0000
  ROM Revision:	113-XXXXX-115
  Displays:
Color LCD:
  Display Type:	LCD
  Resolution:	1152 x 768
  Depth:	32-bit Color
  Built-In:	Yes
  Core Image:	Not Supported
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported

Thanks again

---

### Post by truerobotech on 2009-03-25
(edited since no longer a problem or part of this issue)

---

### Post by truerobotech on 2009-03-27
(edited since no longer a problem or part of this issue)

---

### Post by truerobotech on 2009-03-27
(edited since no longer a problem or part of this issue)

---

### Post by truerobotech on 2009-03-28
Well we can toss all the above post aside.

I have a complete install of 7.10 from the alternate cd.

New problems which I cant find answers to. Boot up is fine but no network devices found. Yet when Im in the network settings it detects both my nic and my wireless. I can enter and try to save a location name but they never show up in the box. I really dont care about the wireless I would prefer wired 

I tried sky2 and it shows in my ls, rebooting after this I am now forced into the initramfs prompt. I get past it by doing the modprobe ide-disk then exit.

Any help with the network problem would be appreciated.

my ifconfig is as follows

userx@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:30:65:1D:84:97  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:65ff:fe1d:8497/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:3 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5471 (5.3 KB)  TX bytes:6973 (6.8 KB)
          Interrupt:57 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by sms0611 on 2009-03-29
I have a feeling the problem is that you have no eth0 which is the default for just about everything.

Have you changed something to disable this?

Why are you running 7.10 I'm using 8.04 (hardy) on my PowerMac G4 without too many problems.

---

### Post by truerobotech on 2009-03-29
Hey Steve

no matter what I did with 8.04 or 8.10 live I ended up with the blank screen video problems. When iused the7.10 cd i can boot in with the video=ofonly but installs always failed

So i moved to the alt disk with each 8 version again bad video problems no matter what I tried. 

I installed 7.10 from the alt disk and it booted fine but that is where the network issues were. 

Same deal no matter what I did no luck. Come to think of it the eth0 showed as my airport, eth1 was the nic.


Ive been kicking this thing for days so with low patience I thought it may be an install problem. Im now trying to set up to boot/install from usb.

Im hung up there trying to copy the cd
  my replay to that post should be a little bit down the main page.

Thanks for the reply.

Also curious did you do anything specific to prep before the install?

---

### Post by sms0611 on 2009-03-29
Hi,

It's quite funny, I first tried to install 7.10 on my machine but could not get it to boot after the instalation, went round in circles for a while too. Then I tried the 8.04 alt disk and it installed and booted first time with only one major problem, no sound, which I have now solved.

The only thing I did was to wipe the hard disk and re-partition every time I installed.

My machine is using an nVida card so may be that's why I didn't have video problems. I'm not hot enough on Ubuntu to offer advice outside of what I have actually done.

Did find this link, don't know if you've seen it but it may help

[http://www.linuxforums.org/forum/ubuntu-help/120520-ubuntu-hardy-heron-8-04-ati-rage-128-a.html](http://www.linuxforums.org/forum/ubuntu-help/120520-ubuntu-hardy-heron-8-04-ati-rage-128-a.html)

Sorry I couldn't be of more help

If you do manage to get hardy installed keep in touch coz i'm finding stuff out every day, as i'm sure you are, and we may be able to help each other out with problems.

Best of luck.

---

### Post by sms0611 on 2009-03-29
One thing I've just noticed you may need the package

xserver-xorg-video-ati

---

### Post by truerobotech on 2009-03-29
Thanks steve,

Ill give it a shot, if the current headache I mean install fails in some manner.

Ive been at this for days.  really close to chucking in the towel and heading back osx. Which would suck but I have other things on my agenda other than learn ubuntu through trial and error.

Ill post back up with any of the results. Again thanks for the article.

---

### Post by sms0611 on 2009-03-29
One interesting point for you.

I've just installed the linux-restriced-drivers-powerpc package to get the latest nvidia drivers and guess what, now my system hangs on boot.

Am trying to rescue it at the moment but it's getting late so may have to continue tomorrow.

Watch this space and I'll let you know how I get on.

---

### Post by truerobotech on 2009-03-29
sorry to hear, how it works out.

I decided to zero fill the drive since a live install failed again.

working the alt cd install now really hope someone answers my usb questions. I only have access to one ppc, my other "production" machine is a intel imac so  no real help there.

let me know on the rescue

---

### Post by sms0611 on 2009-03-30
If you hadn't already guessed my machine is now totally non-bootable (it hangs when trying to switch to GNOME).

I am going to do a complete re-install from scratch.

Luckily I take lots of notes when I'm doing this stuff so it shouldn't be too much of a pain.

What I will do is make detailed step for step notes and post them here when I am done later today. 

I hope this will help you.

---

### Post by sms0611 on 2009-03-30
OK.

Have run through installation about 5 times now (both install and expert) and I think I may have located where the problem is, that doesn't mean I can fix it for you but we can but try.

Let me just check a few things
1) You install 8.04 using the alt disc option install-powerpc
2) When installation is complete the system reboots
3) Doing nothing the system hangs whilst booting

OK so far ?

See if you can do this for me

Boot from CD
boot: rescue-powerpc
start a shell

I need to know the contents of the file

/etc/X11/xorg.conf

It looks like the debian xconfig tool is screwing up and the video device and/or monitor settings are incorrect.

if this is the case it should be fixable with

sudo dpkg-reconfigure xserver-xorg

but hold off on that for a moment whilst I run a few more tests here.

In the meantime have a read of this

[http://www.debianuniverse.com/readonline/chapter/04](http://www.debianuniverse.com/readonline/chapter/04)

---

### Post by sms0611 on 2009-03-30
More info:

As far as I can tell the problem is almost definitely in the xorg.conf file.

Try This:

When the system has 'booted up'

type: ctrl-alt-f1 (this will switch you to a shell)
you will need to log in
then
cd /etc/X11    (note the capital letter X)
sudo cp xorg.conf xorg.orig
sudo cp xorg.conf.failsafe xorg.conf
sudo /etc/init.d/gdm restart (this will restart GNOME)

type: ctrl-alt-f7 (to switch back to GNOME at any time)

see: files.fosswire.com/2008/04/ubunturef.pdf  (section on display)

If this doesn't work we need to edit the xorg.conf by hand.

wait a little while I get my machine back up and I will post the relevant sections. This can be done using nano under the tt1 terminal.

Are we having fun yet?

---

### Post by truerobotech on 2009-03-30
Well some good news, before i saw  your replies I finished up the7.10 install (posting from it now). I think it was fighting with both my hd and the cd. After a good zero fill everything installed.

I still have some video issue to fix but the ofonly works. Sowhile the machine is happy Im taking a backup image and sending it out to my external.

I would rather restore a base install image than redo all the disk problems again.

When i get to the upgrade for 8.04 Ill update the thread.

I wish I would have been able to use the note your provided, hope they help someone.

Thanks
Patrick

---

### Post by sms0611 on 2009-03-31
Hi Patrick,

Glad to hear you've got something up and running.

In the notes I've just made for installing I've written that it is best to disconnect any external devices, why this should be necessary I've no idea but 8.04 won't install when I've got my external (USB) dvd drive plugged in.

I'm still looking into why xorg.conf is screwing up so badly could you post a copy of your xorg.conf so I can have a look and compare it with mine.

I have taken out all Nvidia specific stuff so only the most basic .conf is being used and this seems to work fine. I have also taken out the kernel framebuffering option as this screws up as well.

If you would like a copy of my 8.04 install notes let me know and I'll tidy them up and send them to you.

Best of luck

---

### Post by sms0611 on 2009-03-31
Hi Patrick,

Just come across this you might want to check it out

[http://www.ppclinux.info/boards/4/topics/show/268](http://www.ppclinux.info/boards/4/topics/show/268)

---

### Post by truerobotech on 2009-03-31
Would have replied sooner but for some reason my browsers at work just cycled every time i try to log in.

Well the 8.04 update went in and Im pickled again.

now it just hangs up at running local boot scripts

Im in a recue mode with my 7.10 cd and the 
dpkg-reconfigure xserver-xorg did not work im doing it from root it just gives a message about unknown terminal bterm.

This is killing me. Not really sure how to get into my xorg and send out from terminal Ill have al ook at it and see what i can put in here

---

### Post by truerobotech on 2009-03-31
looking at the thread you pointed to Im not sure how it would help us/me my g4 is not dvi, it has regular vga and an s video. Im probably missing the point.

I was able to get into the xorg file through a rescue 8.4 disk. But from there my knowledge ends.

additionally since I'm in the file through vi every attempt i make to edit it puts in something other than what I want to type

I set the right keyboard in the rescue mode start up.

Unfortunately I have more important things to do then keep wasting time with linux. Im done for tonight at least, if I don't stop I'm going to take a baseball bat this laptop.

Ill check back on the thread in a bit hope your adventures are fairing better than mine, and let me say I really appreciate your input on all this stuff it has moved me along much faster.

---

### Post by sms0611 on 2009-04-01
Hi Patrick,

  Sit down, take a deep breath, count to ten, put the baseball bat away.

  Feeling better ?

   Believe me I know how you feel, I started this whole exercise a couple of months ago simply because I had this dead Apple box which was going into the bin unless I could figure out a way to do something with it. Although I´ve worked with loads of machines and OS´s I´ve never had cause to delve into Apple HW much and my only Unix experience was over 10 years ago (HP and IBM) so I went into this somewhat blind. Luckily, being retired now, I do have lots of time to spare and I´ve needed it just to get where I am now with my system. 

   Unfortunately as far as the graphics card is concerned I am now at an end, I have found out that the nVidia drivers for my card do not work on PowerPC hardware only x86 so that´s me stuffed unless I can find another, supported, card.

   The point of the link that I posted was twofold, firstly this is a forum specifically for PowerPC and Linux so the advice posted there should be much more specific to our configurations/problems, you may do well joining and posting your problems there. Second that they are actively working on getting ATI cards working properly, with some success it seems, so there must be hope for you in solving this problem.

I have included a copy of my xorg.conf at the end of this, as you will see it is the most basic setup possible (except for my swedish keyboard (long story)). I works for me and, as far as I can tell, it should work for you. Try editing with nano in the shell.

One question. When you boot into 8.04 and it hangs did you try
ctrl-alt-f1 to switch to a new tty?
This worked great for me every time I had a boot hang coz it gave me a command line prompt from which to work and edit xorg.conf et al.

if you cannot do this then I suggest that from the rescue shell you try one of the following

sudo nano /etc/modules
and put a # in front of every line which doesn´t have one
this will stop the hardware specific drivers from being loaded
or sudo cp /etc/modules /etc/modules.old
if you cannot edit to achieve the same thing.

Once you can sucessfully switch to a different tty you are almost there because the base system will have loaded properly and then it´s just a question of getting the drivers right.

Finally, I´m glad I have been of at least some moral support for you, I´ve had a lot of good support from these forums when trying to sort out my problems so it is nice to be able to return the favour

Good luck, keep in touch.

Steve

One thing to bear in mind.
The BUSID of the graphics card
use lspci to find it

0000:00:10.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)

it´s the 00:10.0 bit in front but this is in hex so translates to 00:16.0 in my case in xorg.

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"apple"
	Option		"XkbLayout"	"se"
	Option		"XkbVariant"	"mac"
	Option		"XkbOptions"	"lv3:win_switch,compose:ralt"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by truerobotech on 2009-04-01
> **sms0611 said:**
> Hi Patrick,

  Sit down, take a deep breath, count to ten, put the baseball bat away.


Very funny, we are along the same story lines here, my aging g4 tibook was gathering dust and I want to try running boxee from it. Granted it will be slow but better that nothing.

Good news is I can ctrl+alt+f1 and get in through root.

I commented out all items one at a time and rebooted after each, I had the same results. Ive been looking at the xorg.conf file. I need to figure out how to save a copy out to my flash drive through terminal then I can post it here.

I assume is df to get the drive info. then cp /etc/X11/xorg.con /media/sda (or whatever the drive name is for that boot.)

When successful Ill post it
 Thanks again

---

### Post by truerobotech on 2009-04-01
Adding to the sga, I did a dpkg reconfigure and now have a plan jane xorg file. ALso when booting tried to do a video=ofonly.

Trying a few other things before I call it a night

---

### Post by sms0611 on 2009-04-02
Morning Patrick,

That's great that you can get a root terminal, it means that your install is basically OK and it is only the xorg that's causing the problems

to copy stuff out to the flash I think you will have to mount the device first before you can copy.

mount /dev/sda (or whatever)
cp /etc/X11/xorg.conf /dev/sda

Also have a look at the xorg log file in

/var/log/Xorg.0.log (note capital X)

look for any lines starting (EE) (NI) or (??) this should point to whats going wrong.

Hang in there it wont be long now before you're up and running
(famous last words)

I spend 16 hours yesterday trying to find a C/C++/Java Integrated Development Environment that would actually run on this machine so much for cross platform compatability. It seems that the Ubuntu/PowerPC combination is nobodys flavor of the month general support by other people seems to have stopped with 7.04.
I've downloaded and installed Eclipse now, if that doesn't work I'm going to look at switching to a different Linux.

---

