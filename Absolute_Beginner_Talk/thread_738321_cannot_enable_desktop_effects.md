---
title: "cannot enable desktop effects"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by daberger on 2008-03-28
i recently installed ubuntu but now i cannot run any desktop effects. im guessing this may becuz of my bad graphics card but im not sure. i also cannot use networking for sum reason and i would appreciate it if sum1 could help me out.

running ubuntu 7.04 alternate (wubi)

---

### Post by rudihawk on 2008-03-28
Do you have a nvidia or an ati graphics card? or intergrated?

---

### Post by daberger on 2008-03-28
im not sure. its a hand me down system and i havent seen any data about vid cards since ive had it. ill ask the previous owner


integrated?

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> im not sure. its a hand me down system and i havent seen any data about vid cards since ive had it. ill ask the previous owner


integrated?


Hi

type in terminal to see information about your HW ```
lspci
```

---

### Post by daberger on 2008-03-28
ok thank you waappu

here is what i get from it 00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
02:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)


so i have an ati video card.

next step?

---

### Post by Waappu on 2008-03-28
Hi

If you type in terminal, what is output ?
```
compiz
```

---

### Post by daberger on 2008-03-28
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity

---

### Post by icechen1 on 2008-03-28
This might help: [http://ubuntuforums.org/showthread.php?t=580748&highlight=xgl](http://ubuntuforums.org/showthread.php?t=580748&highlight=xgl).

---

### Post by Waappu on 2008-03-28
> **icechen1 said:**
> This might help: [http://ubuntuforums.org/showthread.php?t=580748&highlight=xgl](http://ubuntuforums.org/showthread.php?t=580748&highlight=xgl).

Hi

Yes. But I think open source driver "radeon" will work also with that video card and then you don't need XGL. But I'm not sure.

See this for open source driver
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by daberger on 2008-03-28
ice chen i dont use gutsy gibbon,
are ther any out ther for ubuntu?

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> ice chen i dont use gutsy gibbon,
are ther any out ther for ubuntu?

Hi

Gutsy Gibbon is name of Ubuntu version 7.10.

What Ubuntu version you use ?

---

### Post by Juggrnott on 2008-03-28
Gusty Gib is ubuntu 7.10

---

### Post by daberger on 2008-03-28
i used wubi to install so i could still use windows. i believe i have 7.04

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> i used wubi to install so i could still use windows. i believe i have 7.04

Type in terminal to see your Ubuntu version ```
cat /etc/issue
```or```
cat /etc/lsb-release
```

---

### Post by daberger on 2008-03-28
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu hardy (development branch)"

---

### Post by Waappu on 2008-03-28
Hi

Did you know you use beta version ?

Well, I don't know if there is something special to configure xorg 7.3.

Gutsy guide to enable desktop effect might work also to Hardy or not.

But you can try first that open source "radeon" driver configuration to xorg.conf

---

### Post by daberger on 2008-03-28
yes. the other versions didnt seem to work on my computer

---

### Post by daberger on 2008-03-28
no luck

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> no luck

Can you post your xorg.conf file ?

---

### Post by daberger on 2008-03-28
how?...

---

### Post by Waappu on 2008-03-28
Hi

type in terminal ```
gedit /etc/X11/xorg.conf
```

---

### Post by Tatty on 2008-03-28
> **daberger said:**
> how?...

type this in a terminal:
```
cat /etc/X11/xorg.conf
```

Then copy and paste the output

---

### Post by daberger on 2008-03-28
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
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
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by Waappu on 2008-03-28
Hi

You can try this. But remember it might crash your X.


type in terminal to backup old file ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_old_file
```

Then edit your xorg.conf as root
```
gksudo gedit /etc/X11/xorg.conf
```

replace content wiiith this
```

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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "vmmouse"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver		"radeon"
Option 		"DRI" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth	24
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Synaptics Touchpad"
EndSection

Section "Module"
Load	"glx"
Load	"dri"
EndSection

Section "Extensions"
Option	"Composite"	"Enable"
EndSection

```

if X not start. revert changes ```
sudo cp /etc/X11/xorg.conf_old_file /etc/X11/xorg.conf
```
or
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by daberger on 2008-03-28
how do i replace?...

---

### Post by daberger on 2008-03-28
ahh never mind.....

---

### Post by daberger on 2008-03-28
and 1 more question, whats my 'X'

---

### Post by Waappu on 2008-03-28
Hi

I hope I don't broke your system....

---

### Post by daberger on 2008-03-28
no it works. but what changed?

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> and 1 more question, whats my 'X'

X windows. Your GUI (Graphical user interface)

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> no it works. but what changed?

Did you log out and back in ?
type in terminal ```
compiz
```

---

### Post by daberger on 2008-03-28
still doesnt let me enable graphic effects

---

### Post by Waappu on 2008-03-28
Hi

Sorry that I could not help :( I don't know how things really work in Hardy.

---

### Post by daberger on 2008-03-28
hey but thanks for ur help

---

### Post by lswest on 2008-03-28
can you post the output of ```
lshw -C Display
```.  And what version exactly are you running? if it's pre-7.10 (gutsy gibbons) you'll need to install beryl.  And if it's 7.10 or later, you'll probably need to install xserver-xgl to be able to use the compiz effects.

---

### Post by daberger on 2008-03-28
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon IGP 330M/340M/350M
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=66 mingnt=8

im running hardy

---

### Post by daberger on 2008-03-28
hey all  im going to take the dogs for a walk . ill b back soon. thank u for all ur help and plz keep helping

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> hey but thanks for ur help

Hi

Just want make sure your system still work after changes to xorg.conf.

Did you log out after changes ?

save your work

Press 
Ctrl+Alt+backspace

if dont get back to login screen press

Ctrl+alt+F2
enter user name and then password.
then
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot
```

---

### Post by daberger on 2008-03-28
yes wappu it works :)

---

### Post by daberger on 2008-03-28
do u think it would help if i installed beryl?

---

### Post by Ub1476 on 2008-03-28
According to Bug [#2013390]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/201330") on [Launchpad]("https://launchpad.net/"), is this a blacklisted video card/controller. 

Read [here]("http://ubuntuforums.org/showthread.php?t=582112") for instructions on how to remove the blacklist. Those instructions are for Gutsy, but I suppose they are the same in Hardy.

Good luck:)

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> do u think it would help if i installed beryl?

Hi

It not help. Beryl need same things from video card. Also beryl is "old version" of Compiz Fusion what Ubuntu use for desktop effects.

---

### Post by daberger on 2008-03-28
so i have compiz fusion and all i lack is the right driver?

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> so i have compiz fusion and all i lack is the right driver?

Hi

yes, or right xorg.conf setup. ATI cards has been always pain in Linux, if I understand correct

---

### Post by Ub1476 on 2008-03-28
The Radeon/ATI driver is fine (as there is nothing else which works for your ATI card). For some reason though, your ATI card has been blacklisted in Hardy Heron. This means that Compiz won't work unless you remove the blacklist. See my above post.

ATI has been quite a pain in Linux for some while though. However, they have just started to release monthly new drivers, which is a huge improvement for what we had before. They are also slowly opening specifications for they VGA controllers, so the Linux/open-source community can make their own ATI drivers.

---

### Post by daberger on 2008-03-28
it got worse. now it freezes when i try to change the desktop effect settings

ill keep that in mind when i but my next system :)

so im thinkin i should just forgo the desktop effects till then?

---

### Post by daberger on 2008-03-28
i looked at ur above post ub but it showed nothing about my driver being blacklisted

---

### Post by Ub1476 on 2008-03-28
> I have an ATI radeon IGP 340M (Chip ID 1002:4337) that works really nice with the open source "ati" driver and compiz ALWAYS worked very well since Feisty.

According to a problem on some ati cards as reported in Bug #197135, open source "ati" driver is going to be blacklisted for compiz in Hardy (on laptops).

This guy obviously have been using Ubuntu for some while with the same ATI card as you (**ATI Technologies Inc Radeon IGP 330M/340M/350M**), and this worked brilliant with Compiz before. However, in Hardy, this card is blacklisted. So you have to whitelist it.

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> it got worse. now it freezes when i try to change the desktop effect settings

ill keep that in mind when i but my next system :)

so im thinkin i should just forgo the desktop effects till then?

Hi

Did you removed changes I told to do and restarted X before testing what Ub1476 told ?
Might be that my modification to xorg.conf aren't so good

---

### Post by daberger on 2008-03-28
k ty

---

### Post by daberger on 2008-03-28
alright ub ill try it again

---

### Post by daberger on 2008-03-28
tried it all and no diffrence. still gives me unable to start desktop effects message.

i dont know whats going on here

---

### Post by Ub1476 on 2008-03-28
What driver are you using in System>Administration>Screens and graphics (might be called something else in Hardy)?

What is the output of:

```
SKIP_CHECKS=yes compiz
```

---

### Post by daberger on 2008-03-28
andrew@andrew-laptop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


i was looking for screens and graphics but i got nothing resembling it. here are my options from system> administrations.

authorizations
hardware drivers
language support
login window
network
networking tools
printing
services
software sources
synaptics package monitor
systemlog
time and date
update manager and
users and groups

---

### Post by Ub1476 on 2008-03-28
Actually, it appears to be a problem with Compiz. Try reinstalling:

```
sudo apt-get autoremove
sudo apt-get install ubuntu-desktop --reinstall
```

---

### Post by daberger on 2008-03-28
ub. somhow the problem seems to have solved itself. or maybe we solved it becuz i am now on normal graphics mode. thank u very much. and one more question, what do i press for free cube control?

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> ub. somhow the problem seems to have solved itself. or maybe we solved it becuz i am now on normal graphics mode. thank u very much. and one more question, what do i press for free cube control?

Hi

If you like spin cube press both mouse buttons in same time.
or Ctrl+alt+mouse button 1

What you mean by ? > on normal graphics mode

---

### Post by daberger on 2008-03-28
didnt work. do i need to be on high graphics to use the spinny cube

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> didnt work. do i need to be on high graphics to use the spinny cube

You need enable desktop cube plugin.
type in terminal```
sudo aptitude install compizconfig-settings-manager
```
then you can find Advanced desktop effect settings from System -> Preferences.
There you can enable desktop cube.


Still I like know what you mean by > on normal graphics mode ?? =)

---

### Post by daberger on 2008-03-28
yes i understand. will that give me four workspaces?
i only have 2 now.
may u dont have it in fiesty but i have 3 options of desktop effects in hardy. off. medium. or high. normal is medium

---

### Post by Waappu on 2008-03-28
> **daberger said:**
> yes i understand. will that give me four workspaces?
i only have 2 now.
may u dont have it in fiesty but i have 3 options of desktop effects in hardy. off. medium. or high. normal is medium

Hi

In advanced desktop effect go general options and select desktop size tab.
adjust horizontal virtual size to 4

---

### Post by FreewareFan on 2008-03-28
> **Ub1476 said:**
> This guy obviously have been using Ubuntu for some while with the same ATI card as you (**ATI Technologies Inc Radeon IGP 330M/340M/350M**), and this worked brilliant with Compiz before. However, in Hardy, this card is blacklisted. So you have to whitelist it.

I also use this graphics card, and am thinking about installing Hardy this weekend.  What do I need to do in order to whitelist my ATI card in Hardy??

UPDATE: nevermind, I found it in the previous post...

---

### Post by daberger on 2008-03-28
freeware fan i recomend that u do not get hardy.

waappu thank you but i can still not enable the advanced desktop items
but if i run SKIP_CHECKS=yes compiz
then i can get them to work. but as soon as i restart they stop. i dont know what to do

---

### Post by FreewareFan on 2008-03-29
> **daberger said:**
> freeware fan i recomend that u do not get hardy.


Why?  Just because of the compiz-fusion issue?  As you've already found out, there is a work-around for that issue, and probably someone will come up with a script or patch in the near future after Hardy is officially released.

Worse case scenario is that I just won't be able to use compiz.  That's not a deal breaker for me, because after running it for the last couple of months on Gutsy, I find that I really don't even use it all that often.  Matter of fact, now that I think about it, the only feature that I use on a daily basis would be the ring switcher..  

So, do you have other reasons for advising me not to use Hardy?

---

### Post by st0n3cutt3r on 2008-03-29
Try disabling the restricted drivers.

I know it sounds silly, but it worked on my ATI card, and I have seen positive results from other people who've tried the same thing (on this forum, no less, and with other ATI cards).

I'm too lazy to find the link.  Just try it.

---

### Post by FreewareFan on 2008-03-29
How does one disable restricted drivers?  I've never had to use them, to my knowledge, not on Gutsy anyway....

---

### Post by Waappu on 2008-03-29
> **daberger said:**
> freeware fan i recomend that u do not get hardy.

waappu thank you but i can still not enable the advanced desktop items
but if i run SKIP_CHECKS=yes compiz
then i can get them to work. but as soon as i restart they stop. i dont know what to do

Hi

You can create startup script I think.

```
gedit ~/.config/autostart
```

write these lines to file and save it

```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=Compiz
Name[en_US]=Compiz
Comment[en_US]=Custom startup for desktop effects
Comment=Custom startup for desktop effects
Exec=CHECKS=yes compiz
X-GNOME-Autostart-enabled=true
```

---

### Post by lswest on 2008-03-29
Looks like it is working for you, but just in case it's not this might help:
```
sudo apt-get install xserver-xgl
```
since the compiz check is telling us xgl is not present, but i'm not sure if it will work on your older card.  I only have an ATI RADEON 9600XT which works fine with the propriety drivers...and i don't use compiz effects on that PC, so this is as much a guess as anything else.
then
```
gksudo gedit /etc/X11/xorg.conf
```
and add > Section "Extensions"
	Option		"Composite"	"Enable"
EndSection to the end of the file.  (If this is already present, just ignore me :P)

---

### Post by Ub1476 on 2008-03-29
daberger, read [this sticky]("http://ubuntuforums.org/showthread.php?t=582112") if you want the SKIP_CHECK=YES option to always be true. 

You don't need XGL installed because you're using the open-source ati driver.

---

### Post by Waappu on 2008-03-29
Hi

I agree with Ub1476 and also think you should not install XGL. ATI open source driver not need XGL

---

### Post by daberger on 2008-03-29
hey thanks every1 for all ur help and i guess ur right freeware, there is a temporary fix. ill try ur solutions.

---

### Post by daberger on 2008-03-29
i tried the xgl fix and now i get an error when i boot up. how do i undo this plllllz help. my comp is no crashing alot

---

### Post by lswest on 2008-03-30
to undo it just do ```
sudo apt-get remove xserver-xgl
``` (it removes the xgl packages)  sorry for the delayed response, went to bed an hour before you wrote that :P

---

### Post by daberger on 2008-04-08
thank you.



srry for the delayed response got an essay......

---

### Post by jctalluri on 2008-04-27
The output is....

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by daberger on 2008-04-30
oh yeah! almost 1500 hits woot

---

### Post by gpan on 2008-05-17
Has anyone managed to enable extra desktop effects of this card (ATI  Radeon IGP 330M/340M/350M [1002:4337]) in Ubuntu 8.04 (Hardy)?:(

---

