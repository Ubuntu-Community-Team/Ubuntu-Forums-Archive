---
title: "Newbie on Heron"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Louis1611 on 2008-04-20
I'm the biggest newbie to linux you will probably ever meet... But yeah I deleted Vista on my dual boot and replaced it with Ubuntu Hardy Heron this morning and I need some help...

1. How to install stuff? I downloaded a program that will help me access the internet (ndiswrapper), but I don't know how to install it Dx. I click the file "INSTALL" and it comes up with a window called Open Files.

2. How can I change my screen resolution? I don't want to look at a 800x600 resolution when my monitor is a 22" widescreen Samsung ;_;. Theres no other options under System>Preferences>Screen resolution apart from 600x480 :(

---

### Post by Feelout on 2008-04-20
It seems that you have downloaded a source package - traditional unix way to distribute apps, but it is defenetly not best in Ubuntu. Software in Ubuntu (and Debian) is distributed in .deb packages, and most on them are located in so-called repositories. But you don`t need to download them manually most times - in applications menu (top left corner of screen) click last entry (add/remove applications). It  will show you list of software which is avaliable now. Pick a category, tick apps you want and click Apply changes. Ubuntu will download and install everything automatically.

---

### Post by TeoBigusGeekus on 2008-04-20
1) To install programs
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")
Ndiswrapper is a piece of software that will help you use windows drivers in Ubuntu. When asked to open files, it probably wants you to find the drivers for a particular piece of hardware which does not work normally with Ubuntu.
Before using ndiswrapper, however, why don't you share with us the specifications of your internet connection (modem? router? wireless?) and perhaps we could give you a more solid alternative...

2) Have you installed the Restricted drivers for your graphics card? Probably not, since you can't access the internet yet. 
Solve your network problem first and then we can take a look at your graphics problem.
By the way, what is your graphics card model?

---

### Post by sayakb on 2008-04-20
1. What is the package format? If you want to install anything, just open a terminal and type:
```
sudo apt-get install packagename
```

2. Looks like you have an extra GPU. Goto System->Administration->Restricted driver manager and check the Graphics which shows "Not in use". That would download and install a graphics driver and you would be able to have full resolution.

EDIT: Wow.. 3 replies @ the same time :D :D

---

### Post by ajgreeny on 2008-04-20
Very brave!  As a new linux user you might just have been better to dual boot for the time being, but to try and help you out a bit, let's see what hardware you've got, particularly your graphics card and network adapter (wireless or cabled ethernet).  It may be as simple as enabling restricted drivers, which in Gutsy is possible with the right hardware by going to System>>Administration>>Restricted Drivers Manager,  but it may be somewhere else in Hardy.  Have a look around and see if you can find it and get anything working better.

---

### Post by Louis1611 on 2008-04-20
I have a nVidia GeForce 7 series graphics card
I am trying to connect to my BT Home Hub wireless router (sucks, no need to point it out I already know lmao) via a Linksys WUSB54GS wireless adapter.
Thank you everyone for helping me :D

---

### Post by TeoBigusGeekus on 2008-04-20
Do you have access to internet?

---

### Post by shahrc on 2008-04-20
I have just installed Kubuntu Hardy Heron ths morning to test. I am also having broadcom wifi card which need ndiswrapper to run the wireless. This what you need to do.

[LIST=1]
[*]Install Ndiswrapper " sudo apt-get ndiswrapper" in terminal
[*]Copy your wifi card window driver *.inf and *.sys
[*]Navigate to the folder where you saved your *.inf & *.sys
[*]sudo ndiswrapper -i *.inf
[*]modprobe ndiswrapper
[*]blacklist bcm43**
[*]reboot your pc
[/LIST]

I do not know why, but comparable to my prev ubuntu 7.10, the wireless signal is far more powerful than on  thus kubuntu 8.04. 

Best of luck...:)

---

### Post by Louis1611 on 2008-04-20
On my laptop yes, not on my PC running Ubuntu.

EDIT:^^Problem on the 1st Step!! xD
E: Invalid operation ndiswrapper...

---

### Post by TeoBigusGeekus on 2008-04-20
Let ndiswrapper alone for the time being...
Go to this page
[https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460]("https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460")
and download the 

wicd_1.4.2-1-all.deb  

file. Transfer it to your Ubuntu machine and double click it. It will be automatically installed.
[http://ubuntuforums.org/showthread.php?t=705391&highlight=confused+noob+with+network]("http://ubuntuforums.org/showthread.php?t=705391&highlight=confused+noob+with+network")

---

### Post by Louis1611 on 2008-04-20
Oh for christs sake will nothing go right for me?
I double clicked your file and I get "Error: Conflicts with installed package 'network-manager'" under status.

---

### Post by TeoBigusGeekus on 2008-04-20
Go to the thread I gave you.

---

### Post by Louis1611 on 2008-04-20
Rite its installed, how do I connect to my router?
EDIT: Before you say to read the topic again, I did, I opened WICD but i'm not getting any wireless networks in range, don't know why...

---

### Post by TeoBigusGeekus on 2008-04-20
Go to Applications->Internet->Wicd to launch it.

---

### Post by Louis1611 on 2008-04-20
Done that (you must have been replying during my edit...), i'm not getting any wireless networks in range.

---

### Post by TeoBigusGeekus on 2008-04-20
Ok, then we will try again to install ndiswrapper.
Visit this page
[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=573476]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=573476")
to download the tar.gz file.
Transfer it to your linux machine and double click it. Extract its contents
(ndiswrapper-1.52 folder)
to your desktop.
Open a terminal and type
```
cd /home/yourusername/Desktop/ndiswrapper-1.52
```
Are you with me so far?

---

### Post by Louis1611 on 2008-04-20
Yep, done that. I got a line saying myuser@mycomputer:~/Desktop/ndiswrapper-1.52$

---

### Post by TeoBigusGeekus on 2008-04-20
Excellent! Now type
```
sudo make uninstall
```
then
```
sudo make
```
and then
```
sudo make install
```

There is a file in the folder which explains everything
[HTML]The instructions below explain how to install ndiswrapper. This is
rather short version; more details about installation,
troubleshooting, FAQ etc. can be found in the Wiki at

http://ndiswrapper.sourceforge.net/wiki

Prerequisites 
=============

You need a recent kernel, at least 2.6.6 or 2.4.26, with header files
for the kernel. Make sure there is a link to the kernel source from
the modules directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

Downloading 
===========

Download the latest version of the ndiswrapper sources from here and
extract it with the command

  tar zxvf ndiswrapper-version.tar.gz

This will create ndiswrapper-version directory. Change to that
directory and run

  make uninstall
  make

Login as root and run
  make install

Install Windows driver 
======================

If this is the first time you install ndiswrapper, you need to install
Windows driver for Windows XP (in some cases Windows NT or Windows
2000 may also work). First, get a Windows driver that is known to
work. See http://ndiswrapper.sourceforge.net/wiki/List for status
about the device for which you are installing Windows driver. For
this, you need to identify device ID with

  lspci -n

if it is PCI device or

  lsusb

if it is USB device.

Then lookup in that List for the device ID and if a driver is known to
work, get that driver. Occassionally, Windows driver on the CD or your
Windows partition may work, but if it doesn't, don't complain - get a
known-to-work driver.

Many Windows drivers are distributed either as zipped files or cab
files. Zipped files, even if they are .exe files, can be extracted
with 'unzip' in Linux; cab files can be extracted with combination of
'cabextract' and 'unshield' programs.

Once the driver has been unpacked, locate .inf and .sys files. If
necessary, move these files so both .inf and .sys are in the same
directory. Some drivers also come with firmware files, such as
fwrad16.bin etc. These files also should be in the same
directory. Then install the Windows driver with

  ndiswrapper -i driver.inf

This installs .inf file and required .sys and .bin files. Now, see if
installation of Windows driver is "valid" with

  ndiswrapper -l

This should report

"driver present, hardware present"

for the driver installed and if that driver is for the device that is
already in the system. If device is not present, it should report

"driver present"

If not, the Windows driver has not been installed properly.

Now load ndiswrapper module with

  modprobe ndiswrapper

If everything worked properly, this should initialize 'wlan0' wireless
device, which can be configured with wireless tools, such as
'iwconfig', 'wpa_supplicant' etc.
[/HTML]

---

### Post by Louis1611 on 2008-04-20
Sorry to be so thick skulled but... that makes absolutely no sense to me, that readme file ^^;
Sorry :S if anyone can explain it to me step by step?

---

### Post by TeoBigusGeekus on 2008-04-20
Have you run the make uninstall, make and make install commands?

---

### Post by Louis1611 on 2008-04-20
Yes, thats all done.

---

### Post by TeoBigusGeekus on 2008-04-20
Do you have the window$ drivers for your wireless adapter?
If not, then download them from the internet - they should contain an .inf file.

---

### Post by Louis1611 on 2008-04-20
Yeah I have them what do I do with the .inf file?

---

### Post by TeoBigusGeekus on 2008-04-20
Copy the whole folder of your win drivers to you Ubuntu machine, your desktop for example.
Navigate to it with terminal
```
cd /home/yourusername/Desktop/windriversfolder
```

If your .inf file is named linksys.inf, then type
```
sudo ndiswrapper -i linksys.inf
```

If all goes well and no error messages are displayed, then type
```
ndiswrapper -l
```
to see if your adapter has been recognised.

EDIT:
You should have the whole package of the drivers on your Ubuntu machine, not just the .inf file.

---

### Post by Louis1611 on 2008-04-20
I got the error message "sudo: ndiswrapper: command not found". So much for "Linux for human beings" ~_~

---

### Post by TeoBigusGeekus on 2008-04-20
> **TeoBigusGeekus said:**
> Excellent! Now type
```
sudo make uninstall
```
then
```
sudo make
```
and then
```
sudo make install
```



These commands, are you sure they didn't give you any error messages?

---

### Post by Louis1611 on 2008-04-20
Not that I can remember, should I try again?

EDIT: Checking the applications list, ndiswrapper isn't there...

---

### Post by TeoBigusGeekus on 2008-04-20
Yeah, do that...
It seems that ndiswrapper wasn't installed.

EDIT:
Never mind it not showing up in the applications list.

---

### Post by Louis1611 on 2008-04-20
It looks like the whole installation is made up of error messages O_o. That isn't normal is it? Anyway I "reinstalled" it. Now should I try the .inf file thing?

---

### Post by TeoBigusGeekus on 2008-04-20
Try
```
ndiswrapper -l
```
first (that's -L) to see if it is installed first.
Then do the inf thing...

---

### Post by Louis1611 on 2008-04-20
OH FOR CHRISTS SAKES I WAS DOING -i NOT -L!! -.-

EDIT: It isn't installed.

---

### Post by TeoBigusGeekus on 2008-04-20
I don't get it, what messages does it give you when you type ndiswrapper -l?
Also, reinstall (make unistall,make and make install) and post us EVERYTHING the terminal gives you.

---

### Post by Louis1611 on 2008-04-20
I get "ndiswrapper is not installed on this machine" or something to that effect. I have PMed you some of what was in my terminal when I do the make uninstall, make and make install stuff. I couldn't fit it all in, it wouldn't even fit in 5 PMs (5000 char limit)

---

### Post by TeoBigusGeekus on 2008-04-20
For god's sake...
Go to system->administration->synaptic package manager
and do a search for gcc.
Are the packages cpp and gcc installed on your machine? (They should be checked if so)

[HTML]louis@louislinux:~$ cd /home/louis/Desktop/ndiswrapper-1.52
louis@louislinux:~/Desktop/ndiswrapper-1.52$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko
louis@louislinux:~/Desktop/ndiswrapper-1.52$ sudo make
make -C driver
make[1]: Entering directory `/home/louis/Desktop/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/louis/Desktop/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: Leaving directory `/home/louis/Desktop/ndiswrapper-1.52/driver'
make -C utils
make[1]: Entering directory `/home/louis/Desktop/ndiswrapper-1.52/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before â&#8364;&#732;size_tâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;load_fileâ&#8364;&#8482;:
loadndisdriver.c:67: error: â&#8364;&#732;size_tâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected â&#8364;&#732;;â&#8364;&#8482; before â&#8364;&#732;sizeâ&#8364;&#8482;
loadndisdriver.c:68: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)[/HTML]

---

### Post by Louis1611 on 2008-04-20
Yup, they are both installed. At least, I think they are. They have green blank boxes, under properties it says "Status: Installed". So yeah O_o

---

### Post by TeoBigusGeekus on 2008-04-20
Allright, while you are in the ndiswrapper folder, type
```
./configure
```
and post the results.

---

### Post by Louis1611 on 2008-04-20
bash: ./configure: No such file or directory

---

### Post by Louis1611 on 2008-04-20
This is probably against the rules but i'm going to bump this up, I really need help here. My XP partition screwed up as well so I need to get myself up and running on Ubuntu ASAP...

---

### Post by TeoBigusGeekus on 2008-04-20
Sorry for the delay, I was tied up.
So, there is no configure script for the package.
I'm truly sorry mate... I don't know what to say...

This is what I got when I compiled ndiswrapper
[HTML]teo@teo-desktop:~/Desktop/ndiswrapper-1.52$ sudo make
make -C driver
make[1]: Entering directory `/home/teo/Desktop/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/teo/Desktop/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  LD      /home/teo/Desktop/ndiswrapper-1.52/driver/built-in.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/crt.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/hal.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/iw_ndis.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/loader.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/ndis.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/ntoskernel.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/ntoskernel_io.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/pe_linker.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/pnp.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/proc.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/rtl.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/wrapmem.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/wrapndis.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/wrapper.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/usb.o
  CC [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/divdi3.o
  LD [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/teo/Desktop/ndiswrapper-1.52/driver/ndiswrapper.mod.o
  LD [M]  /home/teo/Desktop/ndiswrapper-1.52/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: Leaving directory `/home/teo/Desktop/ndiswrapper-1.52/driver'
make -C utils
make[1]: Entering directory `/home/teo/Desktop/ndiswrapper-1.52/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/teo/Desktop/ndiswrapper-1.52/utils'
teo@teo-desktop:~/Desktop/ndiswrapper-1.52$ 
[/HTML]

The only things I can suggest are
1)Try to connect with your router with a wired connection in order to update Hardy Heron and then try your luck again with ndiswrapper and wicd.
2)Re-download the ndiswrapper package again. There is a - slight - chance that the package was corrupt. 

I am trully sorry for wasting your time...

---

### Post by Louis1611 on 2008-04-20
Don't worry, theres no problem, I had to reinstall XP during that time anyway lmao. It got corrupted during my Ubuntu installation for some reason, which pisses me off because all my homework and art was on there but oh well.

---

### Post by TeoBigusGeekus on 2008-04-20
I feel kinda bad for this...
Unless someone else has something to suggest, why don't you do a fresh install of Ubuntu as well?
This time, if you can, connect your pc with your router with a networking cable, so that the installation can download all available updates.

---

### Post by Louis1611 on 2008-04-20
Well, err, you see... I kind of wiped my whole hard drive O_o

My dual boot works perfectly now, now I just need to do the ndiswrapper stuff.

Over the past two days, the amount of times i've installed a new OS on my laptop AND my PC counts to about 10... Thats more than I had done in my whole LIFETIME let alone two days!!

---

### Post by TeoBigusGeekus on 2008-04-20
Can you do a wired connection with your router?

---

### Post by SunnyRabbiera on 2008-04-20
just remember wireless can be a little shaky in linux, its not our fault as most drivers out there only have windows in mind.
I know I had a hell of a time getting wireless working on my other computer so dont feel bad, getting ndiswrapper working can be a real pain in the butt.
I speak from experience

---

### Post by TeoBigusGeekus on 2008-04-20
> **SunnyRabbiera said:**
> just remember wireless can be a little shaky in linux, its not our fault as most drivers out there only have windows in mind.
I know I had a hell of a time getting wireless working on my other computer so dont feel bad, getting ndiswrapper working can be a real pain in the butt.
I speak from experience
Phew, that's a consolation...
I feel like a total **** to the eyes of Louis1611. But I'm gonna help him/her as much as I can...

---

### Post by Louis1611 on 2008-04-20
Re, Geekus, then pirasie!!

Hehe ;) Its fine you don't have to feel bad, I am on top of the world after getting my display drivers working on XP, my dual boot working, and soon internet on Ubuntu :D
A wired connection isn't possible i'm afraid.

---

### Post by SunnyRabbiera on 2008-04-20
Hey i spent two weeks experimenting with wireless getting it to work, it was very trial and error.

---

### Post by SunnyRabbiera on 2008-04-20
> **Louis1611 said:**
> Re, Geekus, then pirasie!!

Hehe ;) Its fine you don't have to feel bad, I am on top of the world after getting my display drivers working on XP, my dual boot working, and soon internet on Ubuntu :D
A wired connection isn't possible i'm afraid.

well maybe you can use your dualboot to your advantage, to download and install what you need via windows and put them on your linux drive and cross your fingers.
but have you ever considered giving another distro a shot, sometimes ubuntu can be a little shoddy with wireless.
You can give linux mint a shot, its based on ubuntu but doesnt share a lot of its issues...
The current mint will be a little behind Hardy though in most of its stuff but if you can deal without bleeding edge stuff it might be worth a try.
Plus Mint has ndiswrapper enabled by default though its a older version, but it might just work who knows

---

### Post by dark_harmonics on 2008-04-20
If you can get your ubuntu connected long enough to download the right files, you should be good to go. After you have a good connection (wired would be required for this) You type:

```

sudo apt-get install ndiswrapper*

```

I think this is why they were asking if you could get a hardwire connection. Otherwise you will have to manually compile from source which typically requires the build-essential package. What makes ubuntu great is that it has a HUGE repository of stuff that you can just add without any compiling, but that is useless without a connection.

**If you already have the inf and sys files for your network card (or the driver files) on a usb stick or CD you dont need this section:**

Since you already have XP working properly you can grab the .inf and .sys files from there. Just boot into your XP and do the following:

Right click your My computer icon (it may just be under the start menu) and go to manage.
Click the device manager option on the left and in the right hand pane find network
under there your wireless card should be listed. 

Use the name of this card to find and download the drivers (google search or go to the manufacturer's website). Make sure the drivers are exploded or you will need additional steps in ubuntu (cabextract works for that in ubuntu). Put them on a usb stick, CD, or network accessible location and boot into ubuntu. 

**If you already have the files start here:**
Put the files in a directory organized to your preference (i make a Programs directory from my home dir and put it under ndiswrapper subfolder for my organizational purposes. )

Open that folder in a terminal window and type:
```

sudo ndiswrapper -i driverinfname.inf

```

hope some of this helps!

---

### Post by TeoBigusGeekus on 2008-04-20
> **Louis1611 said:**
> Re, Geekus, then pirasie!!


Of course it does pirasei!!! I'm totally angry now :evil:

The strange thing in your case is that ndiswrapper refuses to _install_, let alone work. 

Have you tried to install other packages from source? Did it go smoothly, or did you have similar errors?

EDIT: You ain't Greek, are you?

---

### Post by climatewarrior on 2008-04-20
What wireless card do you have?

---

### Post by TeoBigusGeekus on 2008-04-20
> **Louis1611 said:**
> I have a nVidia GeForce 7 series graphics card
I am trying to connect to my BT Home Hub wireless router (sucks, no need to point it out I already know lmao) via a Linksys WUSB54GS wireless adapter.
Thank you everyone for helping me :D

Enlighten us...

---

### Post by Louis1611 on 2008-04-20
To what? O_o
And i'm Cypriot. Lmao

---

### Post by TeoBigusGeekus on 2008-04-20
Rather replying to Climatewarrior...

---

### Post by climatewarrior on 2008-04-20
This looks like it might help you out [http://ubuntuforums.org/showthread.php?t=516649](http://ubuntuforums.org/showthread.php?t=516649)

---

### Post by climatewarrior on 2008-04-20
If some of you guys know python and are tired of seeing noobs suffer trough this ndiswrapper process you might want to take a look at this project [https://launchpad.net/auto-ndiswrapprer](https://launchpad.net/auto-ndiswrapprer)

---

### Post by Louis1611 on 2008-04-21
That auto-ndiswrapper doesnt have a download, and I want this thing running tomorrow.

---

### Post by Louis1611 on 2008-04-21
Okay I went out and bought a 15 metre ethernet wire, its connected wirelessly. NDISwrapper has been installed, all updates have been downloaded, but WICD is STILL NOT picking up any wireless networks!! I go into my driver folder and do "ndiswrapper -l", then I get
WUSB54GSv2 : invalid driver!
God this is the most long winded process i've ever had to go through in my life, is Linux really this bad with ease of use? Or am I a special case -.-

---

### Post by climatewarrior on 2008-04-21
Did you try this [http://ubuntuforums.org/showthread.php?t=516649](http://ubuntuforums.org/showthread.php?t=516649) ? Oh and Auto-Ndiswrapper is not ready I was just looking for more people to help me build it.

---

### Post by Louis1611 on 2008-04-21
Yes I did, it didn't work. The adapter isn't lighting up for some reason, even though its plugged into my computer. Dunno whats up with that >.>

Can someone also help me with my Resolution trouble? 800x600 is doing my head in.

---

### Post by Louis1611 on 2008-04-22
Can I bump this? >.>

---

### Post by TeoBigusGeekus on 2008-04-22
If you still want to trust me, go to System->Administration->Hardware Drivers and check if the restricted drivers have been enabled on your system.

---

### Post by Louis1611 on 2008-04-23
Why wouldn't I trust you? ?_? I'll try that in about half an hour.

---

