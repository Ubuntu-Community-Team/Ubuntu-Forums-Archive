---
title: "Uninstall ---&gt; Reinstall"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by carpola on 2007-04-26
I'm trying to uninstall everything from my Linux partition, reformat that partition, make it NTFS, merge that NTFS with my windows NTFS partition, and then take that whole partition and create a new one from that to make a new linux partition.

Basically, i wanted everything to go to windows so i can create a new linux partition because my linux now is just broken and i want to reinstall. anyone help? need clarification?

---

### Post by Sef on 2007-04-26
> I'm trying to uninstall everything from my Linux partition, reformat that partition, make it NTFS, merge that NTFS with my windows NTFS partition, and then take that whole partition and create a new one from that to make a new linux partition.

Basically, i wanted everything to go to windows so i can create a new linux partition because my linux now is just broken and i want to reinstall. anyone help? need clarification?


Just reformat your GNU/Linux partition.   Use ext3, the default when you reinstall GNU/Linux.  You also need to reformat swap at the same time.  Once you do that, your GNU/LInux should run fine.

---

### Post by eldepeche on 2007-04-26
Are you trying to dual boot? The way you described it, it sounds like you just want your computer to run Ubuntu, and not Windows.

---

### Post by Josey on 2007-04-26
Put /home on a separate partition from / and formatting the os will be alot less painful in the future.

---

### Post by sailor2001 on 2007-04-26
I would suggest you download an ubuntu iso disk first before anything.....Formating the partition takes place as you install from the disk and is quite simple........install manually and a slider is there for you to size your free space.  You can remove old partitions with gparted (synaptics)

---

### Post by carpola on 2007-04-26
The thing is, I was originally dual booting XP and ubuntu but then i tried getting feisty using the update manager and that failed completely, leaving me unable to access ubuntu. the only way for me to reinstall ubuntu was to wipe the linux partition clean, merge it with the windows, then separate a new partition from the windows to make the new linux partition. i have to do this because when i'm trying to install off of the live cd, it gives me about two options, take more space off of my windows partition or wipe my entire HD clean.

---

### Post by Josey on 2007-04-26
> **carpola said:**
> The thing is, I was originally dual booting XP and ubuntu but then i tried getting feisty using the update manager and that failed completely, leaving me unable to access ubuntu. the only way for me to reinstall ubuntu was to wipe the linux partition clean, merge it with the windows, then separate a new partition from the windows to make the new linux partition. i have to do this because when i'm trying to install off of the live cd, it gives me about two options, take more space off of my windows partition or wipe my entire HD clean.

Manually is an option too isn't it??

---

### Post by carpola on 2007-04-26
The thing is, I don't know how to do it. Last time, I reformatted the Linux partition, making it NTFS so I could merge it with my Windows partition. WHen that happened, I obviously screwed something up because it wasn't a successful merge and it cleared everything from my Windows partition.

Any advice on what/how to do this?

---

### Post by Josey on 2007-04-26
I would read up on using the "manual" option.  It's not as hard as you might think.  I was wary of it initially but after doing it a few times now I'm pretty comfortable with it.  I think in the long run this will save you some headaches to learn this.  It's really quite simple after you do it a couple times.

This may help you.
[http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)

Something that looks like this in the manual page and you're golden. :)

```

       #1 primary   15.1 GB   K  ntfs       /media/sda1
       #2 primary    8.0 GB   f  ext3       /
       #5 logical   45.9 GB   f  ext3       /home
       #6 logical    1.0 GB   f  swap       swap   

```

Just make sure not to touch the ntfs (windows xp) partition.

---

### Post by Josey on 2007-04-26
My post above seperates /home and / as I feel this is a good idea.

If your linux install ever breaks again all you will need to do is format / and reinstall leaving all your personal files on /home intact.

---

