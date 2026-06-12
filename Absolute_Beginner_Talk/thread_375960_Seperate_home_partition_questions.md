---
title: "Seperate /home partition questions"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-04
I was looking at the instructions at:[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
and was getting ready to attempt this with my trusty Knoppix cd. Does it matter where the partition is created? I assume the best place would be between the root partition and the swap partition. After the commands listed I also assume that /home will be visible as a seperate drive after it is set up to automount via the fstab command. Will the old /home still be in the filesystem or will all the /home info go straight to the /home partition? Is there a more detailed guide for this that explains more than just the steps to create and mount the seperate partition?

---

### Post by Kobalt on 2007-03-04
If you follow this guide you will not see /home as a separate partition, it will be transparent, just as if /home was on the same partition as /. You will only have one /home, and it will be on its own partition. 
I think you can find plenty of infos about separate /home partitions on this forum, but aysiu's tutorial (the one you follow) is pretty much all you need to know about that...

---

### Post by confused57 on 2007-03-04
A separate home partition is a good idea, as Kobalt mentioned you won't even know it's on a separate partition...you might want to consider just a separate /media/data partition, also.
This would be easy, you'd just make a new partition formatted (ext3?), make a directory to mount it, then add an entry to your /etc/fstab.  Aysiu's guide is the best one I've seen for creating a new separate home partition.

---

### Post by 67GTA on 2007-03-04
I'm still a little confused. If I create this home partition will my home directory still be visible under the file system as before or will I have to mount the home partition to view it's contents?

---

### Post by lamalex on 2007-03-04
> **67GTA said:**
> I'm still a little confused. If I create this home partition will my home directory still be visible under the file system as before or will I have to mount the home partition to view it's contents?

fstab will take care of that

---

### Post by Sefrin on 2007-03-04
> **67GTA said:**
> If I create this home partition will my home directory still be visible under the file system as before or will I have to mount the home partition to view it's contents?

I believe it will still be visible under the file system.  The installer should take care of all this after you make your appropriate partitions.  Physically, the partition is separate from everything else, but during install you tell Ubuntu to look in that specific spot for your /home and it takes care of the rest.  I have to get on this and do it myself.  It's practically "My Documents" on steroids.  :)

---

### Post by confused57 on 2007-03-04
> **Iamalex said:**
> fstab will take care of that

Yes, this part of aysiu's instructions mount it in fstab:
> Next, we're going to specify to use the new home partition as /home:
sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab

You'll then be taken to the nano text editor. Add in this line:
/dev/hda7 /home ext3 nodev,nosuid 0 2

Then save (Control-X), confirm (Y), and exit (Enter) 

---

### Post by 67GTA on 2007-03-04
Thanks for the help! How do you mark a post as RESOLVED?

---

### Post by Kobalt on 2007-03-04
You can do that by editing your first post :rolleyes:

---

### Post by 67GTA on 2007-03-04
Ok, that didn't go to well. Something went wrong, and the backup commands aren't working. I tried to log in and got error message:

home directory listed as /home/shawnr but does not appear to exist. Do you want to log in with the / (root) directory as home directory? 

CLICKED YES>

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

CLICKED OK>

/etc/gdm/Presession/Default: Registering your session with wtmp and utmp

/etc/gdm/Presession/Default: Running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h " " -l ":0" "shawnr"

/etc/gdm/xsession: Beginning session setup...

(gnome-session:4789): libgnomevfs-WARNING **: Unable to create ~gnome2 directory: no such file or directory

Could not create per-user gnome configuration directory ' /home/shawnr/.gnome2/': no such file or directory

What the H@#$ happened and where do I start looking? I copied the commands from the psychocat webpage and put my own info in place of theirs, so I have no idea.

---

### Post by 67GTA on 2007-03-04
Could I reverse some of the commands and put home back on the root partition and try it again?

---

### Post by 67GTA on 2007-03-04
How do I get to the fstab file with the terminal to try to take out the line to mount my seperate home partition?

---

### Post by 67GTA on 2007-03-04
I logged into recovery mode and pulled up the fstab file. It looks fine. Something has changed with my home directory. I have ran the home backup commands several times, so I am sure it is back on the original partition. Where to go from here? I haven't really gotten far with this new installation. Would it be easier to just reinstall?

---

### Post by raul_ on 2007-03-04
Could you please post your fstab file? That may give us some lights

---

### Post by 67GTA on 2007-03-04
I am back in now, but not sure how to completely restore everything. I created a new home directory (since it said mine was missing at log in).

sudo mkdir /home/shawnr
sudo chown shawnr /home/shawnr

Now I have a new home directory and my old home backup is right beside it. How do I use my old home directory and get rid of the new one without screwing everything up?

---

### Post by 67GTA on 2007-03-04
Bump

---

### Post by confused57 on 2007-03-04
> **67GTA said:**
> I am back in now, but not sure how to completely restore everything. I created a new home directory (since it said mine was missing at log in).

sudo mkdir /home/shawnr
sudo chown shawnr /home/shawnr

Now I have a new home directory and my old home backup is right beside it. How do I use my old home directory and get rid of the new one without screwing everything up?

I can't guarantee it'll work, but you usually restore a backup by something like this:

```
sudo cp /home/shawnr_backup /home/shawnr
```

this should copy the contents of the backup to the new file.

---

