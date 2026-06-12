---
title: "System hangs when dragging folder"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by uways on 2006-02-23
uh.. hello. i'm very new to linux. been using windows n mac os9/x most of my life. i decided to give linux a try. first i tried to network install debian but i never got past that. somehow the installation wouldn't let me configure my network settings manually. anyone have any ideas?

anyway, that's besides the point. this is an ubuntu forum. i just installed ubuntu 5.10  (installation was a breeze) and now familiarizing myself with the whole linux experience. i must say that i still depend mostly on the gui to go about doing things. 
i tried dragging files around the desktop, from the desktop to a folder, folder to desktop and there was nothing wrong. however, when i attempted to drag a folder containing some pictures the whole system just froze, forcing me to reboot the computer. i've tried again with a lot of other folders and the same thing happens. what's wrong? if i'm not supposed to drag folders, why does ubuntu allow me to drag them? do i have to reinstall ubuntu altogether?

---

### Post by knalle on 2006-02-23
hm sounds like you got a problem with the filemanager/x11 you are using, are you using ubuntu fresh as it was from the install or have you added packages?

---

### Post by uways on 2006-02-23
I downloaded the ISO image and installed using that. i don't think I've done anything else to it so far besides using GIMP and firefox. as far as packages go, to be honest with you i have no idea. I'm completely clueless! if you are asking whether i downloaded any packages myself then the answer is no. i don't even know how to do that yet. in unfamiliar territory here... kinda lost

---

### Post by knalle on 2006-02-23
hm, no goto a **terminal** and write;

**tail /var/log/syslog**

and post the output

---

### Post by uways on 2006-02-23
Feb 23 21:23:11 localhost kernel: [4305409.562000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Feb 23 21:23:11 localhost kernel: [4305409.562000] atkbd.c: Use 'setkeycodes e02 a <keycode>' to make it known.
Feb 23 21:23:11 localhost kernel: [4305409.643000] atkbd.c: Unknown key released  (translated set 2, code 0xaa on isa0060/serio0).
Feb 23 21:23:11 localhost kernel: [4305409.643000] atkbd.c: Use 'setkeycodes e02 a <keycode>' to make it known.
Feb 23 21:23:11 localhost kernel: [4305409.709000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Feb 23 21:23:11 localhost kernel: [4305409.709000] atkbd.c: Use 'setkeycodes e02 a <keycode>' to make it known.
Feb 23 21:23:11 localhost kernel: [4305409.990000] atkbd.c: Unknown key released  (translated set 2, code 0xaa on isa0060/serio0).
Feb 23 21:23:11 localhost kernel: [4305409.990000] atkbd.c: Use 'setkeycodes e02 a <keycode>' to make it known.
Feb 23 21:24:22 localhost ypbind[9387]: broadcast: RPC: Timed out.
Feb 23 21:25:36 localhost ypbind[9387]: broadcast: RPC: Timed out.

---

### Post by knalle on 2006-02-23
mmh, doesn't help much because i guess the erros scrolled up when you rebooted...

try **less /var/log/syslog** and look for errors that are related to the words "X11", "Xorg" or "kernel" and post them

---

### Post by uways on 2006-02-23
Feb 23 22:47:09 localhost syslogd 1.4.1#17ubuntu3: restart.
Feb 23 22:47:09 localhost anacron[17321]: Job `cron.daily' terminated (mailing output)
Feb 23 22:47:09 localhost anacron[17321]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Feb 23 22:48:08 localhost kernel: [4295353.037000] ppdev: user-space parallel port driver
Feb 23 22:48:08 localhost kernel: [4295353.039000] ppdev0: registered pardevice
Feb 23 22:48:08 localhost hpiod: ParDevice::nibble_read failed: Input/output error
Feb 23 22:48:08 localhost kernel: [4295353.080000] ppdev0: unregistered pardevice
Feb 23 22:48:08 localhost kernel: [4295353.080000] ppdev1: claim the port first
Feb 23 22:48:08 localhost kernel: [4295353.080000] ppdev2: claim the port first
Feb 23 22:48:08 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport3: No such file or directory: io/hpiod/ppdevice.cpp 827
Feb 23 22:49:18 localhost gconfd (root-26163): starting (version 2.12.0), pid 26163 user 'root'
Feb 23 22:49:18 localhost gconfd (root-26163): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only
configuration source at position 0
Feb 23 22:49:18 localhost gconfd (root-26163): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Feb 23 22:49:18 localhost gconfd (root-26163): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Feb 23 22:49:18 localhost gconfd (root-26163): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Feb 23 22:49:18 localhost gconfd (root-26163): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Feb 23 22:49:18 localhost gconfd (root-26163): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Feb 23 22:49:18 localhost gconfd (root-26163): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Feb 23 22:49:18 localhost gconfd (root-26163): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Feb 23 22:49:48 localhost gconfd (root-26163): GConf server is not in use, shutting down.
Feb 23 22:49:49 localhost gconfd (root-26163): Exiting
Feb 23 22:50:18 localhost kernel: [4295483.673000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Feb 23 22:50:18 localhost kernel: [4295483.673000] apm: disabled on user request.
Feb 23 22:50:18 localhost modprobe: FATAL: Error inserting apm (/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/apm.ko): No such device
Feb 23 22:50:19 localhost init: Re-reading inittab
Feb 23 22:50:30 localhost gconfd (uways-28265): starting (version 2.12.0), pid 28265 user 'uways'
Feb 23 22:50:30 localhost gconfd (uways-28265): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0

---

### Post by uways on 2006-02-23
the syslog is too long to post (reading the whole thing itself took a while) and i can't seem to find any "ERROR" or anything like that. i tried reinstalling but still have the same problem. if i drag a folder from one place to another very quickly it's fine. but when i drag a folder around in the same place, say the desktop, system immediately hangs. wish i knew what to look for.

---

### Post by Brunellus on 2006-02-23
do this:

cat /var/log/syslog | grep error > pasteme.txt

That should create a textfile with all instances of "error" in the syslog.  paste that.

---

