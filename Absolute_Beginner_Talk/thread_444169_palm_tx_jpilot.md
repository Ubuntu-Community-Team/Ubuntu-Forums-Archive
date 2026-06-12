---
title: "palm tx jpilot"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by kman14 on 2007-05-15
hello there

i know there are a lot of posts on this but i can't find one that completely helps me.

i have a palm tx and am trying to sync it with jpilot.
when i hit the hot sync button i get this:

[B]Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished[/B]

any help with this would be great.
or link to a "how to" etc.

thanks

---

### Post by Kobalt on 2007-05-15
You need to follown these instructions in order to make /dev/pilot an existing device : [https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

---

### Post by kman14 on 2007-05-15
kobalt 
thanks for the reply.

the last part of the "how to" says:

 
[B]
      For Ubuntu 7.04 (Feisty Fawn) when still not working add the visor module to etc/modules. Then load the module by issueing

sudo modprobe visor[/B]


how do i add the visor module to etc/modules?

thanks.

---

### Post by lazyart on 2007-05-15
I have a palm T|X syncing with Feisty.  Just set the port to "usb:" (Go to File>Preferences>Settings to find it).
From there, hit Hotsync on jpilot, then hit Hotsync on the unit/cable and you're golden.

Compared to Edgy when I had to sync via wifi, this is simple.

---

### Post by Kobalt on 2007-05-15
To add visor to /etc/modules you must open it with root priviledges : ```
gksu gedit /etc/modules
```and simply add *visor* to the modules list, save and exit.

---

### Post by kman14 on 2007-05-15
guys, thanks for the help.
it seems to be working well now.

i have to say that the best thing about ubuntu is this forum.....and i _really_ like ubuntu.

thanks again.

---

### Post by marsopia on 2007-05-23
Thanks guys! 
I can now sync my tx with Fiesty, but it syncs with evolution, how can I sync it w/ jpilot please?

thanks in advance!

Mariano

---

### Post by lazyart on 2007-05-23
Go to jpilot's preferences and set the serial port to whatever you used to sync it with Evo.  In my case it is usb: but yours might be different.  Hit the hotsync button on jpilot, then hit hotsync from the palm.

---

### Post by stoian on 2007-12-31
i have a Palm TX and recently I had to switch back from Feisty to Dapper. In Feisty I could sync painlessly with J-Pilot (jpilot)... but in Dapper, even if I follow all the instructions, still not possible.

I wonder if anybody had any success to syncing PALM TX with J-Pilot in Dapper.
Thanks.

---

### Post by stoian on 2007-12-31
Actually only this page holds the truth:
[http://www.computechgroup.com/?p=274](http://www.computechgroup.com/?p=274)


The difference relies in what is the contents of the "rules" file:

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB[13579]", SYMLINK="pilot"

Now, to recap all the steps - for Ubuntu Dapper 6.06 - only, here they are:

sudo gedit /etc/udev/rules.d/10-custom.rules

type or copy the correct line (this is one single line):
BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB[13579]", SYMLINK="pilot"

sudo gedit /etc/modules
add "visor" word at the end of the file

sudo modprobe visor

Make sure in jpilot program, under File > Preferences > Settings
under Serial port: /dev/ttyUSB1

I think now you should restart the computer, and then try to sync. First press the sync button on the palm, then in jpilot.

In Feisty this works even the other way around (first press sync button in jpilot and then on the palm)...

whew!...

---

