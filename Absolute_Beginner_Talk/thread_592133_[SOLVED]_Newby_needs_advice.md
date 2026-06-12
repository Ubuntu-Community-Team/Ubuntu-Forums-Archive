---
title: "[SOLVED] Newby needs advice"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by jd3010 on 2007-10-26
Hello,
Questions from a complete newby :

I deceided to jump, and installed a complete version of Ubuntu 7.10 on my TC1000, I was getting very tired of the slow Tablet XP .... (clean install)

Installation worked perfectly, but I do have problems installing drivers. As I am a complete new in Linux, I do need some help.

1. Booting  is not as quick as I thought  and lauching Porgrams is quite slow also.... What can I do to speed up the system. booting to the login screen takes about 70seconds. Is htis normal ? When the PC starts and before the login screen pops up the screen is completely bizarre (like the TV when you unplugged the Antenna).

2. How can I see which driver version is installed, f.ex Video and Network ?

2. I have been searching the Net and found the files I need, but I do not know how to install them.
Video : NVIDIA-Linux-x86-71.86.01-pkg1.run have been found but I always receive an error message even with sudo command and ALT-F2 and the run .... any idea ?

3. I have another driver tc1k-1.1.tar.gz   how can I install it ? the Install prog  does not list it eventhough I have downloaded onto the PC, do I have to copy it in a special folder ??

thanks for your help,

John

---

### Post by SunnyRabbiera on 2007-10-26
well with your system install did you use the normal installation process?
did you check how much swap memory you have?
you can check out your swap memory by adding a application, the applet i can suggest is the system monitor applet, just right click on the top panel (or bottom if you wish) and click "add to panel" like you do in windows.
the "add to panel" screen will pop up and scroll down to "system and hardware"
from here you can drag and drop the "system monitor" icon to wherever you wish.
after this you will have to modify your new app a bit before its any use to you, no worries, just right click on your newfound app and right click and select "preferences" and another little window will pop up
just click on the boxes that you see that are labeled "memory" and "swap space"
after that you can close the windows, both have easy to use close buttons that are very easy to spot.
after you are done closing those windows just move your mouse over both the memory and swap monitors (the memory is green and the swap is purple)
just tell me your output and we can work from there.

---

### Post by RomeReactor on 2007-10-26
Hi. Maybe looking at the system log can help determine what's causing the slowness of your system; you can find it in "System->Administration->System Log". Look in the **Xorg.0.log** there, in particular for messages starting with (WW) or (EE). Also open your System Monitor (System->Administration->System Monitor) and see if anything is taking up too much of the processor or memory.

To find out which driver your video card is using enter in the terminal (Applications->Accessories->Terminal):
```
sudo lshw -C display
```
(look in the **configuration:** line). And for the network drivers:
```
sudo lshw -C network
```

Most program and driver installation in Ubuntu is done by accessing repositories, which are large pools of software on servers, using programs like Add/Remove (Applications->Add/Remove) and Synaptic (System->Administration->Synaptic), or through the terminal with text based programs like apt-get or aptitude. The easiest way to install the proprietary nVidia drivers (which allow you to use desktop effects and play 3D games) is to go to "System->Administration->Restricted Drivers Manager" and checking the case for your nVidia card there.

What is the **tc1k-1.1.tar.gz** driver for?

---

### Post by jd3010 on 2007-10-26
Hi, Impressive fast reply ...

Thanks for the clear indications.

Install from scratch, used a CDrom downloaded from Ubuntu 7.10.

Memory: 38%  in use by prog,  55% in use as cache.

Swap files : 0 %

memory total 480 MB

John

---

### Post by SunnyRabbiera on 2007-10-26
so are you getting no data from the swap? or is it at 0% use?
this might be your issue if you didnt format a swap.

---

### Post by jd3010 on 2007-10-26
Hi,

System Log:

XX Directory /usr/share/fonts/x11/cyrillic   does not exit

WW system lacks support for changing MTRRs

EE AIGLX : Screen 0 is not DRI capable
EE Synaptics Touchpad no synaptics touchpad detected and no repeater device 
EE Synaptic Touchpad unable to query/initilase
EE PreInit for Input device (Synaptics ....

---------------

Result of Video Product NV11 Geforce 2   version b2 

I will try the Nvidia ... and let you know.

----
Network Atmel wireless ... version 11 .  How do I know if this is the latest version ... I found atmel-firmware-1.3-1fc3.noarch.rpm on the internet ?
-----

----

Can I add in Synaptec  other Repositories or the only 2 default one are the only ones.

The tc1k-1.1.tar.gz file should be a driver for the touch Pen (Tablet PC)

---

### Post by jd3010 on 2007-10-26
I think I did not make a Swap ... How do I creat one ?

---

### Post by mali2297 on 2007-10-26
70 seconds boot time doesn't sound extreme to me. 

If you want to speed up program launching, the readahead daemon **preload** might help. You can find it in Synaptic. (Search by name, also make sure that the universe repository is enabled.)

---

### Post by jd3010 on 2007-10-26
Just saw in the Help file "mkswap"  

Where should I create it ? and how big etc ....  30 GB HD 480 MB memory..

Thanks

---

### Post by RomeReactor on 2007-10-26
First see if you already have a swap partition:
```
cat /etc/fstab
```

---

### Post by jd3010 on 2007-10-26
> **SunnyRabbiera said:**
> so are you getting no data from the swap? or is it at 0% use?
this might be your issue if you didnt format a swap.
Just saw in the Help file "mkswap"

Where should I create it ? and how big etc .... 30 GB HD 480 MB memory..

Thanks

---

### Post by jd3010 on 2007-10-26
Hi,

System Log:

XX Directory /usr/share/fonts/x11/cyrillic does not exit

WW system lacks support for changing MTRRs

EE AIGLX : Screen 0 is not DRI capable
EE Synaptics Touchpad no synaptics touchpad detected and no repeater device
EE Synaptic Touchpad unable to query/initilase
EE PreInit for Input device (Synaptics ....

---------------

Result of Video Product NV11 Geforce 2 version b2

I will try the Nvidia ... and let you know.

----
Network Atmel wireless ... version 11 . How do I know if this is the latest version ... I found atmel-firmware-1.3-1fc3.noarch.rpm on the internet ?
-----

----

Can I add in Synaptec other Repositories or the only 2 default one are the only ones.

The tc1k-1.1.tar.gz file should be a driver for the touch Pen (Tablet PC)

---

### Post by jd3010 on 2007-10-26
> **RomeReactor said:**
> First see if you already have a swap partition:
```
cat /etc/fstab
```
The result is a lot of info

I guess /dev/hda5  is none SWAP sw 0 0 

so  guess none

---

### Post by RomeReactor on 2007-10-26
> /dev/hda5 none SWAP sw 0 0

Yes, that's the swap partition, so you don't need to create another; in the "Resources" tab in system monitor, if should read "Used swap: XX of YY", where XX is the amount being used and YY the total size of the swap partition. So the problem is probably elsewhere.

Can you tell us more details about your PC (RAM, processor, etc)?

---

### Post by jd3010 on 2007-10-26
> **RomeReactor said:**
> Yes, that's the swap partition, so you don't need to create another; in the "Resources" tab in system monitor, if should read "Used swap: XX of YY", where XX is the amount being used and YY the total size of the swap partition. So the problem is probably elsewhere.

Can you tell us more details about your PC (RAM, processor, etc)?
But it says "None" ?  

I also never typed the command mkswap or swapon ? Do I have to do this ?

1Gmghz,  30 GB HD,  480 MB memory..

---

### Post by jd3010 on 2007-10-26
I just typed free -m

and got the result that mem is 479  used 446 
Swap is 1223 used 0

Hope this helps to solve the prob .

---

### Post by mali2297 on 2007-10-26
I think it's quite normal that the system is a little bit slow if you only have 480 MB memory. It shouldn't be extremely slow though but perhaps somewhat slower than XP on the same machine, experiences differ.

I already suggested **preload**. Another thing you could try is XFCE instead of Gnome:
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by RomeReactor on 2007-10-26
Your swap seems OK.

---

### Post by jd3010 on 2007-10-26
Ok will try, but I am really new ... just installed it yesterday....

Do yyou have any ideas on the swap file prob ... previous threads ?

Thanks

---

### Post by jd3010 on 2007-10-28
Reinstalled everthing from Scratch and SWAP file is working fine now.  
Thansk to all=D>

---

