---
title: "unexpected icons"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by e^(i*pi) on 2007-01-13
everything I've read about ubuntu mentions the nice clean desktop with no icons, but mine has two on it (hd1 and hd2). They have been there since I installed. Does anyone know what the deal with them is?

---

### Post by rai4shu2 on 2007-01-13
That's Nautilus. You can change that in gconf-editor at the following location:

/apps/nautilus/desktop/volumes_visible

---

### Post by seijuro on 2007-01-13
do you have any removable storage devices plugged into your system like for example usb jump drive, usb external hard drive, etc?

---

### Post by deadgobby on 2007-01-13
If you have a USB flash drive in the USB port. It will read it and put an icon on the desktop. 
Gobby

---

### Post by raul_ on 2007-01-13
I just wanted to say that you got a sick nick :lol:

sorry, couldn't hold myself

---

### Post by 3rdalbum on 2007-01-13
When you double-click on hd1 and hd2, what is displayed?

My feeling is that they are probably Windows partitions. Hd1 could be your actual Windows partition, and Hd2 could be a recovery partition that your computer vendor has placed there.

---

### Post by 2CV67 on 2007-01-13
My Edgy desktop has also always had 2 ikons: hda1 & hda4 which are my Windows partition & my shared FAT32 partition.

I would rather not have them there, but don't like to try to remove them as there don't seem to be any options about just removing ikons.
If I right-click on them the option is "unmount volume" which I certainly don't want, or "properties" which shows the properties of the partition & not the properties of an ikon...

I am also quite unable (by GUI means) to find anything about them or about desktop ikons or about Nautilus. There is nothing in Applications or Places or System, as far as I can see.

They don't appear in File Browser under Desktop.

Thanks for any (safe & GUI preferably!) advice.

---

### Post by dbott67 on 2007-01-13
> **2CV67 said:**
> My Edgy desktop has also always had 2 ikons: hda1 & hda4 which are my Windows partition & my shared FAT32 partition.

I would rather not have them there, but don't like to try to remove them as there don't seem to be any options about just removing ikons.
If I right-click on them the option is "unmount volume" which I certainly don't want, or "properties" which shows the properties of the partition & not the properties of an ikon...

I am also quite unable (by GUI means) to find anything about them or about desktop ikons or about Nautilus. There is nothing in Applications or Places or System, as far as I can see.

They don't appear in File Browser under Desktop.

Thanks for any (safe & GUI preferably!) advice.

A nice solution right here (pretty much just what **rai4shu2** said):

[http://www.ubuntuforums.org/showpost.php?p=1852633&postcount=10](http://www.ubuntuforums.org/showpost.php?p=1852633&postcount=10)

-Dave

---

### Post by 2CV67 on 2007-01-13
Well - that got rid of my ikons OK, without wiping out the actual partitions!  -  Thanks!

In trying to find how I could have got there by GUI methods (this is too long a story for here but, believe me, is VERY important for me) I found Configuration Editor Help which says, quote:
"You can start Configuration Editor in the following ways: 
Applications menu > Choose System Tools &#8594; Configuration Editor."

But I don't have "System Tools" in my Applications Menu or anywhere else I can see...
So next question is, how do I get System Tools available?

Hope I have not hijacked this thread.

---

### Post by Buck2348 on 2007-01-13
System --> Preferences --> Menu Layout.  In the left pane select "Applications" if it's not selected by default.  In the right pane tick (enable) "System Tools."  Now click on "System Tools" in the left pane and in the right pane make sure that all the items you want are selected (ticked).  I have all but "Floppy Formatter" selected.

Buck

---

### Post by 2CV67 on 2007-01-13
Thanks!

That worked exactly as you said.

I would never have found it by myself though.
Even now, I might expect to find "System Tools" under System > Administration somewhere.
Oh well...

Thanks again!

---

### Post by e^(i*pi) on 2007-01-13
That answers all of my questions as well, icons are now gone and everything is working fine.  Thanks everyone.

---

