---
title: "Roll back Gusty to Feisty"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by MrManager on 2007-10-24
I am having video card compatibility problems, or so I believe with Gusty.  Is there a way to roll back to Feisty without deleting a partition?

---

### Post by danm-koder on 2007-10-24
I'm not quite sure about this, but probably there isn't anyway of downgrading your ubuntu install... You would have to format your partition and do a fresh install... However, what is the problem you're facing?? Maybe the community can help (??) :D

---

### Post by Perpetual on 2007-10-24
There is not a means to 'roll back'.  If your /home is on a seperate partition, you could reinstall 7.04 and not format /home.  I would suggest backing up first though...just in case.  If /home is not on a seperate partition, backup your files to external media then install 7.04.

Edit: yes, as danm-koder stated, maybe the community can assist you with working out the issues before your install 7.04.

---

### Post by mivo on 2007-10-24
When I rolled back to Feisty (keeping /home), Gnome threw some error messages, so I had to delete the Gnome configuration. The rest worked, though.

---

### Post by jettachamp26 on 2007-10-24
when I upgraded from feisty to gutsy, I lost volume and playback using rhythmbox can anyone help?

---

### Post by grifftel on 2007-10-24
This happened to me too. I had to add the volume to /etc/fstab and make a folder for it in /media. It was simple to do. 

/dev/sda1 /media/YOURVOLUME ntfs-3g defaults,locale=en_GB.UTF-8 0 0 0

And a folder called YOURVOLUME in /media

then reboot

That's if your system is in english though

---

### Post by MrManager on 2007-10-25
> **grifftel said:**
> This happened to me too. I had to add the volume to /etc/fstab and make a folder for it in /media. It was simple to do. 

/dev/sda1 /media/YOURVOLUME ntfs-3g defaults,locale=en_GB.UTF-8 0 0 0

And a folder called YOURVOLUME in /media

then reboot

That's if your system is in english though

Could you dumb down what you said?  The whole reason I was trying to rollback in the first place was because I had to boot in GNOME failsafe, and then I was having sound issues, so this might be the problem.  But I'm not entirely sure what you mean.

---

