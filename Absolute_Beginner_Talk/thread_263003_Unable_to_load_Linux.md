---
title: "Unable to load Linux"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by papuaoshi on 2006-09-22
After changing some hardware (CPU, MB), linux kernel doesnt boot, even in recovery mode.

PS. CPU arch is the same (64b).
PS.PS. XP loads well.

---

### Post by bulldog on 2006-09-22
I think it's because Ubuntu has your 'old' hardware configured.
Now you changed important items and Ubuntu can't figure it out.

In windows you can install the new drivers for your MoBo.

I'm not sure if there's a solution for it,never done it and shouldn't know how to solve it.

---

### Post by steve.horsley on 2006-09-22
Try the live CD to start with, to check if there is a fundamental hardware compatibility problem. Assuming there isn't, I really don't know how to trigger the kind of hardware discovery that the installer does, so I would probably use the live CD to mount and back up /home, and then re-install the OS.

---

### Post by papuaoshi on 2006-09-22
> **steve.horsley said:**
> Try the live CD to start with, to check if there is a fundamental hardware compatibility problem. Assuming there isn't, I really don't know how to trigger the kind of hardware discovery that the installer does, so I would probably use the live CD to mount and back up /home, and then re-install the OS.

Live CD boots well.

So how to re-install Ubuntu? I want to keep my newly installed software. I know live CD can only install a new copy...

And how to mount my old /home? What I must add to fstab (old home is ext3)?

---

### Post by bulldog on 2006-09-22
When you do a new install,do the partitioning manual.
Mount your swap and / and /home but don't format your home.

Mounting your existing Ubuntu from the live cd 

sudo mkdir /mnt/ubuntu
sudo mount /dev/hda? /mnt/ubuntu [where hda? is your ubuntu]

Now you can go into the dir ubuntu and save your data.

{the live cd boots well because it detects your new hardware and set it up,your install is configured with your old hardware,which you replaced by the new ones,this is a mismatch I'm afraid,so Ubuntu stops booting}

---

### Post by papuaoshi on 2006-09-22
10x!

---

