---
title: "Sound not working and cd isn't working properly..."
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by starbright on 2007-09-04
Hi,

I just installed Xubuntu, and when I wanted to listen to music, there was no sound. I have Soundblaster and the speakers work fine, since they had worked in Windows XP. I do not know what the problem is or what I have to do, since Xubuntu is completely new for me!

Also, my CD-ROM is not working properly. I can put in a CD, but when I want to take the CD out, it won't open. I have to reboot the computer and then once it is rebooting, then I can take it out. I don't know what the problem is either. :confused: :confused:

Could someone please help me!! 


Xubuntu 6.10 Desktop
Pentium II 400 mhz

---

### Post by deadgobby on 2007-09-04
Are you talking about listen to a Audio CD or mp3 files? Does the CD eject if you left click on the CD icon and scroll down to the eject? 
 Unlike windows. MP3 formate is a paid for formate, that why MS can play them. Now do not fret. You can install the restricted formates to be able to play mp3.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Gobby

---

### Post by starbright on 2007-09-04
thanks,

now I can play my music files, except I still have No sound!

Help Please!!!


The eject works now! :) I didn't even think to right click and look for a way to eject the CD...now I know.

---

### Post by deadgobby on 2007-09-04
Does the speaker icon have a no sound symbol? Did you go into BIOS and disable the onboard sound device? By disabling the on board will tell the system to use the sound card. The other is open up the terminal and type or copy and paste way.

aplay -l 

This will list of sound devices. 

Gobby

---

### Post by starbright on 2007-09-04
Speaker Icon????

I haven't done anything in the BIOS. I did go into the terminal and it said that no sound cards were found. How can that be possible if I have a sound card?

thanks

---

### Post by Dr Small on 2007-09-04
It sounds like some bios problem. You could check in your bios and see if your onboard audio is set to the audio card, instead of "auto". I had to do this with my new motherboard in order to get sound to work feisty.

Dr Small

---

### Post by starbright on 2007-09-04
I checked the BIOS, but it's all fine. Maybe I need to install a driver for the sound card...Does anyone know how to find a right driver for Xubuntu 6.10 Desktop and to install it??

---

### Post by deadgobby on 2007-09-04
There is no driver for a Sound Blaster card. Do you know what SB card you have? There is a way to install ALSA mixer.
 Open up the terminal and type in

sudo aptitude install alsamixer
 It will ask you for a password and be likely the one you logged into the splash screen with. 


Once install type in the terminal 

alsamixer


You'll get a screen that looks like this.

---

### Post by deadgobby on 2007-09-04
There is no driver for a Sound Blaster card. Do you know what SB card you have? There is a way to install ALSA mixer.
 Open up the terminal and type in

sudo aptitude install alsamixer
 It will ask you for a password and be likely the one you logged into the splash screen with. 


Once install type in the terminal 

alsamixer


You'll get a screen that looks like this.

 Play with the volume levels by using the tab key to go across and the up and down arrows to adjust volume levels. Pop in a audio CD and let it play and play with the levels and see if you get a level. By the way the green  out put on the card should be for head phones.

Gobby

---

### Post by starbright on 2007-09-04
After enetering sudo aptitude install alsamixer the following appeared in my terminal window:

sudo aptitude install alsamixer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find package "alsamixer".  However, the following
packages contain "alsamixer" in their name:
  gnome-alsamixer alsamixergui 
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-image-generic 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
The following packages have been kept back:
  avahi-daemon bind9-host dbus dbus-1-utils dnsutils evince-gtk gdm gimp 
  gimp-data gnupg info iptables linux-headers-2.6.17-10 
  linux-headers-2.6.17-10-generic linux-headers-generic popularity-contest 
  screen tcpdump vim-common vim-runtime vim-tiny w3m 
0 packages upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Should I maybe install the package alsamixergui?

---

### Post by deadgobby on 2007-09-05
OH crude I forgot about that. ME BAD! Yes go ahead and install the alsamixergui. It is a graphical version. Yet, it ill not do any good if the system is not finding the sound card.  Did you open up the terminal and type in

alplay -l

Did it find a sound card?

GObby

---

### Post by starbright on 2007-09-05
I typed it in and it said that there were no sound cards found. Should I just install the alsamixergui even though no sound card can be found??

---

### Post by deadgobby on 2007-09-05
Please put this in the terminal and please copy and paste all of the reply you get from the command.
You can install it and no harm done. You can play with the setting and see if sound appears. Any hoo. Type this in and lets start get the bugger to work. I do not know why a sound blaster live card is not working right off the bat.

lspci -v 


Gobby

---

### Post by starbright on 2007-09-05
this is what is said:

~$ lspci -v 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
        Flags: bus master, medium devsel, latency 64
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fc000000-feffffff
        Prefetchable memory behind bridge: f9000000-f9ffffff

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 32
        I/O ports at ffa0 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at dce0 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
        Subsystem: Dell 3C905B Fast Etherlink XL 10/100
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at dc00 [size=128]
        Memory at ff000000 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at fb000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA])
        Subsystem: Dell Optiplex GX1 Onboard Display Adapter
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 10
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at ec00 [size=256]
        Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at f9000000 [disabled] [size=128K]
        Capabilities: <access denied>


When I try to open alsamixergui it says::    alsamixer: function snd_ctl_open failed for default: No such device

thanks.....

---

### Post by deadgobby on 2007-09-05
[http://ubuntuforums.org/showthread.php?t=283048](http://ubuntuforums.org/showthread.php?t=283048)
[http://ubuntuforums.org/showthread.php?t=305269&highlight=gx1+audio](http://ubuntuforums.org/showthread.php?t=305269&highlight=gx1+audio)
[http://ubuntuforums.org/showthread.php?t=121621&highlight=Dell+Optiplex+GX1+sound&page=2](http://ubuntuforums.org/showthread.php?t=121621&highlight=Dell+Optiplex+GX1+sound&page=2)
 I do not know why your sound blaster is not working. It should work right off the bat. Unless you did not go into BIOS and make sure the on board sound device is disabled.

---

### Post by starbright on 2007-09-05
Hi

So I read some of those threads and it worked with the command

sudo modprobe snd-cs4236

in the terminal, but then to make it stay after rebooting the computer, it does not work. I did as they had said in the thread to enter: 

sudo gedit /etc/modules

in the terminal, but when I enter that command it says

sudo gedit /etc/modules

I don't know what to do. Should I maybe create a start up script or file, so that when I reboot my computer, it will automatically enter the command into the terminal with out me having to do something?? Is something like that possible??

Almost working....

---

### Post by deadgobby on 2007-09-06
Once you debug the sound card. I do not think you need to. Just keep it up. Your doing GREAT!! You can look up your system and search on this forum or other places. I should of ask what is your system from the get go. ME BAD!
Gobby

---

### Post by Haus Neuerburg on 2007-09-06
Hi starbright,
you're working with **X**ubuntu, right? Well, my xubuntu doesn't have the editor "gedit", but "mousepad" is installed by default. Maybe you just replace the "gedit" by "mousepad" and you'll be able to open the file etc/modules and amend it if desired.
Hope that helped....best regards
Haus

---

### Post by starbright on 2007-09-06
**Thank you everyone who helped.**

So I finally have my sound working! :)

So this is what I had to do:

I went into the terminal and entered:

sudo modprobe snd-cs4236

then to make sure it stays after rebooting the computer you have to go into the terminal and enter

sudo mousepad /etc/modules

then at the last entry enter

snd-cs4236

save, and reboot computer. Because I am working with **X**ubuntu I had to put in sudo **mousepad** /etc... rather than sudo **gedit** /etc.... which is for Ubuntu, I'm not sure though, you'll have to try it I guess.

Again, thank you very much for everyone's help!

---

### Post by deadgobby on 2007-09-07
ROCK ON!!!! :guitar:

---

