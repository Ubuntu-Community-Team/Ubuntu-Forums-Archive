---
title: "A Few Questions"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by saabirsa on 2005-12-22
Hello all,

I finally got Ubuntu up and running, but a few things still dont work here and there, but slowly im getting the hang of it :)

One of the things that dosent work is the sound, normally in Windows, id do a search for the Drivers on Google, but since this is Linux, I don't know what I should be searching for. I have a C-Media CMI8330 OnBoard Sound Card (I think...).

Also, I have 5 computers running on my network. 3 with Windows XPSP2 and 2 With Linux. Usually, I share the intenet using ICS to all the comptuers on the LAN using my Computer (WinXPSP2). Becasuse ICS does not forward ports (which I need to run servers), I am thinking of moving my internet connection to the Ubuntu machine next to me and letting it share the internet, using my BT Voyager 105 AOL modem. Is this possible?

Thanks for all your help :smile:
Saabir Salim

---

### Post by cwaldbieser on 2005-12-22
[QUOTE=saabirsa]Hello all,

I finally got Ubuntu up and running, but a few things still dont work here and there, but slowly im getting the hang of it :)

One of the things that dosent work is the sound, normally in Windows, id do a search for the Drivers on Google, but since this is Linux, I don't know what I should be searching for. I have a C-Media CMI8330 OnBoard Sound Card (I think...).

Also, I have 5 computers running on my network. 3 with Windows XPSP2 and 2 With Linux. Usually, I share the intenet using ICS to all the comptuers on the LAN using my Computer (WinXPSP2). Becasuse ICS does not forward ports (which I need to run servers), I am thinking of moving my internet connection to the Ubuntu machine next to me and letting it share the internet, using my BT Voyager 105 AOL modem. Is this possible?

Thanks for all your help :smile:
Saabir Salim[/QUOTE]

It is possible to share your Internet connection by turning an Ubuntu machine into a router if it has enough NICs.  What is your physical setup like?

---

### Post by bluefrog on 2005-12-22
enable internet connection on ubuntu. install firestarter, follow firestarter wizard.
eventually tweak firestarter's preferences.
done.

james

---

### Post by saabirsa on 2005-12-22
@**cwaldbieser**
 
Internet <- My Computer <- Hub (In place of a router, which will be bought soon) <- Computers 2,3 and 4
 
Thats my setup atm, untill I get a router
 
@**bluefrog**
I would enable the internet but,
1) I don't have the drivers for the modem
2) I don't know what *Firestarter* is :razz: 
 
Thanks
Saabir Salim

---

### Post by saabirsa on 2005-12-22
OK as for the sound drivers, i found this,
 
@[http://www.opensound.com/linux-x86.html]("http://www.opensound.com/linux-x86.html")
[FONT=Helvetica]> 
**[FONT=Helvetica]Unbuntu/Debian Specific Notes: [/FONT]**[FONT=Helvetica][/b]
None of the Debian systems will work out of the box until you install the kernel sources and generate a kernel from those sources - the reason is that the kernels shipped with Ubuntu are compiled with GCC 3x and the compiler most people will install is GCC 4 and there is NO way to get kernel modules compiled by GCC4 to work with GCC3 compiled kernels. The kernel sources are also a huge mess since the kernel version and the source version are actually different. The ONLY way to successfully OSS to run on Ubuntu or Debian is: 1) make oldconfig 2) make bzImage 3) make modules 4) make modules_install 5) make install 6) reboot 7) now run oss-install from the directory where you downloaded and unpacked the OSS files.[/FONT]

 
What does this mean, and how do I do it?
Thanks
Saabir Salim[/FONT]

---

### Post by estel on 2005-12-22
You don't need to do it :)

Ubuntu offers a number of "sound architectures", and these work (well.. you don't need to worry about GCC and compiling them). They're called esd (enlightenment sound daemon) and alsa (Advanced Linux Sound Architecture?). 
Regardless, you don't need OSS.

Sorry I can't help with your direct query...

---

### Post by bscbrit on 2005-12-22
You are not the only person trying to get a BT Voyager 105 modem working with Ubuntu (Richard Willace and others have had recent threads).  I could not help.  But, if you solve the problem, I think there are quite a few more people who would be grateful for the information on how you did it.  Are there any modem gurus reading who think that they can help with this?

---

### Post by cwaldbieser on 2005-12-22
[QUOTE=saabirsa]@**cwaldbieser**
 
Internet <- My Computer <- Hub (In place of a router, which will be bought soon) <- Computers 2,3 and 4
 
Thats my setup atm, untill I get a router
[/QUOTE]
If you get a router, you probably won't need to set up one of your PCs as the gateway unless you have some specialized need in mind.  Most routers will allow you to filter network traffic and forward ports.

Firestarter is a GUI front end for manipulating the Linux firewall/IP filtering internals.  There is a more general command line tool called iptables which is more flexible, but it is generally considered to have more of a learning curve.

You can enable IP forwarding on your Ubuntu machine and set your other PCs to use it as their default gateway, and that would pretty much turn it into a router.  Using firestarter lets you do this by clicking a single checkbox.  As a bonus, you can block/allow various ports and addresses from the GUI as well (packet filtering).

I don't know if there is an easy way to use Firestarter to do port forwarding.  You may have to use iptables for that.  A good search term is DNAT, which stands for Destination Network Address Translation.  You basically tell your router to change the destination address of the packet to the PC you want to forward the packet to.

---

### Post by saabirsa on 2005-12-22
@**estel**
I have tried (In the Multimedia Systems Selector) all of them, and still nothing :( Any Ideas?
 
@**bscbrit**
Trust AOL and BT to come with a modem that only works with Windows :rolleyes: , but if I get it working, ill post :smile: 
 
@**cwaldbieser**
Yep, i know, that's why I want to buy a router ASAP, just a bit strapped for cash atm. As for Firestarter, installing now :cool: 
 
Thanks
Saabir Salim

---

### Post by saabirsa on 2005-12-23
OK, ive got another question with Ubuntu,
 
How come my AT Keyboard does not work in Ubuntu and my USB keyboard does. I know that my AT Keyboard works because when i need to run the installation for Ubuntu and enter the BIOS etc, it works, but when Ubuntu boots up, it dies.
 
Any Ideas?
Saabir Salim
(PS Linux isnt as hard as I imagned it to be :razz: )

---

### Post by bscbrit on 2005-12-23
Perhaps only one keyboard is being set up in /etc/X11/xorg.conf?

---

### Post by saabirsa on 2005-12-23
OK, so how do I add another one, ive go the file flared up here ;) 
 
Saabir Salim

---

### Post by bscbrit on 2005-12-23
Do you actually need 2 keyboards?  Which one would you really like to use?  

I find I can type enough mistakes just by using the one keyboard. I hate to think _waht_ I might achieve using 2:p :p :p

EDIT: As if to prove my point _waht_ !!!

---

### Post by saabirsa on 2005-12-23
:p 
Gonna remove the USB one, its a pain in the ass to use, a waste of my money, only reason im using is because the other dosen't work.
 
Saabir Salim
(PS, any ideas on the sound problem anyone?)

---

### Post by bscbrit on 2005-12-23
Let me get this straight - you're using the USB keyboard because the AT doesn't work, and you're now going to remove the working keyboard....?

Does that sound like a good plan to you?

---

### Post by saabirsa on 2005-12-23
OK,
 
I want to get the AT keyboard working
After I get the AT Keyboard working, I am going to remove the USB Keyboard
 
:D
Saabir Salim

---

### Post by bscbrit on 2005-12-23
Can you tell me what the keyboard section of /etc/X11/xorg.conf says?

---

### Post by bscbrit on 2005-12-23
I'm going offline until tomorrow morning - cu then:smile:

---

### Post by saabirsa on 2005-12-23
[quote=bscbrit]Can you tell me what the keyboard section of /etc/X11/xorg.conf says?[/quote]
 
I could'nt find the keyboard bit, so heres the whole file,
 
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
 FontPath "/usr/share/X11/fonts/misc"
 FontPath "/usr/share/X11/fonts/cyrillic"
 FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/share/X11/fonts/Type1"
 FontPath "/usr/share/X11/fonts/CID"
 FontPath "/usr/share/X11/fonts/100dpi"
 FontPath "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection
Section "Module"
 Load "GLcore"
 Load "i2c"
 Load "bitmap"
 Load "ddc"
 Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "type1"
 Load "vbe"
EndSection
Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver  "kbd"
 Option  "CoreKeyboard"
 Option  "XkbRules" "xorg"
 Option  "XkbModel" "pc105"
 Option  "XkbLayout" "gb"
EndSection
Section "InputDevice"
 Identifier "Configured Mouse"
 Driver  "mouse"
 Option  "CorePointer"
 Option  "Device"  "/dev/input/mice"
 Option  "Protocol"  "ImPS/2"
 Option  "Emulate3Buttons" "true"
 Option  "ZAxisMapping"  "4 5"
EndSection
Section "Device"
 Identifier "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
 Driver  "nv"
 BusID  "PCI:1:0:0"
EndSection
Section "Monitor"
 Identifier "MAG D510"
 Option  "DPMS"
EndSection
Section "Screen"
 Identifier "Default Screen"
 Device  "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
 Monitor  "MAG D510"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1024x768" "800x600" "720x400" "640x480" "640x350"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1024x768" "800x600" "720x400" "640x480" "640x350"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1024x768" "800x600" "720x400" "640x480" "640x350"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1024x768" "800x600" "720x400" "640x480" "640x350"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1024x768" "800x600" "720x400" "640x480" "640x350"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1024x768" "800x600" "720x400" "640x480" "640x350"
 EndSubSection
EndSection
Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
EndSection
Section "DRI"
 Mode 0666
EndSection

```

---

