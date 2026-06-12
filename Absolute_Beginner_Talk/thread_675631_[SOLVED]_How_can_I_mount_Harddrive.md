---
title: "[SOLVED] How can I mount Harddrive?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Jmejme on 2008-01-22
ok im trying to se whats goin on with my friends laptop and its like completely jacked up. im running th live disk in it right now but for some reason i cant mount the harddrive is there a command that mounts anything that canmount. i thought i saw it some where...? it gives a lil white loading bar when he trys to start xp... there are important files on there and we need them HELP PLEASE!!!

thanks in advance

---

### Post by PurposeOfReason on 2008-01-22
The command you're thinking is:

sudo mount /dev/sda (or whatever the drive is)

but I don't think that works unless the drive is in the fstab. Worth a shot though.

---

### Post by question_chick on 2008-01-22
Do you get any errors when trying to mount or anything?

---

### Post by Jmejme on 2008-01-22
i tried to mount so that i could read the ntfs filesystem. its running xp. it doesnt even show up under disks in the system panel is there a mount -s type command i think that was it

i meant -a not -s

---

### Post by Jmejme on 2008-01-22
nothing ????

---

### Post by rosegarden78 on 2008-01-22
You'll need the ntfs-3g and fuse packages to install from the repositories.  Using them is another matter for you that I cannot assist.  Ubuntu Forum Staff tells me these programs work 100% of the time.  And there is program for XP to write to EXT2, EXT3.

---

### Post by Jmejme on 2008-01-22
k well we found out that the problm was a smart failure basically the harddrive is dying. im trying to maybe istall to the harddrive to atleast giet it to see the hd but thanks anyway

---

### Post by Jmejme on 2008-01-23
no go. the harddrive is dead were pretty sure! so basically, if this post basically has no purpose you could close/delete it. is there a way for me to...or do i ask the big guys ta do it for me? kk well thanks for the help!!!

---

