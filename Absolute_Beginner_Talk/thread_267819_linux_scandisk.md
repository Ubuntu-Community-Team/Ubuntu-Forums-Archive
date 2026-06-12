---
title: "linux scandisk?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-09-29
Hi,

I have a removeable harddrive that seems to be struggle to transfer files. this happened since i convert the partitioning to FAT32 so i can read write on my windows and ubuntu machines. I think there may be some bad sectors on the disk but windows says there is nothing wrong. Are there any linux tools on the repositories that can check hard disk integrety etc?

cheers
niteblind

---

### Post by gn2 on 2006-09-29
Have you tried de-fragmenting it with Windows?

---

### Post by bigken on 2006-09-29
go to makers web site see if there any tools to check the drive ;)

---

### Post by niteblind on 2006-09-29
so there are no linux own tools? this is not  defrag issue for two reasons.

it has just been formatted there has not been any chance for fragmentation to happen.
the drive is stopping to spin and then starting again which would not be caused by a fragmentation issue.

cheers
niteblind

---

### Post by gn2 on 2006-09-29
I have had similar problems, and it was related to the amount of electrical power available on the USB port.

Using my 2.5" enclosure on my wife's old laptop I need to plug the two USB plugs in, one via a USB/ps2 adapter. 
(The supplied lead has two USB plugs to accomodate this)

Or I could use a powered hub.

Same device only needs one plug on desktop PC with USB2 sockets.

---

### Post by bigken on 2006-09-29
> **gn2 said:**
> I have had similar problems, and it was related to the amount of electrical power available on the USB port.

Using my 2.5" enclosure on my wife's old laptop I need to plug the two USB plugs in, one via a USB/ps2 adapter. 
(The supplied lead has two USB plugs to accomodate this)

Or I could use a powered hub.

Same device only needs one plug on desktop PC with USB2 sockets.

I have had this using usb modems power consumption I got round this by using a usb hub ;)

---

### Post by snakyjake on 2006-09-29
> **niteblind said:**
> Are there any linux tools on the repositories that can check hard disk integrety etc?

Here's the Linux tool to check disk integrity: [fsck]("http://man.he.net/?topic=fsck&section=all")

---

### Post by Albi on 2006-09-29
**Don't Run That While The Drive Is Mounted!**

---

### Post by snakyjake on 2006-09-30
> **Albi said:**
> **Don't Run That While The Drive Is Mounted!**

How come?  What if you need to check the same disk you're using (i.e. hda1)?  Is there a better alternative?

---

