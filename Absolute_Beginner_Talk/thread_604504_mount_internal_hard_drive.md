---
title: "mount internal hard drive"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by davidexe on 2007-11-06
I have reviewed all the posts I can find and I can't find anything that applies directly to my situation. I installed Ubuntu Server on my computer, fresh, formatted drive (120gb) and installed. Got share working. Now I installed my new 500gb SATA drive on a PCI card controller. The drive shows up in the drives but with no partitions (not formatted yet). There is no option to add partitions, format, or anything.

I can find nothing about how to simply format the drive in Ubuntu for use as a data drive. I will be mounting a 2nd Sata drive in the future for a RAID 1 installation.

Thanks for any help.

---

### Post by kevinatkins on 2007-11-06
Hi,

Go to System -> Administration -> Partition Editor.

You can use that tool to format the drive to whatever file system you want... Make sure you select the correct drive! ;-)

---

### Post by davidexe on 2007-11-06
I went there and there is no "partition editor" there.

---

### Post by StooJ on 2007-11-06
> **davidexe said:**
> I went there and there is no "partition editor" there.

"GNOME partition editor"?

---

### Post by davidexe on 2007-11-06
I guess I don't understnad the post "gnome partition editor?"

---

### Post by StooJ on 2007-11-06
Sorry David.

I think the menu item is called "GNOME partition editor", not "partition editor".

So, try going to System -> Administration -> GNOME partition editor

Or, if you can't find it there, Hold down ALT & press F2 to get the Run Application window. In there, type ```
gksu gparted
```

That oughta run it.

---

### Post by njparton on 2007-11-06
Sometimes it's not installed by default:

```
sudo apt-get install gparted
```

---

### Post by davidexe on 2007-11-06
There is nothing in the system/administration that says anything about partition.  When I do the Alt / F2 it seems to do something, kicks off the windo and then does nothing.  B ack to desktop and terminal mode.

---

### Post by davidexe on 2007-11-06
It installed and it is formatting now.  THANKS a-bunch...

---

### Post by davidexe on 2007-11-06
well, back again.  I got the drive formatted and thought I mounted it properly to the folder I wanted. I named it "project".  Well, it mounted but with the name "lost+found". I understand that is the name when bad file structure or something is found.

Can I unmount, reformat?  or what?  Is there anyplace where there is comprehensive instructions that cover when it doesn't go the way the simple commands say it should. Or is there anyplace that gives the options on the "mount" command and what the various letters that are listed in the commands are for?

Thanks,

---

