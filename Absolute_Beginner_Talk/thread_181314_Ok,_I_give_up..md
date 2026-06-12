---
title: "Ok, I give up."
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Darvos Omcon on 2006-05-24
Im asking for help. Ive cruised the forums as much as I care to.
Im getting the display probably isnt configured right error. After that, it gives me a text login and text from there. Gnome wont work. I tried using "sudo dpkg-reconfigure xserver-xorg" I tried using different drivers for it. I used nv, vesa, and vga. I can't seem to get it to work. I need help. Im very new to linux. And I just installed it today. Ive played with DSL a little, but other than that, no experience.

Specs:
Celeron 1.7Ghz
1Gb Ram
40 GB HD, 32-Gb windows partition. 5 Gb Ubuntu partition.
nVidia Geforce 5500 oc PCI card.

I think the problem might lie in a conflict between my integrated graphics, and the graphics card. If you can, guys, Id really appreciate some help on this one. Im totally lost.
Thanks, 
Darvos

---

### Post by Mustard on 2006-05-24
I'm surprised that 'vesa' drivers didn't work.  What would be handy is some information from your logs detailed the errors.  What machine are you using for posting on the forums atm?  Are you trying to run Breezy Badger (5.10) or Dapper Drake (6.06)?

---

### Post by RudolfMDLT on 2006-05-24
[QUOTE=Darvos Omcon]
nVidia Geforce 5500 oc PCI card.

I think the problem might lie in a conflict between my integrated graphics, and the graphics card. If you can, guys, Id really appreciate some help on this one. Im totally lost.
Thanks, 
Darvos[/QUOTE]

I'm no guru on graphics in Linux, but if in any way you could get to this link :
[http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html)
These are the latest Nvidia drivers for linux - 22 May 2006.

There shouldn't be a conflict between on board Graphics and the PCI card, but if you believe this is the case; Under chip set configuration in your BIOS you can enable on board graphics. Then take out your PCI card and just use the on board version. See if you can use the on board Graphics until you sorted out the problem with the PCI card.

First try to swap display adapters and then go hunting for drivers.

Goodluck!

---

### Post by Mustard on 2006-05-24
Just searching the forums I found something interesting here too..
[http://www.ubuntuforums.org/showthread.php?t=33142](http://www.ubuntuforums.org/showthread.php?t=33142)

It seems you might be able to blacklist the modules for the onboard graphics, to stop them from loading (assuming thats even the issue in this problem.  The symptoms of your problem differ from this one.)

---

### Post by Darvos Omcon on 2006-05-24
Well, I have two computers in the same room. One of them I am trying out Linux on.(Obviously.)
Sorry about the lack of info. I am using Breezy 5.10. It's a dual boot, so Im going to boot into windows and remove the PCI card, and all that, then try to reconfigure xserver. That link to the Nvidia website didnt list my model number, but Ill look around their site and see if I can find it. But all that comes tomorrow. Its getting kind of late here, and I have school tomorrow. Thanks for the replies, guys. Ill be sure to try it. Ill update tomorrow.

---

### Post by Mustard on 2006-05-24
Ok, sounds like a good idea to start fresh tomorrow. :)

If you got two machines then you might also try hopping on to the IRC support channel at irc.freenode.net in #ubuntu on one machine and see if you can get someone in there to help you with setting it up.  I've read over a few threads in the forums already that have some ideas on things to try.

---

### Post by confused57 on 2006-05-24
Here's a thread that may help:

[http://www.ubuntuforums.org/showthread.php?t=173653](http://www.ubuntuforums.org/showthread.php?t=173653)

I think it may be similar to the thread Mustard mentioned, but it could help...

---

### Post by Phlosten on 2006-05-24
If you have two graphics cards, one being onboard and the other being a seperate card, dpkg-reconfigure xserver-xorg will almost certainly be defaulting to the PCI bus value of the onboard card even though your monitor is connected to the seperate card.

Basically you need to work out the PCI bus number of the graphics card you want to use. At the command prompt type 'lspci' and look for your graphics card in the this. Mine is 
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

Now if I have this right the PCI bus number that xorg.conf uses is the numbers after the 0000: , it is slightly different because of something to do with hex, i forget. But in my case in my '/etc/X11/xorg.cong' file I have:
        BusID           "PCI:1:0:0"

You can edit this file manually to change the BusID number 'sudo nano /etc/X11/xorg.conf'.

---

### Post by Darvos Omcon on 2006-05-25
Thanks for your help guys, sorry so late for the update. I got that working, now I have mouse problems. :(
See [here]("http://ubuntuforums.org/showthread.php?t=181884").

---

