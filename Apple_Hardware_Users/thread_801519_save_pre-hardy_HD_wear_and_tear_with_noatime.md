---
title: "save pre-hardy HD wear and tear with noatime"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by stream303 on 2008-05-20
Now that Hardy has included the *relatime* parameter to fstab, I thought I'd point out a reminder to those running pre-Hardy installs that you can obtain the same benefit by manually modifying your /etc/fstab with **noatime**

The only difference is that Hardy's relatime parameter will perform this function on a weekly basis, whereas with noatime it won't perform it at all.  However, I think it is better than having your drive constantly writing to disk on read-only files, perhaps slowing the system somewhat and increasing wear and tear, especially on very old oem Apple hard drives.

Here is the original forum thread:
[http://ubuntuforums.org/showthread.php?p=4301096](http://ubuntuforums.org/showthread.php?p=4301096)

---

### Post by BladeMelbourne on 2008-05-20
I have been running for a few months with noatime on my root and home partitions. The performance increase is noticeable (especially with the notebook drive inside my Mac Mini). I haven't tried relatime yet.

```
# Entry for /dev/hda4 :
UUID=f2cf1df1-81ef-41b0-913b-851cea8ee4bf / ext3 defaults,noatime,errors=remount-ro 0 1
# Entry for /dev/hda2 :
UUID=ffe4e180-2b54-49b7-987e-b81a9e01f76b /home ext3 defaults,noatime 0 2
# Entry for /dev/hda5 :
UUID=5aada659-baf1-4171-8bd2-614e2c772a35 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

Disabling the last access date also improves performance on Windows - it can be done by editing the registry. Google for it if you're interested.

---

### Post by stream303 on 2008-05-20
I think the relatime parameter is new to Hardy, having come from Fedora(?).  Not sure if it is available to pre-hardy users, but noatime works.

Windows?  I'll have to check that out, although most old machines I run across with windows get reformatted with Linux. :)

---

### Post by Scientia on 2008-05-27
How exactly do you change the system to use noatime?
Sorry, but i'm floundering around in the Linux envuronment.

---

### Post by stream303 on 2008-05-27
You edit the /etc/fstab file.  Just be very careful with editing!  In fact, I'd back it up first:

```
sudo cp /etc/fstab  /etc/fstab.bak
```

You add the noatime parameter similar to what is shown in the examples.  In a simple case of partitioning, find the EXT3 partition line.  Add the noatime parameter with the comma if needed. You can edit it via a text-based editor or gui:

Text based:
```
sudo nano -w /etc/fstab
```
(make your edits, ctrl-o to write it out, ctrl-x to quit nano)

Gui based:
```
gksudo gedit /etc/fstab
```

As with all system files, just take it easy and study the ext3 line above.  Your line will look different, you just want to add only the noatime parameter and the comma if needed.  This is a really important file, and you don't want to blow it. :)

---

### Post by stream303 on 2008-05-27
> **Scientia said:**
> Sorry, but i'm floundering around in the Linux envuronment.

btw, don't be sorry. :)  I think we all floundered at some point.  It comes to you if you take it easy and not get frustrated, and most importantly, don't bite off more than you can chew. :)  Small steps.

I remember back when I started with Yggdrasil Linux in '95 and was so frustrated that the only thing I had was the $ shell prompt - it looked nothing like what was on the box with all those x-window gui programs running.

My frustration led me to believe that merely installing a commercial version would be better.  500 dollars later with only a two-seat license, no networking, no compilers, practically nothing led me right back to the $ shell prompt.  And it wasn't even in color. :)

Hard lesson.  Back to Slackware and small steps.  Keep it fun.

sorry about the rambling...

---

