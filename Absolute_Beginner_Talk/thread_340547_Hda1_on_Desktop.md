---
title: "Hda1 on Desktop?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Michaelt74 on 2007-01-17
Hi

I'm trying to move over to ubuntu and recently installed using the 'manually edit partition table'

The install went fine but when it started up I saw the hda1 (windows) partition on my desktop.
I can unmount it by right clicking and choosing 'unmount volume', but on start up it mounts again. I would like to prevent it from mounting when I restart. I found some 'fstab' commands but I'm not sure what they are. Any ideas? Please reply with step by step commands a
s I'm new to this

Why does it mount? How can I prevent it from mounting in future installs?

Thanks!

---

### Post by taurus on 2007-01-17
Post your /etc/fstab here then.

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

p.s.  Just put a # in front of an entry for /dev/hda1 to prevent it from mounting each time you boot Ubuntu.

```
gksudo gedit /etc/fstab
```

---

### Post by PetePete on 2007-01-17
ok this is from memory so sorry if its a bit wrong..
open console..
sudo vi /etc/fstab

(or substitute vi for what ever text editor you want)

look for where it says something about hda1 and put # at the staart of any lines which mention it

---

### Post by Michaelt74 on 2007-01-17
Thanks for your assistance!

---

