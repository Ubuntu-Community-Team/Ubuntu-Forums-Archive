---
title: "trouble with nvidia driver"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by natialos on 2007-08-08
Hello. I'm a complete newbie when it comes to working with terminals, etc, so bear with me.
 I'm using Feisty, and I'm having trouble getting the Nvidia driver to work. I have the driver installed, and I have the linux restricted modules, but when I change my xorg.conf to say nvidia, and then do ctrl+alt+bkspc, my computer just sort of.... doesn't work. The screen changes a few times, and then it goes black and stays there, sort of how it did in screensaver mode before I got the actual screensaver to work. So I reboot it, and then it loads as normal up to the point of the ubuntu loading screen, and then I'm shifted over to the terminal screen that I usually would get to by pressing Crtl+Alt+F1, and there is a prompt asking for my login there. Right above the login prompt is a bit of text, and the two things that stuck out to me were "unable to locate RSDP" and "no resume image"
If I press Ctrl+Alt+F7, I just get a blank screen with a flashing cursor at the top.
Please help. :(

---

### Post by overdrank on 2007-08-08
> **natialos said:**
> Hello. I'm a complete newbie when it comes to working with terminals, etc, so bear with me.
 I'm using Feisty, and I'm having trouble getting the Nvidia driver to work. I have the driver installed, and I have the linux restricted modules, but when I change my xorg.conf to say nvidia, and then do ctrl+alt+bkspc, my computer just sort of.... doesn't work. The screen changes a few times, and then it goes black and stays there, sort of how it did in screensaver mode before I got the actual screensaver to work. So I reboot it, and then it loads as normal up to the point of the ubuntu loading screen, and then I'm shifted over to the terminal screen that I usually would get to by pressing Crtl+Alt+F1, and there is a prompt asking for my login there. Right above the login prompt is a bit of text, and the two things that stuck out to me were "unable to locate RSDP" and "no resume image"
If I press Ctrl+Alt+F7, I just get a blank screen with a flashing cursor at the top.
Please help. :(

Ok let me see if I understand you correctly have the nvidia driver installed and you are using the restricted drivers also? What is the model of the graphics you are these issues with? :confused:

---

### Post by natialos on 2007-08-08
Are you referring to what graphics card I have?
I believe it's one of the 9000 series. I forget which one exactly.

---

### Post by alienexplorers on 2007-08-08
Why did you not try the ENVY script at:
> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
I have used this and it setup my drivers perfectly.

---

### Post by jake16424 on 2007-08-08
> **natialos said:**
> Are you referring to what graphics card I have?
I believe it's one of the 9000 series. I forget which one exactly.
ahh, use Everest, well i dont know if it will work with ubuntu, but it works with windows, if your doing a dual boot system. so yeah, it will have all the information you could ever need on your hardware and software. =)

---

### Post by overdrank on 2007-08-08
> **natialos said:**
> Are you referring to what graphics card I have?
I believe it's one of the 9000 series. I forget which one exactly.

HI you can find out which model it is with the command in the terminal 
```
lspci
```
Terminal is located under applications, accessories, terminal

---

### Post by iAndrew on 2007-08-08
I've tried this myself, but honestly I don't see a video card.

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0402 (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by overdrank on 2007-08-08
> **iAndrew said:**
> I've tried this myself, but honestly I don't see a video card.

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
[COLOR="Red"]01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0402 (rev a1)[/COLOR]
03:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

HI it is highlighted and you need to update your pciids you can do this in the terminal with the command
```
sudo update-pciids
```

---

### Post by natialos on 2007-08-08
> **jake16424 said:**
> ahh, use Everest, well i dont know if it will work with ubuntu, but it works with windows, if your doing a dual boot system. so yeah, it will have all the information you could ever need on your hardware and software. =)
Sorry, I don't have Windows on my machine.

I tried envy now, and it ended up with the exact same thing I've been getting before:

ACPI: Unable to locate RSDP
Loading, please wait...
kinit:name_to_dev_t (/dev/disk/by-uuid/7c365f33-f1d4-482a-aa3b-76eac48e6a47)= sda2(8,2)
kinit:trying to resume from 7c365f33-f1d4-482a-aa3b-76eac48e6a47
kinit:no resume image, doing normal boot

and then a login prompt.

And I have a GeForce FX 5200

---

### Post by natialos on 2007-08-09
Any ideas? Anyone?

---

### Post by overdrank on 2007-08-09
> **natialos said:**
> Any ideas? Anyone?

Hi maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=514513&highlight=GeForce+FX+5200](http://ubuntuforums.org/showthread.php?t=514513&highlight=GeForce+FX+5200)
Good luck!

---

### Post by natialos on 2007-08-09
it seems to me I'm having some trouble with the nvidia module, but no idea how to fix it.
When I'm booting up, I get this message:
SIS630comp bus not detected module not inserted

---

### Post by natialos on 2007-08-09
> **overdrank said:**
> Hi maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=514513&highlight=GeForce+FX+5200](http://ubuntuforums.org/showthread.php?t=514513&highlight=GeForce+FX+5200)
Good luck!

Ech.... but that's exactly what I HAVE done, but whenever I restart X/my computer, it doesn't work right.

---

### Post by splintercellguy on 2007-08-09
Have you tried using Envy? [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by overdrank on 2007-08-09
> **natialos said:**
> Ech.... but that's exactly what I HAVE done, but whenever I restart X/my computer, it doesn't work right.

Ok sorry I was just offering help. If you get the error of xorg then try and configure it. If you search for that graphics card in the forums you will see that some people have trouble with that card and some don't. :(

---

### Post by natialos on 2007-08-09
> **splintercellguy said:**
> Have you tried using Envy? [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
yes, I have tried envy

---

### Post by natialos on 2007-08-09
> **overdrank said:**
> Ok sorry I was just offering help. If you get the error of xorg then try and configure it. If you search for that graphics card in the forums you will see that some people have trouble with that card and some don't. :(

Sorry, I didn't mean to bit your head off.
I'm just SO frustrated at this.

---

### Post by natialos on 2007-08-09
Whenever I try to run this command, as per one walkthough I found on getting the nvidia drivers to work:
> sudo sh NVIDIA* -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`

I get this error message:

> Unable to load the kernel module 'nvidia.ko'. This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as fivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s).
Please see the log entries 'kernel module load error' and 'kernel messages' at the end of the file '/var/log/nvidia_installer.log' for more information.

---

### Post by JonathanWright on 2007-08-30
Here's what I had to do with gutsy (alpha 5) on a dell m4300:

Completely remove everything in synaptic which says nvidia.

Get the 100.14.11 release from [www.nvidia.com](www.nvidia.com). Install it.

Reinstall the gutsy packages for the wireless network card. These trash the nvidia again.

Manually remove again everything you can find in synaptic saying nvidia. Do this one file at a time using "sudo rm [filename]" at a terminal prompt. 

Once again install the 100.14.11 release from [www.nvidia.com](www.nvidia.com).

Useful commands: 
to get a text prompt: alt-f1 
to stop/start the window manager:
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
to try starting xwindows after editing xorg.conf
sudo nano /etc/X11/xorg.conf
startx
... try replacing the "nvidia" with "vesa" to see if you can avoid the problem in the interim

Good luck!

---

### Post by BerlinOliver on 2007-09-02
..sorry, i wanted to delete my reply, but i didn't worked...

---

