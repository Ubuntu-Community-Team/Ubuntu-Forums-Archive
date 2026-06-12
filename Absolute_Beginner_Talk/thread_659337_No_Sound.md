---
title: "No Sound"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by unknown512 on 2008-01-05
I am recieving no sound, and am bieng told that i do not have GStreamer plugins, i don't know if i have them or not, i would appreciate help, Thanks

here is my lspci

```
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.1 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a4)
00:0e.2 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a5)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
02:04.0 Audio device: Creative Labs SB X-Fi
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
```

---

### Post by Ub1476 on 2008-01-05
Post the output of this:

```
gksudo asoundconf list

```

---

### Post by icheyne on 2008-01-05
Your Creative SB X-Fi soundcard is not supported by Alsa, the main Linux sound system.

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)
"Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time."

There are some drivers, but I believe they are for 64 bit processors only.

This guy claims to have got it working: [http://ubuntuforums.org/showthread.php?t=649908](http://ubuntuforums.org/showthread.php?t=649908)

---

### Post by unknown512 on 2008-01-05
```
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences
```.

I don't know what it means, but nothing came up other than that

:confused:

---

### Post by balaknair on 2008-01-05
open synaptic and search for gstreamer
if it has been installed the little check box next to it will be green
If not just click the little box and click apply
it'll install all dependencies as well
This should fix the gstreamer part of your problem

---

### Post by unknown512 on 2008-01-05
icheyne, thanks, well taht stinks, i guess im just gonna have to go without sound for a while =/

](*,) ](*,) ](*,)

[-(

---

### Post by Ub1476 on 2008-01-05
After pasting the command you should be able to write in your password (sudo/admin).

> **unknown512 said:**
> icheyne, thanks, well taht stinks, i guess im just gonna have to go without sound for a while =/

](*,) ](*,) ](*,)

[-(

You're sure you got no onboard sound device?

---

### Post by unknown512 on 2008-01-05
> open synaptic and search for gstreamer
if it has been installed the little check box next to it will be green
If not just click the little box and click apply
it'll install all dependencies as well 

Im not sure what you mean, wheres synaptic?

---

### Post by icheyne on 2008-01-05
Try the steps on that last link I gave you. It might work.

If you are using a desktop, and you seem to be from your lspci output, why not buy a cheapo used soundcard from eBay or rip one out of an old machine or do as Ub1476 suggests and check for on-board sound.

---

### Post by unknown512 on 2008-01-05
> after pasting the command you should be able to write in your password (sudo/admin).

Well i couldn't =/

---

### Post by agim on 2008-01-05
What I would do is go to a command line and type:

  sudo apt-get install gstreamer

Then type:

  sudo apt-get update

---

### Post by unknown512 on 2008-01-05
> You're sure you got no onboard sound device?

Yeah, because i bought the computer when it came with it :lolflag:

---

### Post by Ub1476 on 2008-01-05
> **unknown512 said:**
> Im not sure what you mean, wheres synaptic?

Synaptic is Ubuntus packagemanager. It's located in System>Admininstration. You probably know it better as add/remove. However if you would like to install flash/java/codecs etc it's easier just to install "ubuntu-restricted-extras".

---

### Post by unknown512 on 2008-01-05
> What I would do is go to a command line and type:

sudo apt-get install gstreamer

Then type:

sudo apt-get update



```
unknown512@unknown512:~$ sudo apt-get install gstreamer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer
```

nope. cant

---

### Post by Ub1476 on 2008-01-05
> **unknown512 said:**
> Yeah, because i bought the computer when it came with it :lolflag:

Still, just to be sure, post the command again:

```
gksudo asoundconf list

```

It's better than nothing:lolflag:

> **unknown512 said:**
> nope, can't

```
sudo apt-get install ubuntu-restricted-extras
```

Or search for it in Add/remove / Synaptic.

It won't help much if you got no sound device working anyway though..

---

### Post by unknown512 on 2008-01-05
```
unknown512@unknown512:~$ sudo apt-get install ubuntu-restricted-extras
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

:confused:

---

### Post by unknown512 on 2008-01-05
```
he volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
```

BTW. this is the error message i get when i try to enable sound 

:lolflag:

---

### Post by unknown512 on 2008-01-05
```
unknown512@unknown512:~$ gksudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.
```

:confused:

---

### Post by unknown512 on 2008-01-05
I also have installed ALL packages avaible for the GStreamer in the Synaptic Package Manager.

:popcorn:

---

### Post by rkd on 2008-01-05
I know you said your computer has no integrated audio, but from your lspci output, it looks like your motherboard has the MCP55 chipset, and all but the budget version of that chipset support integrated audio. Have you looked on the back of the computer to see whether there are audio jacks over by the LAN and USB jacks?  If so, you might be able to activate them by removing the Creative sound card from the computer.

If you really, truly don't have integrated audio, please excuse me for butting in.

---

### Post by jryprt on 2008-01-05
> **unknown512 said:**
> ```
unknown512@unknown512:~$ gksudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.
```

:confused:

```
jerry@jerry-desktop:~$ gksudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
ICH6
jerry@jerry-desktop:~$ 

```

Here is mine did you copy all the info. My card ICH6

---

### Post by Ub1476 on 2008-01-05
> **unknown512 said:**
> ```
unknown512@unknown512:~$ sudo apt-get install ubuntu-restricted-extras
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

:confused:

Close Synaptic and/or Add/remove and/or Update Manager, then run the command.

> **unknown512 said:**
> ```
unknown512@unknown512:~$ gksudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.
```

:confused:

You should get a pop-up asking for your super-user (admin/root) password.

This is my output after I have entered my password:

```
(gksudo:10256): librsvg-WARNING **: sourceGraphic not found

Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkWidget::cursor-color' of type `GdkColor' from rc file value "((GString*) 0x8115550)" of type `GString'
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Intel

```

---

