---
title: "Installation hangs on HP dv9014 laptop"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by tntc1978 on 2006-12-19
I'm experiencing trouble booting the live cd, and when I finally get it to boot, I'm having trouble installing Ubuntu. It hangs during the procedures. I've seen some threads that state that I can put in some parameters to make it work, but which parameters, where and how?

Thanks for all the help I can get.

My Hardware:
- AMD Turion&#8482; 64 X2 mobil teknologi TL-50
- 1024 MB DDR2 667 MHz (2 x 512 MB)
- 160 GB (2 x 80 GB) EIDE-harddisk, SATA 5400 o/m
- 17"" WXGA+ High Definition BrightView Widescreen
- NVIDIA® GeForce&#8482; Go 7600 256 MB
- FireWire (IEEE1394)
- Lightscribe Super Multi DVD Writer (+/-r +/-rw)
- 802.11a/b/g WLAN
- HP Mobile Remotecontrol
- 5-i-1 integreret Digital mediareader 
- HP Pavilion WebCam with integrated mike.

---

### Post by milton1 on 2006-12-19
Try the alternate install cd. Not as pretty, but I have found it to be much less prone to difficulty.

---

### Post by tntc1978 on 2006-12-19
> **milton1 said:**
> Try the alternate install cd. Not as pretty, but I have found it to be much less prone to difficulty.

I'll do that and post my endevours back here. Why isn't it as pretty? Is it only the installation that isn't pretty?

---

### Post by milton1 on 2006-12-19
By not as pretty, I mean literally, not as visually attractive. The alternate cd installer does not run X. Nothing but simple text on primary colors :)

---

### Post by tntc1978 on 2006-12-19
Ohh I was fearing, that you were refering to the final installation... So far all seems to be going well I'm 90% into the installation and no hanging/crashing and the like... 
Uhh 97% got to go :D

---

### Post by tntc1978 on 2006-12-19
It seemed to help a bit. 

The installation is complete (I'm now dual-booting with XP), **but** now the system hangs when I try to boot it. Furthermore the splash-screen is Grey :-? Any connection? How do I get it to boot every time?

Thanks a bunch.

NB I've made it into Ubuntu once out of 4 boots.

---

### Post by tntc1978 on 2006-12-19
When I boot as recovery mode it stalls:

First time it stops here:
[34.356013] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

Second time it stops here:
* Starting kernel event manager

Third time it stops here:
[19.142478] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0

Fourth time it stops here:
* Starting kernel event manager

Fifth time it stops here:
* Starting kernel event manager

Any thoughts?

---

### Post by tntc1978 on 2006-12-19
sixth time:
[19.142478] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0

seventh time:
* Setting up console font and keymap

eigth time:
* Starting kernel event manager 
](*,)

---

### Post by tntc1978 on 2006-12-19
anyone?

---

### Post by Kobalt on 2006-12-19
Hello,
On a HP dv6000 laptop I had to use the option "noapic nolapic" at boot to get a working Ubuntu installation. Before the install start, at the first boot menu, press F6 to get access to the launch option and just add noapic nolapic at the end of the line...

---

### Post by tntc1978 on 2006-12-19
OK, do I need to make a fresh install then?

---

### Post by Kobalt on 2006-12-19
> **tntc1978 said:**
> OK, do I need to make a fresh install then?
No you can try to manually edit the menu.lst file. To do so, access a command line after booting your computer (in recovery mode then) and type this : 
```
sudo gedit nano /boot/grub/menu.lst
```
Find the end section were your kernels are listed (after the line "## ## End Default Options ##") and add the options at the end of your kernel line, that should look like this afterwards : 
> kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash noapic nolapic
Then save by pressing Shift+X, exit and reboot.

You will have to add these options at each kernel update though, since you didn't add it before install.

Edit: the command is wrong, I know, silly mistake corrected bellow.

---

### Post by tntc1978 on 2006-12-19
Merci Kobalt, I'll write back here as soon as I can put it into the menu. But first I need to get past all the places where my machine stops. But it has been posible before, so I guess I just need to reboot until I get to that point :-(

---

### Post by Kobalt on 2006-12-19
De rien ;)

---

### Post by tntc1978 on 2006-12-19
I get this:
> cannot open display:
Run 'gedit --help' to see a full list of available cammand line options.

When I try this:
```
sudo gedit nano /boot/grub/menu.lst
```

---

### Post by tntc1978 on 2006-12-20
It seems like gedit don't know the command. or I'm doing it wrong... Any input here?

---

### Post by Kobalt on 2006-12-20
So sorry, my mistake, I typed the command wrong... :( You should try this, it'll work : 
```
sudo nano /boot/grub/menu.lst
```
Again so sorry...

---

### Post by tntc1978 on 2006-12-20
It works, thanks a bunch Kobalt.

Some info to future readers:
It is posible to put this (noapic nolapic) booting parameter in when grub is prompting. All you do is press "e" and put it into the line that resembles the one Kobalt wrote in #12

This makes it posible to boot, and then make sure you edit the menu file.

Thanks again Kobalt

---

### Post by Kobalt on 2006-12-21
You're welcome !

---

### Post by Cywolf1 on 2007-08-10
Copy of another post I made...just getting the word out to those watching !!!
------------------------------------------------------------------------------------------------

To all folks out there looking for an APIC/ACPI solution for Ubuntu AMD boot lockup problems:

My Hardware:
HP dv6324us
Gutsy Distro (Tested with feisty, seems to work)
2.6.22 Kernel
AMDx2 - 1.6
Nvidia 6150
Nvidia chipsets (All the goodies on HP)
bcm43xx driver
etc...

After many weeks of searching through kernel documentation, I think I may have found a permanent soluton to the kernel boot problem. Most people can temp. resolve the problem with either noapic noacpi or other kernel options that disable or impair the apic/acpi on the system. Fear no more the loss of IRQs, use more than 2 usb devices all at once, and free yourself from the random loss of your wireless cards............... okay so now that everyone is anxious...simply append this to the kernel boot option

pci=conf1

so for the ubuntu (linux) rookies...
when grub boots, press esc to stop boot on a grub menu, press e on the kernel line, and at the end of the line append "pci=conf1" without the quotes....then press enter, and then b, and witness the glory.

It almost seemed too simple, and I nearly cried when the system booted up faster and smarter. I've got all my APIC set to fasteoi and some on edge triggered, just like it should be. I've also got all 8 USB ports found, full working display, wireless, nics, USB 2.0, and even my battery stats appear to be more accurate. I am also using compiz and it's running ten times faster (cause the kernel is not tweaking out). Oh it's sheer beauty....I rarely post, but I figured it was time to share the love. I know that I will be making so many folks with HP dv6000 series or other HP model owners supremely happy!! I know I AM... YEAH. Hopefully the fix works on other platforms with similar issues.


Cyber///olf

Posted here as well -->
[http://ubuntuforums.org/showthread.php?p=3164902&posted=1#post3164902](http://ubuntuforums.org/showthread.php?p=3164902&posted=1#post3164902)

---

