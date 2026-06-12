---
title: "How do I get my Secondary drives to show in Gnome?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-12
I know how to mount and format with cmd line, but how I do I get my 2nd and 3rd HDDs to show in Places -->Computer?  The last machine I installed Ubuntu on, they just showed there automatically...but on this new one they arne't showing.  How would I put these into this view?

---

### Post by FuriousLettuce on 2007-04-12
Are you mounting them using fstab (are there entries for them if you do 'cat /etc/fstab'? If so, they ought to be there automatically, and this seems like a wierd problem. If not, you want to add the entries to /etc/fstab - there are a large number of tutorials around on how to do this (just search fstab)

---

### Post by kc5hwb on 2007-04-12
No...I have not put them into the FSTAB yet.  I know how to do that from reading around, but I haven't done it yet.  (I think that I can do it with Webmin also)

But on my last Ubuntu setup with 6.04, I never edited the FSTAB and the 2nd drive in that box showed up fine.

---

### Post by kc5hwb on 2007-04-12
Anyone else?

---

### Post by rsambuca on 2007-04-12
Any drive mounted in /media/ should show up.  Did you mount them in /media during installation this time?

---

### Post by kc5hwb on 2007-04-12
No, they are mounted in /mnt   So for them to show up in the GUI, they have to be in media?  I can remount them....

---

### Post by rsambuca on 2007-04-12
I could be wrong, but I believe that is what happens (just going by personal experience on this one).  The last time I installed, I mounted some in /media, and some in /partitions, and only the ones in /media show up.

---

### Post by kc5hwb on 2007-04-12
No, that didn't work... :(  I have 3 extra drives in this box, 2 of them are mounted in /mnt and I just tried to mount the 3rd one in /media and it still isn't showing in the Places-> Computer view.

This drive is partitioned and formatted as NTFS because it was in an XP box.  I want to reformat it to EXT3, but I'd like to do it with the GUI.  Any ideas on how to do that?

---

### Post by kc5hwb on 2007-04-14
Anyone else have an idea for this?

---

### Post by rsambuca on 2007-04-14
Have a look in the gconf-editor.  Try apps -> nautilus.  Perhaps there is a toggle in there somewhere.

---

### Post by kc5hwb on 2007-04-14
I don't have an Apps->Nautilus.

I found this...
```

jason@SAMSON:~$ whereis gconf
gconf: /etc/gconf /usr/shar
```e/gconf

---

### Post by rsambuca on 2007-04-14
```
gconf-editor
```

---

### Post by kc5hwb on 2007-04-14
That's a neat little tool that I will use again for some other things, but no...there is no toggle for Secondary Drive view in COMPUTER that I can find..

---

### Post by rsambuca on 2007-04-14
Sorry, out of ideas here.  I still think it has something to do with the /media folder somehow, though.

---

### Post by kc5hwb on 2007-04-14
> **rsambuca said:**
> Sorry, out of ideas here.  I still think it has something to do with the /media folder somehow, though.

I mounted it in the /media folder and that didn't seem to help.  I'll try it again though.  Thanks for your help.

---

### Post by devnulljp on 2007-04-14
> **kc5hwb said:**
> This drive is partitioned and formatted as NTFS because it was in an XP box.  I want to reformat it to EXT3, but I'd like to do it with the GUI.  Any ideas on how to do that?

best method is fdisk & mkfs
But you want a gui? Try parted -- I think the guis are qtparted on kde and gparted on gtk.

You don't need to mount to format anyway.

sudo fdisk 
d for delete partitions <---------delete all
c for create partitions
w to write the table to disk

sudo mkfs -t ext3 /dev/<devicename>

Should do it for you.

Then you can mount as usual:
mount -t ext3 /dev/<devicename> /media/some/mount/point

---

### Post by kc5hwb on 2007-04-14
Gparted....that is what I used before.  Thanks, I couldn't remember that name for the life of me.

---

