---
title: "Trouble writing to slave hard drive."
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Dev0205 on 2007-05-25
Oh great and powerful Linux community,

I have two hard drives, one formatted for Linux, the other I use to store my music and such(NTFS). I'm having a bit of trouble writing files to my second drive. I've tried to set permissions to read-write as root but have had no luck. I'd like to avoid formating the drive if possible. Any ideas?

In short : Unable to write to my second internal hard drive that is NTFS format. Need help.

Thank you in advance,
Dev

---

### Post by Paperclips4u on 2007-05-25
Which version of Ubuntu are you running?

---

### Post by Paperclips4u on 2007-05-25
Nevermind, this link should cover whatever version you have. :)

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Follow Givre's instructions carefully :)

---

### Post by Dev0205 on 2007-05-25
Paperclips4u,

I was just about to edit my post to include that I have given ntfs-3g a shot. I installed it but am still unable to set any permissions or write to the drive. I'll try a reboot maybe? Thanks for the quick reply.

---

### Post by Neil Purling on 2007-05-25
Obviously the perfect solution would be to re-format the drive as FAT32. How much stored data are we talking about? You should always have backups  on CD-R or DVD-R anyway
There is something called ntfs3g. I understand this may cause a problem or two.
You should search this forum for references to it.

---

### Post by Paperclips4u on 2007-05-25
Dev0205,

Maybe try removing ntfs3g and then reinstalling it verbose from Givre's post. It's possible that things didn't get set up correctly when ntfs3g first moved in.

Just for reference, which Ubuntu version?

---

### Post by Dev0205 on 2007-05-25
*Edit*

With the help of many Mt.Dews and some elbow grease, I was able to finally mount the drive as NTFS but only from the terminal and as root. Sudo this Sudo that! Thanks for pointing me in the right direction.

Cheers,
Dev

---

