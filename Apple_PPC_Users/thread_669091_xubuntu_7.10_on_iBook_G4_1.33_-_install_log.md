---
title: "xubuntu 7.10 on iBook G4 1.33 - install log"
date: 2008-01-16
forum: Apple PPC Users
---

### Post by VERiON on 2008-01-16
[SIZE=6]**intro**[/SIZE]

I've wiped out my OSX install entirely and installed xubuntu on my [iBook G4 1.33 (mid 2005)]("http://support.apple.com/specs/ibook/iBook_G4_Mid_2005.html").
There is a lot of things in OSX that I really liked and with the power and flexibility of open source software I would like to recreate some of them.

Because I'm relatively new to linux, it's a good idea to log my instalation/configuration steps for future instalations.
It won't be a detailed log with lots of descriptions - sorry, I don't have enough spare time to do that.
I just like to share my raw notes with you.

__________________

Be sure to visit links below, where you can find lots of interesting stuff/info.

[xubuntu blog (#1)]("http://xubuntublog.wordpress.com/")
[xubuntu blog (#2) ]("http://xubuntu.wordpress.com/")
[ubuntu PPC FAQ]("https://wiki.ubuntu.com/PowerPCFAQ")

__________________

I assume that: 
- you have xubuntu already installed and all repositories enabled (google to find out how).
- your system is up to date ("sudo apt-get upgrade")
- you should run " sudo apt-get update" (without the quotes) before "apt-get" command (once in a day should be enough)
- text in [code] frames should be typed/pasted in terminal window (in XFCE terminal you can paste with shift-ctrl-V)

__________________

My notes can be applied to Ubuntu install as well (not tested thou). Be sure to replace "mousepad" (xubuntu default editor) with "gedit" (ubuntu default editor) when typing/pasting text in terminal

__________________

ps: my english is not that good so PM me if you find and mistakes

---

### Post by VERiON on 2008-01-16
[SIZE=6]**main**[/SIZE]
____________________________________

[SIZE=4]**wifi with WPA**[/SIZE]

based on [this article (in Polish)]("http://czytelnia.ubuntu.pl/index.php/2007/07/28/wicd/")

1. plug in your ethernet cable and be sure that you have connection to the internet

2. enable restricted driver for your wi-fi card 

      run APPLICATIONS > system > "Restricted Drivers Manager"

    for "Firmware for Broadcom 43xx chipset family" 
    put the tick in "enabled" field

    Close "Restricted Drivers Manager" and restart computer

3. uninstall network manager

```
sudo apt-get --purge remove network-manager
```4. install wicd

```
sudo apt-get install wicd
```5. edit /etc/network/interfaces

```
sudo mousepad /etc/network/interfaces
```delete/comment (#) everything except:

```
auto lo
iface lo inet loopback
```6. save and restart (just to be sure) :D

7. open WICD (under APPLICATIONS > internet) and configure your wifi connection

____________________________________

[SIZE=4]**two fingers scrolling**[/SIZE] [in progress]

1. open xorg.conf in editor
```
sudo mousepad /etc/X11/xorg.co    nf
```

2. find synaptic section
```
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
```

3. copy/paste this:
    ```

	Option		"HorizEdgeScroll"		"0"
	Option		"VertEdgeScroll"		"0"
	Option		"HorizTwoFingerScroll"		"1"
	Option		"VertTwoFingerScroll"		"1"
```

0 - disable
1 - enable

4. fix Firefox horizontal scroll issue

configure Firefox so that it doesn't misinterpret the horizontal scroll: 
- In firefox type in the address about:config. 
- double-click the line mousewheel.horizscroll.withnokey.action and set it to 0 
  (2 is forward and back pages. 1 enables Horizontal scrolling). 
- set mousewheel.horizscroll.withnokey.sysnumlines to true.
____________________________________

[SIZE=4]**install and configure compiz**[/SIZE] [in progress]
based on [this article]("http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/#comment-3623")

1. install

```
sudo apt-get install compiz-core compiz-plugins compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald compizconfig-settings-manager
```

2. set emerald as windows decorator

	run Applications->Settings->Advanced Desktop Effects Settings

	click Window Decoration. In the Command input field, 
	enter "emerald" (without quotes)

3. install dri driver  [if you know better way - let me know]

xubuntu doesn't install dri drivers out of the box, so you have to get one:

- boot ubuntu 7.10 live CD
- copy /usr/lib/dri directory to pendrive (for Radeon 9550 you only need r300_dri.so file in that directory)
- set permissions on directory to "Others: Read & Write"
- boot into your xubuntu
- make "dri" directory in "/usr/lib" (all without quotes)
- "r300_dri.so" file into /usr/lib/dri
- logout and login again

4. run  compiz --replace  (in terminal)

5. make compiz running persistent [in progress]

[INFO] I've skipped compiz (for now) because it was slow, I've noticed that Ubuntu Live CD compiz was a great deal faster - maybe I'll investigate it later
____________________________________

[SIZE=4]**powersaving / overheating**[/SIZE] [in progress]

____________________________________

---

### Post by VERiON on 2008-01-16
[size="4"]**gui**[/size]

---

### Post by VERiON on 2008-01-16
[SIZE="4"]**to-do**[/SIZE]

HARDWARE
- get sleep (suspend-to-ram) working
- configure (o) power buton to show suspend/restart/shutdown menu
- low battery warning

SYSTEM OVERALL SPEED-UP
- [read this guide]("http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/")

SOFTWARE
- install/configure [mac menubar]("http://www.gnomefiles.org/app.php/Mac_Menubar_for_GNOME_and_Xfce")
- flash for Firefox > gnash, swfdec
- MP3/DVD/etc. functionality > check [medibuntu]("http://www.medibuntu.org/")
- find and install good launcher ([OSX Quicksilver]("http://en.wikipedia.org/wiki/Quicksilver_(software)") equivalent) > [Gnome launch box]("http://developer.imendio.com/projects/gnome-launch-box")?
- replace GIMP with GIMPshop

GUI
- replace boot splash image with some king of apple logo
- replace GDM login theme with one that have face browser
- replace status icons (battery, wifi range, etc) with OSX-like symbols

---

### Post by VERiON on 2008-01-16
[SIZE="4"]**research**[/SIZE]

**how to stop disk from spinning**

- disable -noatime
- stop daemons from saving log to disk or save log to ramdisk
- no flush with ext2?
    - convert to ext2     tune2fs -O ^has_journal /dev/hda3

**disable unnecessary services/daemons**

**uninstall applications that I don't use**

---

### Post by VERiON on 2008-01-16
[SIZE="4"]**your ideas/requests**[/SIZE]

if you have an interesting idea, what can be improved in xubuntu install, I can put it here:

example:

> 
I really like OSX "apple key" ("super" in linux world) implementation.
In OSX most crucial keyboard shortcuts work with "apple key"

apple-Q quit application
apple-W close window
apple-TAB cycle through programs
apple-X cut
apple-V paste

I would like to have that functionality in xubuntu.

I know I can do the same with CTRL. But I have to switch between function keys:

ALT-TAB  cycle through programs
CTRL-W close window

And because I always use control keys on the left side of the keyboard, I prefer apple key as my main function key because on iBook keyboard it is easier to reach apple key then CTRL :D - try CTRL-P with one (left) hand


---

### Post by VERiON on 2008-01-16
**[SIZE="4"]help me[/SIZE]**

**murrine configurator**

[murrine configurator]("http://murrine.netsons.org/index.php?q=node/1") is a great tool for configuring murrine theme (in my case - to remove roundness and shine of any theme and speed up GUI significantly)
Unfortunatly there is no .deb PPC package for [murrine configurator]("http://murrine.netsons.org/index.php?q=node/8")

- if you have one please post the link
- if you can compile PPC pagkage, please do it and post link

---

### Post by VERiON on 2008-01-16
.

---

### Post by VERiON on 2008-01-16
.

---

### Post by Jammy4041 on 2008-01-30
I take it you need to download RPMs.

To do this, you need alien.

Alien is a piece of software that enables you to convert RMPs into DEBs etc. (Ubuntu uses the DEB format, whereas GimpShop is an RPM).

you can download alien from [http://packages.debian.org/sid/all/alien/download]("http://packages.debian.org/sid/all/alien/download").  ( I know it's the Debian site, but Ubuntu is based on Debian, and it works all the same)

Just choose your country and download.

Once it has downloaded, you can install it by double clicking on it.

Now download GimpShop and in a terminal all you need to do is:

sudo alien (File name of Gimp shop)
Then where you put the file e.g. your desktop, you will find your original RPM and next to it a DEB. 

Click on your deb package and it should install "normally"

---

### Post by glug101 on 2008-02-03
> **VERiON said:**
> 

3. install dri driver  [if you know better way - let me know]

xubuntu doesn't install dri drivers out of the box, so you have to get one:

- boot ubuntu 7.10 live CD
- copy /usr/lib/dri directory to pendrive (for Radeon 9550 you only need r300_dri.so file in that directory)
- set permissions on directory to "Others: Read & Write"
- boot into your xubuntu
- make "dri" directory in "/usr/lib" (all without quotes)
- "r300_dri.so" file into /usr/lib/dri
- logout and login again


Has anybody been successful with this step?  I booted the livecd and can't find /usr/lib/dri.  In fact, "locate dri" comes up with zilch as well.  How does one get dri to work in Xubuntu?

If what I've read here is true, then it seems silly that dri is not included on Xubuntu, and even sillier if the functionality isn't available in a package that can easily be installed.

---

### Post by VERiON on 2008-02-11
You have to boot UBUNTU 7.10 (not Xubuntu) liveCD and copy this file - just like I did.

I agree it is silly that xubuntu doesn't ship with this driver.

Anyway - r300 open drivers preformance really dissapoints me (not that smooth like in OSX).
Glxgears shows about 950 fps.

I've stoped using compiz, because firefox scrollin was to choppy.

---

### Post by kogen on 2008-03-08
Hi i just installed xubuntu on my ibook G4. I've found this post searching for two finger scroll - and it worked!

> **VERiON said:**
> ([OSX Quicksilver]("http://en.wikipedia.org/wiki/Quicksilver_(software)") equivalent) > [Gnome launch box]("http://developer.imendio.com/projects/gnome-launch-box")?


I sugest installing [Gnome-Do]("http://do.davebsd.com/") as OSX Quicksilver replacement.

You just need to add the Gnome-Do PPA from launchpad. Add the following line to your /etc/apt/sources.list file:
```
deb http://ppa.launchpad.net/do-core/ubuntu gutsy main
```
And as always...
```
sudo aptitude update
sudo aptitude install gnome-do
```
ALT-F2 or open a terminal and execute: gnome-do

**Easy r300_dri.so**
You can get "r300_dri.so" module by simply instaling "libgl1-mesa-dri" package.
```
sudo apt-get install libgl1-mesa-dri
```
Nice thread BTW. I'll try to contribute some more info in the future

---

