---
title: "Expand /home ext3 partition"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by CupofDice on 2006-10-25
I just took away 20 gigs from XP, and I want to add that space to my /home ext3 partition. How do I go about it with my breezy live cd. Thanks for any help.

---

### Post by Bachstelze on 2006-10-25
Just run GParted and expand your partition to the free space if they are contiguous.

If they are not, copy the partition into the free space first, and then grow it. Don't forget to edit your fstab to match the new partition.

---

### Post by CupofDice on 2006-10-25
With the live cd? Do I need to edit fstab if I only need to do your first sentence? And how do I tell if the free space is contiguous.

---

### Post by Bachstelze on 2006-10-25
Nope, editing the fstab will only be needed if the identifier of your partition (/dev/whatever) has changed. If you just resize it, it should not.

---

### Post by CupofDice on 2006-10-25
Alright I am in breezy live cd right now, and using gparted. It doesn't give me an option to go above 9994mb, only to resize down.

---

### Post by Bachstelze on 2006-10-25
Can we have a screenshot ?

---

### Post by CupofDice on 2006-10-25
[[IMG]http://img84.imageshack.us/img84/4177/screenshotjs6.th.png[/IMG]]("[URL=http://img84.imageshack.us/my.php?image=screenshotjs6.png)"][[IMG]http://img84.imageshack.us/img84/4177/screenshotjs6.th.png[/IMG]](http://img84.imageshack.us/my.php?image=screenshotjs6.png)[/URL]

---

### Post by Bachstelze on 2006-10-25
As I told you in my first message, your partition and the free space ar enot contiguous so you have three options :

1) Create a new partition in the 20 G free space and mount it in a subdir of your home.

2) Copy/paste your home partition into the 20 G free space.

3) Completely modify your hard drive partiton table so the 30 G free space are continuous. This will work but might be a bit long and tedious. What in there do you want to keep ? I see a nearly empty ext3, if you can afford getting rid of it, we will be able to repatrition your drive without reinstalling anything.

---

### Post by CupofDice on 2006-10-25
Most of my home is filled. Only 1.3 gigs or so left. That ext3 is a partition I create a few weeks ago. 2 sounds good. I have edited my fstab before. How do I copy/paste /home into the free space?

---

### Post by CupofDice on 2006-10-25
Can't believe I forgot about this.
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")
If I take away more space from windows right now, will it automatically join the 20 gigs of free space I now have?

Edit-Alright, none of that will help because /home is already on a partition.

---

### Post by Bachstelze on 2006-10-25
Since they are contiguous, yes. As I said, you can copy and paste the whole /home partition in the free space. Just right click > copy and then right click in the free space and paste :) It will take quite a while though.

---

### Post by CupofDice on 2006-10-25
Yeah, but how do I get it mounted as /home? I know how to edit fstab now, but I can't unmount /home in gparted. I was going to make a new thread, but is what I wrote below feasible?

"I wanted to copy my /home on my hda6 ext3 partition to a 30 gig ext3 partition (not yet created). I then wanted to edit fstab to mount the former partition in /mnt (temporarily) and mount the new partition in /home. This is the problem because I can't unmount hda6 with it in use and the live cd was no help. I was wondering if I could create the 30 gig or so ext3 partition right now, reinstall ubuntu, mount that as /home, mount the former /home partition as /mnt/formerhome, then once everything is done copy everything from /mnt/formerhome to /home. Now that I think about do I need to reinstall to do this, or can I just complete the mounting stage, restart, copy /mnt/formerhome to /home, and done? If not then I will just mount the new partition in /home/user/.

Edit- Or is it possible to create the new partition, edit fstab to have the old hda6 show in /mnt, and the new partition to show in /home, then save.

---

### Post by Bachstelze on 2006-10-25
You can perfectly well edit your fstab from the live cd, just mount your root partition, like this :

```

sudo -i
mkdir /mnt/root
mount -t ext3 /dev/whatever /mnt/root
nano /mnt/root/etc/fstab

```

So when you reboot, the system will mount the new home instead of the old one, which you can delete if you copied it in the free space as I suggested.

As I told you, no need to reinstall anything, that would be a waste of time.

---

### Post by mdwuznik on 2006-10-25
Judging by your screenshot You shall rather resize your extended partition to eat up the non-allocated space, than move the partitions in the extended partitions to have the free space next to the partition you want to grow, than grow the partition you want to :)

Cheers
Michal

---

### Post by CupofDice on 2006-10-25
Okay I think I understand now Hymn.

---

### Post by CupofDice on 2006-10-25
Success! Thanks for the help.:D

Oh, and if anyone ever reads this try this to copy your /home.

```
$cd /home/
$find . -depth -print0 | cpio --null --sparse -pvd /where/you/are/copying
```
from-
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

Edit to answer mdwuznik's question-

From ubuntuwordpress-
"Now, Copy files over:
Since the &#8220;/home&#8221; directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely. Therefore, we use something we learn from the Debian archiving guide"

I ran into an error trying to do a simple copy, so then I went with that method and everything worked perfectly.

---

### Post by Bachstelze on 2006-10-25
You're welcome ;)

---

### Post by mdwuznik on 2006-10-25
Sorry for my previous answer, which was send after some delay and has not included the discussion in the meantime.

BTW:This cpio trick is a pure "confuse the noob command":) I can't see any reason for it to be better than dd on a partition level or sudo cp -rp on the filesystem level. Enlighten me if there's some reason...

---

