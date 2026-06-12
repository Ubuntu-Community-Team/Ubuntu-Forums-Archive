---
title: "How to create shortcuts in Ubuntu?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by bombitmd on 2006-08-22
Another question :wink: 

Does dragging a folder to the desktop create a shortcut to that folder, or does it just copy it?  I dragged the My Documents folder from the FAT32 partition (which I use as the target for My Documents in XP) onto my Ubuntu desktop so I don't have to click and click just to reach my XP files.  It turns out, when I access a file from My Documents desktop folder, whatever changes I made are not carried over into XP, but remain in Linux.  It's like I just copied the entire folder.

Hmmm.  I just thought about something. I'm guessing it DID just copy it.  So, how do I create a shortcut to it?

---

### Post by sonny on 2006-08-22
It only copies your file to the location you specified... in order to make a shortcut you can bookmark it in nautilus, that way it will stay in the places menu and you won't have to click and click, it'll be accesible with one click.

---

### Post by bombitmd on 2006-08-22
Ok, thanks.  But, um ... I'm using Ubuntu 5.04, and have just absolutely begun trying it out (past 2 days).  Where can I find nautilus?  I don't remember seeing it on any of the drop down menus. :-(

---

### Post by sonny on 2006-08-22
> **bombitmd said:**
> Ok, thanks.  But, um ... I'm using Ubuntu 5.04, and have just absolutely begun trying it out (past 2 days).  Where can I find nautilus?  I don't remember seeing it on any of the drop down menus. :-(
Nautilus is your file browser, like windows explorer, anytime you browse your home folder (or any other folder) you are using nautilus. You can then go to the folder you want and then bookmark it.

---

### Post by bombitmd on 2006-08-22
Oops! ok.  Thanks!

---

### Post by bodhi.zazen on 2006-08-22
Linux uses Links for "shortcuts".

From a terminal:
```
ln -s /full/path/of/file /name/of/link
```

When making a link: 
1. I advise using the full path name for example:
/home/username/filename.

2. After the "-s" the first file is the full path to the file you want a short cut to.

3. The second file is the name of your shortcut.

4. Don't forget the ,space. between the two file name and shortcut name.

for example, to create a link (short cut) from your home folder to a USB drive (mounted at /media/usb):

```

cd ~
ln -s /media/usb /home/username/usb
```

```

cd
ln -s /media/usb usb
```
also works if you are lazy ("cd" without any location goes directly home).

You should now have a link (short cut) in your home folder to your usb device.

---

### Post by Delkster on 2006-08-22
> **bombitmd said:**
> I'm guessing it DID just copy it.
Yes, it probably did. The default action is to move the files or folders when the source and target folders are on the same filesystem (i.e. drive/partition) and to copy when they're on different ones (e.g. when dragging from a Windows partition to your Linux filesystem).

> So, how do I create a shortcut to it?
Drag and drop it with the middle mouse button instead of the primary one. When you drop the files this will give you a menu allowing you to choose whether you want to move, copy or link the files you dragged. Choose "Link here" in the menu.

Edit:
Check whether you have write permission to the files on the Windows drive, though. I'm not completely sure but I suppose mounted Windows partitions are only writable with administrator privileges by default, and if you link the files instead of copying them, any modifications you do via the link would actually be done to the files on the Windows drive (which is what you wanted in the first place), and that won't work if your Linux user account doesn't have the write permission to them.

If you don't have the write permission to the Windows drive, post the contents of your /etc/fstab file and someone can probably help you sort out your permissions to the Windows partition.

---

