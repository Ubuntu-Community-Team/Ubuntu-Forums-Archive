---
title: "sed query?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Miguellint on 2007-03-09
Hi all... Is the following an accurate translation of this sed command:

sed 's/zzz/usr/g' /etc/fstab.zzz > /etc/fstab

English translation: Find every instance of 'zzz' in the file /etc/fstab.zzz and replace it with 'usr'. And then copy the modified /etc/fstab.zzz to /etc/fstab, overwriting whatever was in /etc/fstab.

Thanks
Miguel

---

### Post by enopepsoo on 2007-03-10
that looks right.  Why not just test it out with some file other than your fstab :P

---

### Post by Miguellint on 2007-03-10
Hi enopepsoo....Funnily enough I thought of the same thing after I'd posted but I was away from my Ubuntu computer.

Got back to it a short while ago, tried out the command and it does what I thought it does.

Thanks

Regards
Miguel

---

