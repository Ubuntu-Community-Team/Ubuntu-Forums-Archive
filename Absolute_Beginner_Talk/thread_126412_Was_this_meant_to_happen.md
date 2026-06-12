---
title: "Was this meant to happen?"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by mongoled on 2006-02-06
Another Linux n00b here :) 

So I installed ubuntu, rebooted and only have command line options available to me. Ive spent the last week reading up on solutions to my problem with no avail. 

Is this 'normal' or is there a procedure i need to go through to get a working desktop? For example, i tried using the 'vesa' driver and all I am met with is a blank screen, locked up PC?!?

My brain feel like its been tossed into a scrambling machine, fglxr...xorg...dhkg...ls....mount.....compile....deb.....ram.... so many pieces of information with no coherent order, damn, is there not an easy way for a n00b to get started? Like a resource with **essential** command line prompts and there uses? 

Oh forgot to describe the hardware ive been trying this on, tis A64, x800xt (PCI-E) and ubuntu x64.

Im sure many of you will feel that my post is too short, but really, my head is in a spin, i need some coherent and logical guidance on how i should be looking to troubleshoot my problem. 

If anyone cares to help me, please bear in mind that **i dont have a desktop** all i can use is txt mode.

mong

---

### Post by kaamos on 2006-02-06
If you have not already, try
```
sudo dpkg-reconfigure xserver-xorg
```
and select the "vesa" driver.

---

### Post by mongoled on 2006-02-06
[QUOTE=kaamos]If you have not already, try
```
sudo dpkg-reconfigure xserver-xorg
```
and select the "vesa" driver.[/QUOTE]Hello Kaamos :)
As i said
[quote=mongoled]For example, i tried using the 'vesa' driver and all I am met with is a blank screen, locked up PC?!?[/quote]
Selecting 'vesa' results in locked up system :confused:

Ive tried editing the xorg.cof file with wht i have read here at the forums (i.e. lower resolutions, 8bit, refresh rates etc etc) but nothing seems to work. The only time ive seen a desktop of some kind is using 'VGA' but tht gives me a resolution of 3xx X 2xx

:(

-EDIT-

Right im going to reboot so tht i can enable the drive tht ubuntu is installed on, then i will use **explore2fs** (n00bs, this is an excellent tool you can use to browse the Linux partition from Windows!!! I think this is invaluble as it gave me some insight into the directory structire of the OS) to get a copy of my xorf.conf file and post it here

brb

---

### Post by kaamos on 2006-02-06
Whoops, sorry about that! Hope someone here has better answers for you.

---

### Post by mongoled on 2006-02-06
[QUOTE=kaamos]Whoops, sorry about that! Hope someone here has better answers for you.[/QUOTE]I hope so to, thanxs for trying :)
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 XT (R423)"
	Driver		"vga"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"VP191b"
	Option		"DPMS"
	HorizSync	28-38
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 XT (R423)"
	Monitor		"VP191b"
	DefaultDepth	4
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
Please ignore the 'vga' driver showing this was the last config tht actually gave me a desktop even though it was too small to be able to do anything in it!

Here is a copy of my...darn cant remember were the log file with xserver errors is saved

-EDIT-

ok found it, end of Xorg.0.log
```
(II) Primary Device is: PCI 05:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon X800 XT (R423)".
(WW) ATI:  PCI Mach64 in slot 5:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 5:0:1 could not be detected!
(EE) No devices detected.

Fatal server error:
no screens found

```

---

### Post by ysse on 2006-02-06
[QUOTE=mongoled]Here is a copy of my...darn cant remember were the log file with xserver errors is saved[/QUOTE]

You mean /var/log/Xorg.0.log.

That file would be helpful to see. OK - you found it while i was typing. The warnings make me wonder if your ATI card really is in the slot 5:0:0 like it says in the Device section. Try ```
lspci
``` and see where your X800 is connected.

I see you have an ATI graphics card. There is a "How to" for the ATI 3D drivers [here]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI"). Try that out. I have my ATI 9800 working with the Ubuntu supplied ATI drivers.

Good luck.```

```

---

### Post by mongoled on 2006-02-06
Hiya ysse :)

I edited my above post (yup u were right abt the file i was trying to refer to)

---

### Post by ysse on 2006-02-06
Yes, and I edited my post, too :)

---

### Post by mongoled on 2006-02-06
[QUOTE=ysse]Yes, and I edited my post, too :)[/QUOTE]Hehehhe lag :0

I will reboot and try tht command

brb

Ok i tried tht command and got
```
0000:05:00.0 VGA Compatible Controller: ATI Technologies Inc: Unknown device 5d57
0000:05:00.1 Display Controller: ATI Technologies Inc: Unknown device 5d57
```
I noticed there were alot of things tht said 'unknown device'. How does one go abt scrolling the output of the command, i.e. in windows I would do a '/p'. Whts the equivalent in Linux??

---

### Post by kaamos on 2006-02-06
```
lspci | more
```
So the output of the command lspci is piped to the commad more.

---

### Post by mongoled on 2006-02-06
[QUOTE=kaamos]```
lspci | more
```
So the output of the command lspci is piped to the commad more.[/QUOTE]Hello again, what do u mean by 'piped' :confused: :confused:

---

### Post by Zimmer on 2006-02-06
[http://ubuntuforums.org/showthread.php?t=116427](http://ubuntuforums.org/showthread.php?t=116427)
May provide some clues as to how to get it going..
..and the wiki info for Binary Drivers (fglrx)

---

### Post by kaamos on 2006-02-06
the "|" is used to redirect output of the first command. This can be used for simple things like more or tail (shows last lines), but if can do a whole lot of more complicated stuff as well. For example it can be used to transfer output to a remote machine.

---

### Post by mongoled on 2006-02-06
[QUOTE=Zimmer][http://ubuntuforums.org/showthread.php?t=116427](http://ubuntuforums.org/showthread.php?t=116427)
May provide some clues as to how to get it going..
..and the wiki info for Binary Drivers (fglrx)[/QUOTE]Hi zimmer, this is the problem im getting when ever i try to follow instructions. For a n00b they are always **incomplete**, wht do i mean?

For example the wiki link you provided tell us tht we need to 

'Installation of this driver requires **removing the restricted-modules package in order to work**'

This is **so incompete** for me, how do i remove the restricted module package?? Where is the restrcited module package?? How many things are in the restricted module package?? Fortunately i have managed to answer some of those questions myself. I say fortunately but I am **assuming** that i have answered them!

Is the restricted-module package this one:

/lib/linux-restricted-modules/2.6.12-9.amd64-generic

??

If it is do i do a 'apt-get remove' for each item in the '2.6.12-9.amd64-generic' directory? Whoops i think i can answer this question myself (again im guessing) does this command remove all the items:

apt-get remove linux-restricted-modules-$(uname -r)

??

In the next section i dont understand this bit

'Make sure that you have the **universe and multiverse repositories** enabled' err..come again.....n000000000000b alert :)

then i got a 'sample source list' wht is this, how do i use it, wht does it do??

So many questions....

---

### Post by carlosqueso on 2006-02-06
[QUOTE=mongoled]

Is the restricted-module package this one:

/lib/linux-restricted-modules/2.6.12-9.amd64-generic[/quote] I don't think so, but i'm not sure.

[QUOTE=mongoled]If it is do i do a 'apt-get remove' for each item in the '2.6.12-9.amd64-generic' directory? Whoops i think i can answer this question myself (again im guessing) does this command remove all the items:

apt-get remove linux-restricted-modules-$(uname -r)[/quote]that is correct.

[QUOTE=mongoled]In the next section i dont understand this bit

'Make sure that you have the **universe and multiverse repositories** enabled' err..come again.....n000000000000b alert :)

then i got a 'sample source list' wht is this, how do i use it, wht does it do??
[/quote]  These are related.  Provided you got a good sources.list (and if it's the one that's most places on these forums, it's the right one), type ```
sudo nano /etc/apt/sources.list
``` and make the file that comes up look exactly like the sample.  Then you will have enabled the universe and multiverse repositories, and should be good to follow the rest of the tutorial.
So many questions....[/QUOTE]

---

### Post by mongoled on 2006-02-07
carlosqueso, thanks for your post

You have answered some of my questiosn but i have others, LOL

Im assuming that the fglrx driver is not installed in the beginning, the reason I say this is because I cant find a directory called 'xorg-driver-fglrx', so when i attempt to do a 'apt-get remove xorg-driver-fglrx' i only get an error. 

Also do I have to download the following items?

gcc-3.4
fakeroot

Or are these already part of the distro, if they are part of the distro where are they?!

-EDIT-

Another question, how can i mount my USB stick? Or is this not possible and i have to burn stuff to a CD. The problem for using a CD is tht the CD does not have write access and I dont know wht is the correct procedure to move files/folders, im assuiming tht the USB stick will already have write access

-EDIT x2-

Ok so if i have to download the above files, which do i download? Source, binaries, lib, m32r?????? Man isnt there a resource explaining these things? These are pretty critical for a n00b, the simplest of things **need to be explained**

---

### Post by newuser111 on 2006-02-07
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by mongoled on 2006-02-07
[QUOTE=newuser111][http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)[/QUOTE]
Hello thanxs for your post, but did u even read the thread :confused: , I am already discussing some of the stuff in the link you posted! Im asking for help with stuff regarding tht link

[-(

-EDIT-

Whoops maybe I should follow my own advice (reading...),  LOL

-EDIT x2-

Well i re-read tht link u sent (i must have raed that page several time already) and it does not provide any answers to the questions i asked. In fact it has done the opposite, i now have another question!

Where is the directory '/path/to/directory'??? This is called the 'download' directory, should i assume that its name is indictive of wht it is i.e. a directory for files downloaded from a 'foreign' (as in not part of the distro) medium . Also is this action an automated action, i.e. we dont have to tell the OS to 'download' stuff we want to work with to this directory.

Im sorry but im going to quote this again as it is the details which matter

**the simplest of things need to be explained**

What is common knowledge to you, **is not** common knowledge to me, that is why i am posting in the **Absolute Beginner Talk** because I am an **Absolute Beginner!!**

---

### Post by kaamos on 2006-02-07
the "cd /path/to/directory" means to use the command "cd" to move to the folder where you downloaded the file. So if the file is at /home/*username*/Desktop then the command is "cd /home/*username*/Desktop"

The usb-stick can btw be mounted with
```
sudo mkdir /media/usbstick
sudo mount /dev/sda1 /media/usbstick
```
The number after sda can be different (2,3..) depending on the number of usb-drives you have attached.

---

### Post by mongoled on 2006-02-07
Thanxs again kaamos :)

you have again provided clear answers to some of my questions. Is it wrong for me to feel a little let down when peeps dont properly explain themselves when providing information? The 'cd /path/to/directory' is an excellent example of this. It looked to me that this was an actual directory in the distro, where in fact it was just being used to  provide a structured 'view' of how to browse to a designated folder. Little things like that equate to hrs of **frustration and time wasted** looking for non existant entities!

Now just need answers to my other questions, so that i can give this this thing another go.

---

### Post by Zimmer on 2006-02-07
One last try, then, to get the graphics working.
I quote from the post I linked last time.
[http://ubuntuforums.org/showthread.php?t=116427](http://ubuntuforums.org/showthread.php?t=116427)

(*) except this step: in /etc/X11/xorg.conf:

change:

Section "Device"
Identifier "ATI Technologies, Inc. Radeon X850 Pro (R480)"
Driver "ati"
BusID "PCI:5:0:0"
Option "UseFBDev" "true"
EndSection

to:

Section "Device"
Identifier "ATI Technologies, Inc. Radeon X850 Pro (R480)"
Driver "radeon"
BusID "PCI:5:0:0"
Option "UseFBDev" "true"
EndSection

So try "radeon" instead of "vesa" or "ati" and see if you can re boot into a graphical environment.

If that works you can then begin the process of seeing if 3d is working before trying the many wiki's and how to's on installing fglrx drivers etc.

The one thing I have learned with Linux...my next graphics card will be NVidia..
Regards

---

### Post by mongoled on 2006-02-07
Hi Zimmer,

I will give it a try but im still waiting for an answer to a few questions which I believed would be easy for someone to answer. The questions are related to the information found at the wiki link here

[ Method 2: Generating/Installing Ubuntu packages for the newer 8.20.x drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.20.x_drivers")

I am interested in particular with these two commands

sudo apt-get install gcc-3.4 module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

and specifically 

gcc-3.4 and fakeroot

Are these two programs which i need to download and install? If i dont have to download them and they are part of the distro, where are they? If ive got this completely wrong and these are not programs, can someone please tell me!

I will be sitting here refreshing the page, hopefully i will get an answer to these questions

---

### Post by Zimmer on 2006-02-07
[QUOTE=mongoled]Hi Zimmer,

I will give it a try but im still waiting for an answer to a few questions which I believed would be easy for someone to answer. The questions are related to the information found at the wiki link here

[ Method 2: Generating/Installing Ubuntu packages for the newer 8.20.x drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.20.x_drivers")

I am interested in particular with these two commands

sudo apt-get install gcc-3.4 module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

and specifically 

gcc-3.4 and fakeroot

Are these two programs which i need to download and install? If i dont have to download them and they are part of the distro, where are they? If ive got this completely wrong and these are not programs, can someone please tell me!

I will be sitting here refreshing the page, hopefully i will get an answer to these questions[/QUOTE]
I see from this you are going to try and use the ATI drivers. Good Luck. I am using the xorg fglrx ones.

As for your installation questions, when you get a graphical interface (X) working in Ubuntu you will be able to see the ease of Ubuntu supported software installation through the Synaptic PAckage MAnager.
This is essentialy a graphical interface for the apt-get command. Synaptic provides a list of apps on the screen and you check the box against the ones you want to install/uninstall , click apply and off it goes, job done. It is why a lot of people like Ubuntu.
With only the command line available to you you must issue the apt-get command with details. apt-get will refer to your sources.list file and find the software packages you specify from the repository addresses  in it.
If you want to install stuff that is not 'officially' supported by Ubuntu then often the package is not to be found in the repositories and so you have to get your hands dirty and use other methods to get a package to install, learning a bit more Linux on the way.
The last section of this file explains the rationale far better than I..
file:///usr/share/ubuntu-artwork/home/index.html
I also recommend you have a search through the AMD64 part of the forum for any other hints on these ATI drivers as the deb packages you would be installing according to that how-to are marked 386 ..there may be issues there, but I am not an AMD 64 person so I can't be sure, sorry.

---

### Post by mongoled on 2006-02-08
Hello again,

I think im going to give up on the x86_64 version of ubuntu, i suspect alot of the error I am seeing are down to this. I cant even do a 'sudo' from the 'user' account I get an error ()cantgetnamehost or sommet along those lines. Im downloading the x86 version and will give tht a shot, hopefully i wont be seeing these errors. 

It is really becoming a pain when everything i try doesnt work, I was trying to mount my usb stick today, managed to google the details i needed (command + switches) but when i tried i got the message

volume already mounted or usb stick busy

Its very down heartening that the most 'simple' things fail (i mean 'sudo' should work off the bat!!!). I real hope tht x86 solves these problems

---

### Post by mongoled on 2006-02-10
Well any advice for n00bs is **STAY AWAY FROM x86_64** of Ubuntu!!!!!!

Last night i installed the x86 version and was up and running in less 10 minutes, non-of the sudo errors, just had to use the 'vesa' driver. All the apt-get now makes perfect sense. Wish someone would have pointed out tht 'apt-get' is used as an autonated downloader. Anyhow that is in the past. I dont know why my x86_64 Ubuntu was so borked, i tried installing twice, must be to do with my hardware.  

I wont try x86_64 for at least another six months!!

---

### Post by cogadh on 2006-02-10
mongoled,

I would highly recommend either getting a beginning linux book, checking out one of the many linux newbie sites ([www.justlinux.com](www.justlinux.com) is a pretty good one) and/or reading much of the Ubuntu start guide on this site. A lot of your confusion seems to be related to the "foreign language" experienced linux users sometimes speak (i.e. the "apt-get" question). When I first started using Slackware Linux many years ago, I couldn't live without my "Slackware Linux Essentials" book, it translated the "linux geek speak" into plain English for me and has allowed me to continue using linux everyday (even though I no longer use Slackware).

---

