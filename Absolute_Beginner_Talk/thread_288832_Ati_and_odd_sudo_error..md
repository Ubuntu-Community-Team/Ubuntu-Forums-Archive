---
title: "Ati and odd sudo error."
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-10-30
Hi there,

Anyone know when there will be a fix for the Ati FGLRX driver for edgy? Jusst asking for interest sake, my slow fps is really annoying me.

Anyhow, After the upgrade to Edgy i get this error(I used Gnome baker as an example but it happens with all sudo commands):

rudolf@rudolf:~$ sudo gnomebaker
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
                  


Hope it makes sence to someone. Any ideas?


Thanks

Rudolf

---

### Post by petri on 2006-10-30
First thing first, when your launch a program with GUI from terminal do use **gksudo** in Ubuntu and **kdesu** in Kubuntu. Always. All Gui programs doesn't need that but as a rule it is easy to remember. You might get an error warning but it isn't "for real" More about it at [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) and in wiki. I don't know if that will solve your problem but it keeps you off the problem in the future. Hopefully :mrgreen: 

About ATI have you checked the guide at [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) ?

---

### Post by RudolfMDLT on 2006-10-30
Thanks Petri.

kdesu:


X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken


Thanks for the link, there are one or two things that I haven't tried yet. My ati card "works" but there is a GPU interface error with the new graphics engine(my terminology may be way off!) in Edgy with ati cards. So 3D works, just VERY slowly!

Thanks!

Rudolf

---

### Post by RudolfMDLT on 2006-10-31
Anybody else think they can have a go? :)

---

### Post by petri on 2006-10-31
Have you tried to install Gnomebaker again?

---

### Post by RudolfMDLT on 2006-10-31
Hi,

This is what I just typed:

"Thanks, but thats not the problem, this happens with any sudo command." 

Which was true... I just thought, that the heck, let me give you some examples of the error and like magic, it's not there anymore. There is no more error with sudo. I don't understand it, nut thanks anyway!

Cheers!

---

### Post by iamnafets on 2006-10-31
> **RudolfMDLT said:**
> Hi there,

Anyone know when there will be a fix for the Ati FGLRX driver for edgy? Jusst asking for interest sake, my slow fps is really annoying me.

Anyhow, After the upgrade to Edgy i get this error(I used Gnome baker as an example but it happens with all sudo commands):

rudolf@rudolf:~$ sudo gnomebaker
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
                  


Hope it makes sence to someone. Any ideas?


Thanks

Rudolf

Don't know how much help it is, but the first two inputdevice warnings (though not really important) can be fixed by editing /etc/X11/xorg.conf and commenting out the wacom tablet sections.  There is three of them I think, they should be fairly obvious, just put a # before them with something like:

sudo gedit /etc/X11/xorg.conf

The rest I can't help much with, I'm new too.  Good luck!

---

### Post by RudolfMDLT on 2006-11-01
Sweet! thanks!

---

