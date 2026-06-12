---
title: "Fstab and Permissions/Newbie Troubles"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by cerverx27 on 2006-09-25
Yes, I'm aware this has probably been posted numerous times but searching for the answer I'm looking for has been somewhat difficult.

I've made the transition to Ubuntu from Windows.  Great, right?

Well, I've got some problems due to my inexperience with linux:

After my installation of Ubuntu (on a 15gig partiton) and swap file (5gig) I had some unallocated free space that I wanted to use to save most of my downloads, and other media.

I created two ext3 partitions, both logical and mounted them as follows:

[B]mount /dev/hda5 /home/mef/mefdrive1
mount /dev/hdb5 /home/mef/mefdrive2[/B]

The drives do show up in my home directory under /mef but they are completely inaccessible in that I can't write, they just read.  On top of this, under the "Computer" tab in Nautilus they show them mounted in **/media/idedisk** and **/media/idedisk-1**.  Those as well are readable but not writeable due to permissions (I'm assuming.)

Also when fiddling around with **Fstab**, I tried adding the drives to that but nothing really changed.  This is somewhat frustrating and if anyone has any input on this matter it would be greatly appreciated.

If any more information is needed please let me know.


Sincerely,


MEF!

---

### Post by aysiu on 2006-09-25
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) might help.

---

### Post by cerverx27 on 2006-09-25
Yes!  Well, that allowed me to have permissions now.  Just one thing, can the partitions be viewable in "Computer" and how would I go about doing that?

You've been a great help Aysiu!

-cerverx27

---

### Post by aysiu on 2006-09-25
I don't know about Computer, but you can put it in Places by adding it to your Nautilus bookmarks.

---

### Post by cerverx27 on 2006-09-25
Yeah, its handy to put it in Nautilus's bookmarks.

I wonder if it matters which mounting place you choose.

For the two drives I chose the /mnt folder, but I've seen drives show up in the Computer window when I mount them in the /media folder.

Hmmm.

---

