---
title: "Moving folders from OS X (hfs) partition to /home partition"
date: 2009-03-11
forum: Apple Hardware Users
---

### Post by wersdaluv on 2009-03-11
I want to move my "Users" and "Applications" folder to my Ubuntu /home partition. Is it possible? I tried moving them to my /home partition then created symlinks for OS X to be directed to my /home partition but it did not read the symlinks properly.

Also, I can't write on my hfs partition now while on Ubuntu. I don't know what happened. I can still read it and my UID on Ubuntu is the same as my UID on OS X (501). How do I fix this?

Thanks in advance. :)

---

### Post by cyberdork33 on 2009-03-11
do you still have journalling disabled?

---

### Post by wersdaluv on 2009-03-11
> **cyberdork33 said:**
> do you still have journalling disabled?
I suppose. I don't remember changing it.

By the way, when I tried booting OS X a while ago, I never got to boot. After the splash screen, my computer just restarted. Oh well. It's a new issue. If I don't get this to work, I'll just reformat.

After reformatting, I hope, I can find a way to move my folders and make symlinks because OS X doesn't allow moving such folders.

---

### Post by damis648 on 2009-03-11
Well, Mac OS X can't read Ext3. Do you have a driver for Ext3?

Also, to get write access, make sure you
```
sudo diskutil disablejoural /dev/rdisk0
```
in Terminal.app.

---

### Post by wersdaluv on 2009-03-11
> **damis648 said:**
> Well, Mac OS X can't read Ext3. Do you have a driver for Ext3?

Also, to get write access, make sure you
```
sudo diskutil disablejoural /dev/rdisk0
```
in Terminal.app.
I have a driver for Ext3. I was able to access my /home.

I'll recheck if journal is enabled again but I don't remembering enabling it.

Thanks :)

Btw, are Linux symlinks supposed to work on OS X?

---

### Post by wersdaluv on 2009-03-11
> **damis648 said:**
> Well, Mac OS X can't read Ext3. Do you have a driver for Ext3?

Also, to get write access, make sure you
```
sudo diskutil disablejoural /dev/rdisk0
```
in Terminal.app.
I have a driver for Ext3. I was able to access my /home.

I'll recheck if journal is enabled again but I don't remembering enabling it.

Thanks :)

Btw, are Linux symlinks supposed to work on OS X?

---

### Post by damis648 on 2009-03-12
> Btw, are Linux symlinks supposed to work on OS X?

As far as I know... but there my just be a confliction in the fact that the symlinks are between different filesystems. Also, what driver are you using? I have tried to find one (recent one) that works, but I have not found one.

---

### Post by wersdaluv on 2009-03-12
> **damis648 said:**
> As far as I know... but there my just be a confliction in the fact that the symlinks are between different filesystems. Also, what driver are you using? I have tried to find one (recent one) that works, but I have not found one.
I'm using ExtFSManager. 

I'm on my fresh OS X install now. i can read my /home partition but I can't write on it...

Any idea how to fix this?

---

### Post by phatqao on 2011-01-10
> **damis648 said:**
> Well, Mac OS X can't read Ext3. Do you have a driver for Ext3?

Also, to get write access, make sure you
```
sudo diskutil disablejoural /dev/rdisk0
```
in Terminal.app.

Thanks for the tip. The identifier of the boot disk may differ (it did for me), in which case you can use ```
diskutil list
``` to find it. then instead of 'rdisk0' in your command, it's the ID you found for the OS X partition.

I used this info to make a symlink between my os x music folder and my ubuntu rhythmbox directory - thank you very much!

---

