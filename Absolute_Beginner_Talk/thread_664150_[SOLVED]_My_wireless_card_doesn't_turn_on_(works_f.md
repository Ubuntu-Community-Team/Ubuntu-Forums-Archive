---
title: "[SOLVED] My wireless card doesn't turn on (works fine in vista)"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Jake90 on 2008-01-10
Hi, I'm really new to linux so please explain everything, don't consider something obvious and leave it out. Here is my problem. When I was on vista everything worked fine, but I couldn't stand the program so I switched to Ubuntu. On Ubuntu my wireless card won't even turn on (there is a light that says if it is on or off). I checked the supported drivers and found it on there. My wireless card came built in to my laptop which is a hp pavilion dv6600. That is my primary problem, then when I tried ndiswrapper it doesn't appear in administration so I tried installing other programs and realized they don't come up under administration though it says it is installed. Could someone please help me with this. I don't even know which information to post so just tell me and I'll post it as soon as possible. If my hardware isn't compatible  or if there is nothing I can do then could someone recommend a different distribution of linux for me? Thanks

---

### Post by wolfen69 on 2008-01-10
see this thread [http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)  alot of people are having problems with the 6000 series.

---

### Post by eolson on 2008-01-10
It looks like the thing to do is download 6.06LTS and use it and then upgrade to 8.04 after we find out  how it works.

---

### Post by Jake90 on 2008-01-10
> **wolfen69 said:**
> see this thread [http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)  alot of people are having problems with the 6000 series.
Thanks, but I'm sorry I don't know what gutsy is, I just went to the ubuntu home page clicked download version 7.10 and burned as image then installed. If what I have is in fact gutsy then how do I install the version of ubuntu that will work?

---

### Post by Jake90 on 2008-01-10
> **eolson said:**
> It looks like the thing to do is download 6.06LTS and use it and then upgrade to 8.04 after we find out  how it works.
Could you tell me how to do that. I don't even know what that means. Thanks I am desperate, I really don't want to be stuck with vista

---

### Post by buccaneere on 2008-01-11
> **Jake90 said:**
> Could you tell me how to do that. I don't even know what that means. Thanks I am desperate, I really don't want to be stuck with vista

See if you can find Edgy Eft version 6.10 to download. More users have solved problems with this version, I do believe.

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Edgy-Eft-15387.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Edgy-Eft-15387.shtml)

Are you sure the wireless switch is not powered on?

---

### Post by Jake90 on 2008-01-11
> **buccaneere said:**
> See if you can find Edgy Eft version 6.10 to download. More users have solved problems with this version, I do believe.

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Edgy-Eft-15387.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Edgy-Eft-15387.shtml)

Are you sure the wireless switch is not powered on?
Thanks, I am downloading it right now. I  have a dual boot (I didn't want to delete vista until I was sure this was working) and if I boot vista it works fine. I have a switch to turn on the card when I do the light turns from red to blue on vista, but on Ubuntu when I switch it on it it stays red.

---

### Post by Jake90 on 2008-01-11
> **buccaneere said:**
> See if you can find Edgy Eft version 6.10 to download. More users have solved problems with this version, I do believe.

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Edgy-Eft-15387.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Edgy-Eft-15387.shtml)

Are you sure the wireless switch is not powered on?
I downloaded it and started installing it but when I got to the detect network devices part I hit the same problem it could not detect my wireless card. It said that I may have to install the module for it so  should go back. I went back about 20 times with the card on and the card off but it couldn't find it. I then finished the installation without but when I booted it up all that appeared was code. I entered my user name and password and waited but nothing happened. Did I do something wrong or is that how it's supposed to be? (I did install lantern and the other program that they asked me if I wanted to) If it is how it is supposed to be then I don't know enough to use it. Am I better off going with another distribution? I am without sleep for almost 35 hours already I can't do this for much longer. If I am better of which distribution should I install. I would need one that is beginner friendly and will be able to find my card. Thanks a lot

---

### Post by Amstell on 2008-01-11
IMO Ubuntu is the best distro.  Its not the distro its your hardware and thats a problem with linux, especially wireless cards.  Stick with it and keep researching.  I don't use wireless but understand that a wrapper works for a lot of wireless cards.  Good luck and don't give up.

---

### Post by Digger78 on 2008-01-11
Hi jake,

I have never used Dapper (6.06) so I dont know what is involved in the installer, I'm guessing that you have just installed the server edition** (ubuntu-6.06.1-server-i386.iso)** instead of the desktop edition **(ubuntu-6.06.1-desktop-i386.iso)**.

If you still have the .ISO or even if you could pop the disk in on Vista  and confirm the **full name/label**

**If** you do have the server edition could you download the **desktop edition** and install it

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Jake90 on 2008-01-11
> **Digger78 said:**
> Hi jake,

I have never used Dapper (6.06) so I dont know what is involved in the installer, I'm guessing that you have just installed the server edition** (ubuntu-6.06.1-server-i386.iso)** instead of the desktop edition **(ubuntu-6.06.1-desktop-i386.iso)**.

If you still have the .ISO or even if you could pop the disk in on Vista  and confirm the **full name/label**

**If** you do have the server edition could you download the **desktop edition** and install it

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

You are right, thanks a lot 
Should I reinstall the version? (I still have the installation cd from last time) they told me I should switch to another version because I was having problems with this one

---

### Post by Digger78 on 2008-01-11
I would recommend downloading and installing ubuntu dapper (6.06) or fiesty (7.04) desktop edition as there are people here who will know how to workaround any problems you encounter.

you can download dapper from [http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-desktop-i386.iso](http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-desktop-i386.iso)

or

feisty from [http://releases.ubuntu.com/7.04/ubuntu-7.04-desktop-i386.iso](http://releases.ubuntu.com/7.04/ubuntu-7.04-desktop-i386.iso)


I am assuming that you have an Intel processor, if you dont, you will need different links.

---

### Post by stchman on 2008-01-11
> **Jake90 said:**
> Hi, I'm really new to linux so please explain everything, don't consider something obvious and leave it out. Here is my problem. When I was on vista everything worked fine, but I couldn't stand the program so I switched to Ubuntu. On Ubuntu my wireless card won't even turn on (there is a light that says if it is on or off). I checked the supported drivers and found it on there. My wireless card came built in to my laptop which is a hp pavilion dv6600. That is my primary problem, then when I tried ndiswrapper it doesn't appear in administration so I tried installing other programs and realized they don't come up under administration though it says it is installed. Could someone please help me with this. I don't even know which information to post so just tell me and I'll post it as soon as possible. If my hardware isn't compatible  or if there is nothing I can do then could someone recommend a different distribution of linux for me? Thanks

The DV6600 series uses the broadcom 43xx series of cards.  You need to use ndiswrapper to get it to work.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver)

---

### Post by ginnie6 on 2008-01-12
sadly returning mine is not an option. bought it at Compusa and all sales are final since they're closing. I've gone back to a dual boot with vista since nothing I've tried can get the wireless working. I hate it but the whole point of a laptop was to not be chained to the desk. It really stinks though since dh's toshiba works perfectly on ubuntu.

---

### Post by buccaneere on 2008-01-12
> **ginnie6 said:**
> sadly returning mine is not an option. bought it at Compusa and all sales are final since they're closing. I've gone back to a dual boot with vista since nothing I've tried can get the wireless working. I hate it but the whole point of a laptop was to not be chained to the desk. It really stinks though since dh's toshiba works perfectly on ubuntu.

What wireless card do you have?

---

### Post by ckuka on 2008-01-12
If you are unable to get it to work using edgy eft, check [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) and verify that your card is supported. ndiswrapper should work, but I know how that goes....
If it is not supported, you can post suggestions to support the driver to ubuntu "directly", I think in the "Idea Pool", but I'm sorry I don't actually know where.  Don't be discouraged, XP reads the card because it was configured to, not because it is a better operating system. 
Good Luck!

---

### Post by Jake90 on 2008-01-13
> **Digger78 said:**
> I would recommend downloading and installing ubuntu dapper (6.06) or fiesty (7.04) desktop edition as there are people here who will know how to workaround any problems you encounter.

you can download dapper from [http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-desktop-i386.iso](http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-desktop-i386.iso)

or

feisty from [http://releases.ubuntu.com/7.04/ubuntu-7.04-desktop-i386.iso](http://releases.ubuntu.com/7.04/ubuntu-7.04-desktop-i386.iso)


I am assuming that you have an Intel processor, if you dont, you will need different links.

I just installed gutsy.. oh well. I don't have intel I have amd turion. Which links do I need?

---

### Post by Jake90 on 2008-01-13
> **stchman said:**
> The DV6600 series uses the broadcom 43xx series of cards.  You need to use ndiswrapper to get it to work.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver)

Thanks, that looks perfect. The only problem is that there are links in there and I can't access the Internet on Linux I am on vista right now (dual boot) so I don't think that will work....
I can try going somewhere to get wired Internet for however long it takes but that may be in a week so if you have an alternative please let me know.

---

### Post by Jake90 on 2008-01-13
All right, the last problem is still not solved but now I have a couple more. Maybe these are related so I'll put them here instead of a new thread.The first one is after I was told I need ndiswrapper I went to administrations>package manager and tried installing it. It said it was installed but when I lloked under administrations again it was no where to be found. I searched my whole computer and even restarted but it is not on my computer although it's file are. I tried this with another program (just to see what would happen) and the same thing happened. The second problem I have is when I try to install the driver to my graphics card (nvidia, I went to restricted drivers and tried clicking on it) it says error with source. Thanks a lot for all your help so far, and any more help would be greatly appreciated.

---

### Post by Digger78 on 2008-01-13
From reading a few posts i believe you will need to use the alternate install CD (text based installer) I have never used it, so i don't know what is involved
[http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso)

If the system fails to boot after installation (quote from [This Post]("http://ubuntuforums.org/showpost.php?p=3096602&postcount=1"))
[QUOTE=EXCiD3]at the GRUB menu, hit 'e' and add 'noapic' to the end linux image boot line. Make sure you leave a space in front of it.[/QUOTE]

when you have it installed and can boot into it, we will continue.

---

### Post by Jake90 on 2008-01-13
[QUOTE=stchman;4116799]The DV6600 series uses the broadcom 43xx series of cards.  You need to use ndiswrapper to get it to work.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver)[/QUOT[/I]
I got internet but I got lost after the source list pops up where am I supposed to continue the steps. I tried both but I don't know where I am supposed to type in, in the source list. I am going to try installing the alternative because even if I fix this problem I may have to install the alternative anyway to fix my other problems and then I will have to do this again anyway.

---

### Post by Jake90 on 2008-01-13
> **Digger78 said:**
> From reading a few posts i believe you will need to use the alternate install CD (text based installer) I have never used it, so i don't know what is involved
[http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso)

If the system fails to boot after installation (quote from [This Post]("http://ubuntuforums.org/showpost.php?p=3096602&postcount=1"))


when you have it installed and can boot into it, we will continue.
All right I have installed it, but when I try to boot it up it says server X cannot be loaded and then goes back to line of code. I tried pressing e but when I press it, I have 4 options to add to and I'm not sure which one to do it on. Am I doing something wrong?

---

### Post by Digger78 on 2008-01-13
i think its the line that will look similar to

```
kernel /boot/vmlinuz-[COLOR="Red"]blah blah blah[/COLOR]
```

leave a space after "ro quiet splash"


```
[COLOR="Red"]blah blah blah[/COLOR] ro quiet splash noapic
```

then press return

press escape

then press return to boot

---

### Post by Digger78 on 2008-01-13
when you have booted into the desktop, open a terminal

```
sudo gedit /boot/grub/menu.lst
```

near the bottom you will see the menu entries

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=[COLOR="Red"]blah blah[/COLOR] ro quiet splash **noapic**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

the values will obviously be different on yours but you get the idea....dont you?

---

### Post by Jake90 on 2008-01-13
> **Digger78 said:**
> i think its the line that will look similar to

```
kernel /boot/vmlinuz-[COLOR="Red"]blah blah blah[/COLOR]
```

leave a space after "ro quiet splash"


```
[COLOR="Red"]blah blah blah[/COLOR] ro quiet splash noapic
```

then press return

press escape

then press return to boot

Yeah that is what I tried but it doesn't help anything. (does return mean shift>enter?if it doesn't then that must be what I am doing wrong) It shows up in the code but when I boot first code appears then the screen gets all messed up except for the middle which is blue and says "could not load server x which is....."

---

### Post by Digger78 on 2008-01-13
enter will do the same thing.

---

### Post by Jake90 on 2008-01-13
> **Digger78 said:**
> enter will do the same thing.

 So is the problem my installation? That I somehow did not install server X?

---

### Post by Jake90 on 2008-01-13
> **Digger78 said:**
> i think its the line that will look similar to

```
kernel /boot/vmlinuz-[COLOR="Red"]blah blah blah[/COLOR]
```

leave a space after "ro quiet splash"


```
[COLOR="Red"]blah blah blah[/COLOR] ro quiet splash noapic
```

then press return

press escape

then press return to boot
The exact error message that comes up is
"Failed to start the X server (your graphical interface) It is likely that it is not set up correctly would you like to view the X server output to diagnose the problem?( Then you can choose yes or no) I selected yes and it gave a whole message on what to do before reporting and stuff like that then on bottom. "Fatal server error no screens found"

---

### Post by Digger78 on 2008-01-13
OK try booting into "recovery mode" then put the installation CD in the drive

you will need to login, then  (they may already be installed but just to be sure)

```
sudo apt-get install xserver-xorg ubuntu-desktop
```

when its finished 

```
sudo /etc/init.d/gdm start
```

```
startx
```

if it still fails to start take note of the lines starting with** (EE)**

I need to goto bed now but i will be back later today (its 4:45 am here)

---

### Post by Jake90 on 2008-01-14
> **Digger78 said:**
> OK try booting into "recovery mode" then put the installation CD in the drive

you will need to login, then  (they may already be installed but just to be sure)

```
sudo apt-get install xserver-xorg ubuntu-desktop
```

when its finished 

```
sudo /etc/init.d/gdm start
```

```
startx
```

if it still fails to start take note of the lines starting with** (EE)**

I need to goto bed now but i will be back later today (its 4:45 am here)
It still didn't work. By EE it said "No Devices Detected" and on bottom "fatal server error, no screens found
Thanks a lot, and sorry for keeping you up so late.

---

### Post by Digger78 on 2008-01-14
OK,

Boot into recovery mode and login

```
sudo dpkg-reconfigure xserver-xorg
```

when selecting the driver try "**vesa**"

continue through the configuration, i dont think you should need to change anything else, if its blank, leave it blank

when your back at the command line

```
startx
```

---

### Post by Jake90 on 2008-01-14
> **Digger78 said:**
> OK,

Boot into recovery mode and login

```
sudo dpkg-reconfigure xserver-xorg
```

when selecting the driver try "**vesa**"

continue through the configuration, i dont think you should need to change anything else, if its blank, leave it blank

when your back at the command line

```
startx
```

All right I did that, but I think I entered the wrong information (I just kept it on default) because I got around 10 error messages while last time it was only one. I have a HP pavilion dv6600 with AMD Turion 64 x 2. It's a 15.4 inch screen, and an Nvidia graphics card. If you need more information just ask. The error messages (the ones with EE in front) are
EE- AIGLX: Screen 0 (there is a dot in middle of the 0 but I couldn't find it on the keyboard) is not DRI capable
-xf86OpenSerial: Cannot open device /dev/gpmdata/no such file or directory
-Configured mouse: Cannot open input device
-Preinit device failed for input device "Configured Mouse" 
-xf86OpenSerial: Cannot open device /dev/input/wacon No such file or directory Error opening/dev/input/wacon : Invalid argument. It repeats this 3 more times 
Then it says on bottom "Fatal server error: Failed to initialize core devices
How do I fix these errors?

---

### Post by Digger78 on 2008-01-14
```
sudo nano /etc/X11/xorg.conf
```


find **Section "Module"**

delete the line that says 

```
Load "DRI"
```

then find and change (the bold text)

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	**"/dev/input/mice"**
```

press **ctrl+x**

then try **startx**

---

### Post by Jake90 on 2008-01-14
> **Digger78 said:**
> ```
sudo nano /etc/X11/xorg.conf
```


find **Section "Module"**

delete the line that says 

```
Load "DRI"
```

then find and change (the bold text)

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	**"/dev/input/mice"**
```

press **ctrl+x**

then try **startx**

I did that and now I get different error messages, they are
(EE) Problem parsing the config file
(EE) Error parsing the config file
and on bottom "Fatal server error no screens found.
How do I fix this? Also why is it so difficult to install Feisty? Is it my hardware?

---

### Post by Digger78 on 2008-01-14
go back and have a look ate the things you changed, you have probably left an unmatched quote

e.g.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	**"/dev/input/mice** 
```

notice that there is no** "** after mice

that would cause the parsing error.

If i'm not mistaken it should have told you where or why it failed (like a line number)

look over the file and make sure you have not accidentally deleted a quotation mark on any of the lines

---

### Post by Jake90 on 2008-01-14
> **Digger78 said:**
> go back and have a look ate the things you changed, you have probably left an unmatched quote

e.g.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	**"/dev/input/mice** 
```

notice that there is no** "** after mice

that would cause the parsing error.

If i'm not mistaken it should have told you where or why it failed (like a line number)

look over the file and make sure you have not accidentally deleted a quotation mark on any of the lines
It wasn't that, it was another mistake I made with the vesa thing you told me to do so I redid that and it works fine. The problem is now I am back to the same problems I had with Gutsy. Maybe I am doing something wrong in the system, but when I try to install ndiswrapper and ndiswrapper-utils I can't find it anywhere even when I try a file search (though the package manager says it is installed). Also I went to restricted drivers and tried enabling my video card but all it did was go Grey for a second then went back to the way it was before. Can I solve these problems or do I need to try another distribution?

---

### Post by Digger78 on 2008-01-14
OK, now we are getting somewhere ;)

does the wired connection work?

can you post the outputs from

```
lspci -v
```

```
iwlist scan
```

---

### Post by Jake90 on 2008-01-14
> **Digger78 said:**
> OK, now we are getting somewhere ;)

does the wired connection work?

can you post the outputs from

```
lspci -v
```

```
iwlist scan
```
My wired connection does work
lspci -v
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3080 [size=64]
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
        Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at f2300000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at f2586000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at f2589000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at f2587000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at f2589400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 30c0 [size=16]
        Capabilities: <access denied>

00:07.0 Audio device: nVidia Corporation Unknown device 055c (rev a1)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at f2580000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        Memory behind bridge: f2100000-f21fffff
        Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at 30f0 [size=8]
        I/O ports at 30e4 [size=4]
        I/O ports at 30e8 [size=8]
        I/O ports at 30e0 [size=4]
        I/O ports at 30d0 [size=16]
        Memory at f2584000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at f2588000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 30f8 [size=8]
        Memory at f2589c00 (32-bit, non-prefetchable) [size=256]
        Memory at f2589800 (32-bit, non-prefetchable) [size=16]
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f4000000-f5ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
        Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: f2200000-f22fffff
        Prefetchable memory behind bridge: 00000000f2000000-00000000f20fffff
        Capabilities: <access denied>

00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at f3000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at f2100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

02:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, medium devsel, latency 64, IRQ 7
        Memory at f2100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f2100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f2101000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f2101400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 1366
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f2200000 (64-bit, non-prefetchable) [size=16K]
        Memory at f2000000 (64-bit, prefetchable) [size=1M]
        Capabilities: <access denied>


iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by Digger78 on 2008-01-14
first thing to do is enable all repositories

synaptic package manager >settings> repositories

enable them all and download & install all your updates

---

### Post by Jake90 on 2008-01-14
> **Digger78 said:**
> first thing to do is enable all repositories

synaptic package manager >settings> repositories

enable them all and download & install all your updates

There was only one that wasn't but I enabled them all

---

### Post by Digger78 on 2008-01-14
OK, hopefully this will work, if it doesnt we will try ndiswrapper

this is taken from [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

open a terminal

```
wget http://www.fileden.com/files/2007/9/16/1436371/bcm43xx-0.3.2-internet.tar.gz
```

go into your home folder

. Right click the .tar.gz file and click Extract Here. It should extract into its own directory.

. Go into the bcm43xx-gtk-installer-* folder and double click the installer.py file and click the Run button when prompted.

. The installer should detect which installation method is appropriate for you.

. Click the install button to install the appropriate driver.

. Now enter your password and press the Enter key.

The driver should now be installed. Note that you may have to restart your system depending on which method you chose.

Reboot just to be sure

---

### Post by Jake90 on 2008-01-15
> **Digger78 said:**
> OK, hopefully this will work, if it doesnt we will try ndiswrapper

this is taken from [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

open a terminal

```
wget http://www.fileden.com/files/2007/9/16/1436371/bcm43xx-0.3.2-internet.tar.gz
```

go into your home folder

. Right click the .tar.gz file and click Extract Here. It should extract into its own directory.

. Go into the bcm43xx-gtk-installer-* folder and double click the installer.py file and click the Run button when prompted.

. The installer should detect which installation method is appropriate for you.

. Click the install button to install the appropriate driver.

. Now enter your password and press the Enter key.

The driver should now be installed. Note that you may have to restart your system depending on which method you chose.

Reboot just to be sure
Thanks everything is working!

---

