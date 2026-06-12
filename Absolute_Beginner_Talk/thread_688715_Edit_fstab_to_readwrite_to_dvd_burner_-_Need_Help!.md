---
title: "Edit fstab to read/write to dvd burner - Need Help!"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by discmaster on 2008-02-05
I guess I need to change something here, but I am unsure of what; I need to be able to read/write to both DVD drives, but when trying to use K3b, I am getting the message - "access denied to /media/DVD_VIDEO_RECORDER".

Here is the fstab file;
> proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=07b7fcb6-280b-4ba7-963e-ae53b806b8b3 / ext2 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=f2884278-3e06-4fe8-af01-6efb38457b1b /media/sda1 ext3 defaults 0 2
# Entry for /dev/sda3 :
UUID=f5e28123-e525-4e5e-9fe8-6d79170790e2 /media/sda3 ext3 defaults 0 2
# Entry for /dev/sda6 :
UUID=2d1e5ae4-97f2-4287-8245-ba22402ccb89 /media/sda6 ext3 defaults 0 2
# Entry for /dev/sda5 :
UUID=e2202547-6119-4e52-9e0a-a0efa81cb195 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/hdb1 /media/HDSK\040 ntfs-3g defaults,locale=en_US.UTF-8 0 0

Where do I go from here? I am kinda confused, because there is no "ro" or "rw" entry for the cdrom/dvd burners...

:confused:

---

### Post by drs305 on 2008-02-05
deleted by poster

---

### Post by ayenack on 2008-02-05
I don't use k3d but I think this is correct.
If I remember correctly you have to set up user for k3b as root user. Might be worth starting it from terminal like this.

**sudo k3b**

And then adding yourself as a user also make sure you are added to the k3b users like this.

**System>Administration>Users_And_Groups**

Select **Manage Groups** and scroll down until you find k3d and add yourself to it.

As I said not sure about this but think it's correct.

EDIT: Think this is wrong. I was thinking about a different app.

---

### Post by discmaster on 2008-02-05
If I understand this situation correctly, doesn't the problem lie with the fstab, & the fact that I need to edit it to make the drives "rw"?
> proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=07b7fcb6-280b-4ba7-963e-ae53b806b8b3 / ext2 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=f2884278-3e06-4fe8-af01-6efb38457b1b /media/sda1 ext3 defaults 0 2
# Entry for /dev/sda3 :
UUID=f5e28123-e525-4e5e-9fe8-6d79170790e2 /media/sda3 ext3 defaults 0 2
# Entry for /dev/sda6 :
UUID=2d1e5ae4-97f2-4287-8245-ba22402ccb89 /media/sda6 ext3 defaults 0 2
# Entry for /dev/sda5 :
UUID=e2202547-6119-4e52-9e0a-a0efa81cb195 none swap sw 0 0
[B]/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto,exec 0 0[/B]
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/hdb1 /media/HDSK\040 ntfs-3g defaults,locale=en_US.UTF-8 0 0In the bold text, there is no "ro" or "rw", which I am thinking is supposed to be there, according to other reading I have been doing on the web. I am hesitant to just go ahead & add it in there, 'cause I don't really know what I am doing! :lolflag:

---

### Post by Bothered on 2008-02-05
Your fstab looks good (the cdrom entries are similar to mine). I'm not sure why k3b is trying to write to /media/DVD_VIDEO_RECORDER, as fstab is not configured to mount anything to there. This could be a problem with the k3b configuration (I don't know how to change that, as I don't use it), but could probably also be worked around by:

1. Changing the mount point of your DVD writer to /media/DVD_VIDEO_RECORDER. I'm not sure which of /media/hda and /media/hdb should be changed to this, as it's not clear which is your DVD writer.

or

2. Creating a symbolic link from /media/DVD_VIDEO_RECORDER to the DVD writer mount point, with:

```
sudo ln -s /media/hd[a or b, whichever is your DVD writer] /media/DVD_VIDEO_RECORDER
```

---

### Post by ayenack on 2008-02-06
There's also pysdm it's in the repo's to edit fstab if you're not to comfortable at the command line. It'll display as Storage Device Manager under System>Administration. Never used it but it's supposed to be very good indeed. To install you should be able to use Add/Remove or you can.

**sudo apt-get install pysdm**

In Terminal.

---

