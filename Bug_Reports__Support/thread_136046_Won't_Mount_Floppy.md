---
title: "Won't Mount Floppy"
date: 2006-02-25
forum: Bug Reports / Support
---

### Post by Silmaril on 2006-02-25
I've just installed Ubuntu and it won't mount floppys.

I've also requested help on launchpad: [this is what I've got so far]("https://launchpad.net/distros/ubuntu/+ticket/404")

As I'm about to ask them: how do I uncomment something? I've worked out how to edit source.list, but I simply don't know what to type/delete in order to uncomment. 
In addition, does anyone have any other suggestions for what might be causing the problem-I have successfully downloaded the update that was meant to fix th bug, and it hasn't.

Thanks for any help!

---

### Post by ajgreeny on 2006-02-25
Is your floppy drive listed in /media?  If not you will need to add it as a folder named floppy0.  You will also need to add the following line to /etc/fstab

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

If you've got none of those give it a try and see what happens.

To uncomment a line in sources.list you need to remove the # sign in front of the text.

---

### Post by Silmaril on 2006-02-25
Thanks!

Unfortunately it still won't mount.

---

### Post by hav0x on 2006-02-25
you need to update pmount or something like that.
search these forums for that problem, iirc the thread will point you to a dapper package, just install that and the problem will go away

---

### Post by wylfing on 2006-02-25
Yes, the package you need is pmount from breezy-backports. In other words, the next version of Ubuntu will have this fixed, but if you want to apply the fix now, you can.

The instructions are here:
[http://www.ubuntuforums.org/showpost.php?p=577799&postcount=1](http://www.ubuntuforums.org/showpost.php?p=577799&postcount=1)

---

### Post by Silmaril on 2006-02-25
I reinstalled ubuntu (as I haven't been working with it long it seemed the easiest way of sorting things)

Then I followed the link and did as it said.

Still won't mount, still getting the same error message.](*,)

---

### Post by wylfing on 2006-02-25
The common workaround for non-mounting floppies is to do it manually from the command line. Insert the floppy and type this in a terminal:
```
mount /media/floppy0
```

This should mount it and put a floppy icon on the desktop. BEFORE you eject the floppy disk be sure to unmount it by right-clicking the icon and choosing Unmount Volume.

That should hold you until Dapper is finished.

---

### Post by schmidty on 2006-02-26
Try this command;

sudo mount -t auto /dev/fd0 /media/floppy

If that doesn't work try replacing *auto* with **msdos** or with **ntfs**.
This will also work with zip drives. I had to do this on my laptop to get it to mount a swapping floppy/CDROM/zip port.

Hope this might help!

Schmidty

---

### Post by Silmaril on 2006-02-27
I'm not having luck with either of those, but I need to play around with them a bit- will report back again once I've done that.

Any idea when the next version is out???

---

### Post by beast2k on 2006-03-09
Did this pmount/floppy/zip/usb problem get solved? I had it resolved but here I am a month later and the problem is back this time it's iomega zip100 drive as well as floppy, strange stuff. This time my pmount is already updated from the last time I fixed it so now I am stumped, I have tried everything from every thread on this and other forums. Does anyone have any new ideas about how to fix this ? No idea is to far out so don't be shy. I guess I'll just use the cd & dvd untill the next version is out. What a p.i.t.a

---

