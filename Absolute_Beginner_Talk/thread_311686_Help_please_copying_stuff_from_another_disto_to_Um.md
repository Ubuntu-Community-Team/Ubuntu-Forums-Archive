---
title: "Help please copying stuff from another disto to Umbuntu - more hotplug woes"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by cogvos on 2006-12-03
Dear all,
:confused: Oh why doesn't technology just *work!*

Having installed Umbuntu on an internal sata hard drive I now want to copy data from an external usb drive that has suse installed.

Having found out that there is a glitch in edgy's hotplug system (where it does not recognise usb drives if they are already plugged in on boot, only if they are plugged in after boot... grrrr) - anyone know why?; I started 6.10 and plugged in the external usb drive.

Result? Zilch.

The drive in question is an ide in an external usb casing; so it talks via usb and should (?) be picked up by the hotplug system. It ain't

dmesg|tail shows the drive being detected as sdf: sdf1 sdf2 sdf3 <sdf5 sdf6> but (like the pen drives I've been struggling with) nothing appears on the desk top. I expected to get an icon per drive (minus I guess suse's swap partition)

So I created a new directory in media called linux2 and tried to mount the *@"£! thing.

mount /dev/sdf1 -t ext3 /media/linux2

I type confidently

Device sdf1 does not exist

Comes the reply. ](*,) 
So how do I mount this thing so that it appears on the desktop (or somewhere!) so that I can use the gui and not spend ages typing cp bla/bla/* -r

Any ideas?
John.

---

### Post by cogvos on 2006-12-03
Right, I've narrowed this a bit, thought still have no idea what's not working.

If there are no usb items, thats pen drives, mice, printers etc, connected at startup and you connect a usb drive after you log in hotplug picks it up, displays the partitions and all is right with the world.

If *any *usb devices are present at startup, such as a printer,then it sulks and refuses to do anything.

This must be something to do with a timing issue (?) or somthing else, aliens perhaps, I'm stumped. I can't test since the way to stop the hotplug /etc/init.d/hotplug stop does not work 'cos hotplug ain't in /etc/init.d!

Anyone any idea how you stop and start hotplugging in edgy?
J.

---

