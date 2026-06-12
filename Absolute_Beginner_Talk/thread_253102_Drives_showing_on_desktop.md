---
title: "Drives showing on desktop?"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by OneEyedMan on 2006-09-07
I'm not sure if this is a problem or what, but it's the first confusing thing I've seen.

I've been running a Dualboot XP/Ubuntu box for a month now, and Ubuntu is behaving very nicely. I haven't had a single issue. Until I looked at the desktop a while back and noticed that instead of the clean, unbroken dekstop I was used to, I now have 2 icons on it, one for "hda1" and one for my storage hard drive "storage".

I'd rather not have them there, since I can find them just fine with "Places" But I'm leary of just deleting them, since I don't want to wipe my drives. So could someone tell me how to move/remove these? Shoudl I unmount them? or what?

Man, just when I think I've got a handle on things...:confused:

-Jeff

---

### Post by GonZo1323 on 2006-09-07
should be able to just right click and delete the are only shortcuts

---

### Post by orb9220 on 2006-09-07
No they will come back. You have to remap them from the /media folder.

open a term and run  gksudo nautilus
now in nautilus go to home folder and create a folder called drives. In the drives folder create one folder called hda1 and one called storage.

now run term and enter gksudo gedit /etc/fstab and edit them. the two should be /media/hda1 and /media/storage change to /home/drives/hda1 and /home/drives/storage.

You will still have access but the drives will now be found in home/drives and not appear on desktop.

Anything in /media from fstab gets displayed on the desktop.

---

### Post by bollix47 on 2006-09-07
See if anything [here]("http://www.ubuntuforums.org/showthread.php?t=226732&highlight=Drives+showing+desktop") helps.

---

### Post by Rui Pais on 2006-09-07
Hi,
if you don't want to see mounted volumes on your Gnome desktop run gconf-editor 
(on Main menu is at Applications->System Tools->Configuration Editor) 
and navigate to:
/apps/nautilus/desktop/volumes_visible 
and uncheck the checked box.
That's all. Don't know if there is a simpler way...

---

### Post by orb9220 on 2006-09-07
No that is simplest way. Tho It also disables the cdrom icon too I belive.

---

### Post by OneEyedMan on 2006-09-07
Thanks everyone. Orb9220, I went ahead and did the fstab edit you suggested, and it seems to have worked perfectly. First term operation for me, too. Go me!

I'm going to jump to an assumption here, but the operation would work in reverse, wouldn't it? just editing the fstab and redirecting voulmes to /media/hda1, for example?

That was easier than I had thought it would be. I'm starting to see why the terminal is such a big deal.

-J

---

### Post by orb9220 on 2006-09-07
Well good for you. But remember most fstab problems are a result from syntax errors. Like when I started learning mine was /home/[COLOR="SandyBrown"]D[/COLOR]rives/ but when i  edited the fstab I had /home/[COLOR="DarkOrange"]d[/COLOR]rives not thinking about case-sensitive characters.

---

### Post by jimrz on 2006-09-07
> **OneEyedMan said:**
> Thanks everyone. Orb9220, I went ahead and did the fstab edit you suggested, and it seems to have worked perfectly. First term operation for me, too. Go me!

I'm going to jump to an assumption here, but the operation would work in reverse, wouldn't it? just editing the fstab and redirecting voulmes to /media/hda1, for example?

That was easier than I had thought it would be. I'm starting to see why the terminal is such a big deal.

-J

:D  Welcome aboard

---

### Post by jimrz on 2006-09-07
> **OneEyedMan said:**
> Thanks everyone. Orb9220, I went ahead and did the fstab edit you suggested, and it seems to have worked perfectly. First term operation for me, too. Go me!

I'm going to jump to an assumption here, but the operation would work in reverse, wouldn't it? just editing the fstab and redirecting voulmes to /media/hda1, for example?

That was easier than I had thought it would be. I'm starting to see why the terminal is such a big deal.

-J

:D  Welcome aboard

---

### Post by Rui Pais on 2006-09-08
> **orb9220 said:**
> Tho It also disables the cdrom icon too I belive.
Uhmm, i'm not sure... but i think that uncheck volumes_visible will prevents only the mounted hardisk partitions not media mount points. 

I'm not using gnome (using nautilus but with --nodesktop flag) i will check on my wifes desktop to see how happens...

*EDIT:*
No, you are right... uncheck volumes_visible prevents media icons on desktop, but auto mounting still works normally. 
But in my case, harddisk drives (like hda, hdb) never appear with or without the volumes checked.

Anyway, OneEyedMan solved the issue with your other suggestion... good!

---

