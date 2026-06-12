---
title: "Hiding the sda1 icon on desktop?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Mikestarko on 2007-04-21
I just installed Feisty Fawn today, but there is an icon named "sda1" that leads to my windows folder.  Is there a way to hide this?

Thanks.

---

### Post by Famicommie on 2007-04-21
Press alt+F2 to bring up the run dialogue and enter ```
gconf-editor
```
Choose	apps &#8594; nautilus &#8594; desktop.
Uncheck the "volumes_visible" checkbox

---

### Post by kyphi on 2007-04-21
Yes, that works.  But ...

It will also hide the icon if you want to use your USB stick or the icon if you put a CDROM in the CD player.

There must be another way.

---

### Post by Famicommie on 2007-04-22
While it certainly will prevent removable media from showing an icon on your Desktop, said removable media should still be accessible from the Places menu.

---

### Post by kyphi on 2007-04-22
Indeed any mounted media are accessible via Places.

However, if you mount a CD or access a USB drive how do you eject (unmount) it.  Does just pulling the device out of the USB socket unmount it automatically?

---

### Post by mcduck on 2007-04-22
> **kyphi said:**
> Yes, that works.  But ...

It will also hide the icon if you want to use your USB stick or the icon if you put a CDROM in the CD player.

There must be another way.

The other way is to edit /etc/fstab to mount that partition to any other directory than /media. (you'll have to create the directory first) Or if you don't need it to be mounted all the time you could alternatively add 'noauto' to it's options in fstab. Then it would only mount when you access it through Computer or Places menu, and would not show on your desktop when not mounted.

For example I use the 'noauto' for my windows partition as I rarely need to access it anyway, and mount my storage partition (which I need all the time) into /mnt/storage.

---

### Post by kyphi on 2007-04-22
Thank you, mcduck.  I will put that into effect.

---

### Post by JebusWankel on 2007-04-22
A simpler way, if you want to mess around with it, is to increase the screen resolution and move the icon to a corner, probably the bottom right, and then decrease the resolution and I believe that will hide it. Plus it will still be accessible through the /home/user_name/Desktop.

---

### Post by kyphi on 2007-04-22
Adding "noauto" in the fstab file hides the desktop icon but creates permission problems when trying to access sda1 via the places menu.

Jebus, your suggestion to change the screen resolution to sweep the offending icon under the carpet made me chuckle.  A fine example of lateral thinking that works (sort of).

Will try mounting sda1 into another folder.

Hang in there, Mike, this will be solved yet.

---

### Post by chakkaradeep on 2007-04-22
> **Mikestarko said:**
> I just installed Feisty Fawn today, but there is an icon named "sda1" that leads to my windows folder.  Is there a way to hide this?

Thanks.

Any idea also how to change the name "sda1" ? I know this is the label if am not wrong, so, how do we go about  changing the label :)

---

### Post by kyphi on 2007-04-22
Here is one answer to the question of hiding the sda1 icon;

"noauto" was not effective.  A separate directory created access problems.  Sweeping it under the carpet by changing screen resolutions is problematic (see how many requests there are on how to change resolution).

BUT - sweeping it under the carpet using the following method is very easy and also easily undone:

Just drag the icon to the bottom (or top) panel so that the panel hides it.  If you need it back, right click on the panel, go to Preferences and activate the "Show Hide Buttons" box.  Roll back the panel and retrieve your hidden icon.  You can still access sda1 via your Places menu.

As to the question on how to change the name of sda1, you can to change that in the fstab file.

---

### Post by Famicommie on 2007-04-25
Can you post your fstab?

---

### Post by Nythain on 2007-04-25
the surest way to do it is edit the fstab to mount it in /mnt instead of /media... but then im not sure if it will still be available the Places menu...

---

