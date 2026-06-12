---
title: "Ubuntu fills my memory like crazy - what can I do?"
date: 2013-05-26
forum: Any Other OS
---

### Post by zesterer on 2013-05-26
Hi,

I recently got a new laptop. Its quite fast, and its a good laptop, and it has 8 Gb of RAM.

The problem I have is that when starting up Ubuntu, and opening Google Chrome, playing a few youtube videos, going on a few websites, my RAM usage has jumped up to 60%, or so says the memory indicator I have on the top panel. My computer starts to get slow if I do anything massive as well - If I use a virtual machine for a bit then close it, the memory stays high and the computer stays slow. Quickly and Glade UI Designer also cause a lot of this.

At the moment, I am using unity and compiz with a lot of effects turned on. I switched over to Gnome 2.x without, and it seemed to be fine, although then again I didnt exactly test it. I like Unity though, I dont want to switch.

My question is - what can I do to improve this? Is there some handy little background daemon software that automatically cleans the caches or something? Because I would have thought that Ubuntu (technically I use Mint 14, but its based heavily off Ubuntu and Ive customised it so much that it pretty much is Ubuntu) could handle with 8 Gb on RAM on this laptop...

Its just a little annoying that, although Google Chrome is a very intensive program in terms of memory, the CPU Monitor is telling me that it alone with only 4 tabs open, one with youtube, is using 1.9 Gb of RAM...


Thanks for any suggestions, I really appretiate them.

Barry Smith

P.S: Dont feel too pressed to answer, its not an urgent issue. Its just annoying that I have to reboot every few hours because my computer gets slow...

---

### Post by hansdown on 2013-05-26
Hi zesterer.

Could you please post what graphics card you are using?

---

### Post by Perfect Storm on 2013-05-27
Moved to Other OS/Distro Support.

---

### Post by robert shearer on 2013-05-27
> **Artificial Intelligence said:**
> Moved to Other OS/Distro Support.

Eh...???   What 'Other Distro" did the o/p mention...? They're using Ubuntu...

---

### Post by DJWYMAN on 2013-05-27
> **robert shearer said:**
> Eh...???   What 'Other Distro" did the o/p mention...? They're using Ubuntu...

the OP says he is using mint.  

OP,

as far as your memory problem do you have a swap partition by any chance?  If not that may help.

---

### Post by OrangeCrate on 2013-05-27
> **zesterer said:**
> Hi,

I recently got a new laptop. Its quite fast, and its a good laptop, and it has 8 Gb of RAM.

The problem I have is that when starting up Ubuntu, and opening Google Chrome, playing a few youtube videos, going on a few websites, **my RAM usage has jumped up to 60%**, or so says the memory indicator I have on the top panel. My computer starts to get slow if I do anything massive as well - If I use a virtual machine for a bit then close it, **the memory stays high** and the computer stays slow. Quickly and Glade UI Designer also cause a lot of this.

At the moment, I am using unity and compiz with a lot of effects turned on. I switched over to Gnome 2.x without, and it seemed to be fine, although then again I didnt exactly test it. I like Unity th[SIZE=2][/SIZE]ough, I dont want to switch.

My question is - what can I do to improve this? Is there some handy little background daemon software that automatically cleans the caches or something? Because I would have thought that Ubuntu (technically I use Mint 14, but its based heavily off Ubuntu and Ive customised it so much that it pretty much is Ubuntu) could handle with 8 Gb on RAM on this laptop...

Its just a little annoying that, although Google Chrome is a very intensive program in terms of memory, the CPU Monitor is telling me that it alone with only 4 tabs open, one with youtube, is using 1.9 Gb of RAM...


Thanks for any suggestions, I really appretiate them.

Barry Smith

P.S: Dont feel too pressed to answer, its not an urgent issue. Its just annoying that I have to reboot every few hours because my computer gets slow...

A great article on disk caching:

**Help! Linux ate my RAM!**

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by zesterer on 2013-05-27
I do have swap space, and I have set up hibernation with it. However, I think it might be a bit small, at only 6 Gb or something :S I havent tested hibernation in a while though...

EDIT: My home folder is encrypted, as is my swap space if that makes any difference...

With regards to my graphics card, here is my system summary...

> -Computer-Processor        : 4x Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz
Memory        : 5979MB (3524MB used)
Operating System        : Linux Mint 14 Nadia
User Name        : barry (Barry Smith)
Date/Time        : Mon 27 May 2013 09:39:17 BST
-Display-
Resolution        : 1366x768 pixels
OpenGL Renderer        : Mesa DRI Intel(R) Ivybridge Mobile 
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel PCH
-Input Devices-
 Power Button
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
 2.4G Wireless Mouse
 Video Bus
 Video Bus
 Dell WMI hotkeys
 Laptop_Integrated_Webcam_HD
 HDA Intel PCH HDMI/DP,pcm        : 3=
 HDA Intel PCH Mic
 HDA Intel PCH Headphone
 ETPS/2 Elantech Touchpad
-Printers (CUPS)-
Photosmart-C4200-series        : <i>Default</i>
-SCSI Disks-
ATA ST1000LM024 HN-M
MATSHITA DVD+-RW UJ8D1
Generic- xD/SD/M.S.



Is this any help? I found that the memory is fine if I use Epiphany web browser and other lightweight software, but its annoying as this is a pretty good computer and Mint really should be able to cope with it... :(

Thanks for all the replies,

Barry Smith

---

