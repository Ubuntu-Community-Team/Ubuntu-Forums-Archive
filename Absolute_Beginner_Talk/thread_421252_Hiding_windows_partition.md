---
title: "Hiding windows partition"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by tomcheng76 on 2007-04-24
How to hide the icon for windows' partitions under "Computer":confused: 
I dont need them,Thanks

---

### Post by sgbeamer on 2007-04-24
Remove the line describing it from /etc/fstab and it should go away on the next boot.

---

### Post by Stickymaddness on 2007-04-24
Open a terminal and type

```

sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

```

Then change the lines containing "ntfs" in them, eg:

```

/dev/hda1 /media/hda1 ntfs defaults 0 0

```

To

```

#/dev/hda1 /media/hda1 ntfs defaults 0 0

```

**Only do this to lines containing "ntfs"!!** 

After all is done, save & restart...

---

### Post by tomcheng76 on 2007-04-24
actually i dont have the line for the partition in fstab 
I have installed gparted
when i open gparted using root power, it will automatically made a "LABELNAME" Directory in /media and mount them
i dunno why the partition icons are on the "COMPUTER" page

---

