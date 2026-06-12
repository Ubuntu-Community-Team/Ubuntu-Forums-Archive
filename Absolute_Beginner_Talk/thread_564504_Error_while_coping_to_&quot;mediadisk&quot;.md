---
title: "Error while coping to &quot;/media/disk&quot;"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Rex72 on 2007-10-01
Sure am glad there are these "beginner threads" to ask these silly questions:)

Im running Edubuntu on a hard drive shared with WinXP and Edubuntu.  

I plugged in an external USB 100Gig hard drive formated with WinXP.  Im trying to copy material to this drive when using Edubuntu but get the following error.

Error while coping to "/media/disk".
You do not have permission to write to this folder.

When installing Edubuntu I created only 1 user.  I thought this user had full unrestriced write/read to these kinds of things.

So basically Im stuck and looking for some simple advice.  

Thank you

---

### Post by philinux on 2007-10-01
sudo chown username  /media/disk

Is what you need I think. Before doing that if you right click on disk and click properties then permissions can you post a screenshot of the output.

---

### Post by Rex72 on 2007-10-01
After typing "sudo chown user /media/disk" I get the following back.

chown: changing ownership of `/media/disk': Read-only file system

I'll try and describe my properties then permissions options as you requested.

Owner and Group say ROOT and everything else is grayed out.  Nothing can be click on and changed.

Hope this was clear and thanks for responding.  Hope I can get this figured out with everyones help.

---

### Post by philinux on 2007-10-01
Is it formatted as ntfs?

If so read this [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

[edit] sorry this is for internal drive partitions

---

### Post by justleen on 2007-10-01
if its an NTFS drive, install ntfs-3g (its avaible through apt/synapctic)

---

### Post by philinux on 2007-10-01
They've even got a home page [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)
good luck

---

### Post by Rex72 on 2007-10-01
Thanks for the help.

It did the trick!!

---

