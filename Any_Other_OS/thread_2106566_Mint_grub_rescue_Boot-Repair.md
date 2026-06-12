---
title: "Mint grub rescue Boot-Repair"
date: 2013-01-18
forum: Any Other OS
---

### Post by bilmaruf on 2013-01-18
linux mint failed to boot. 

please help. 

when i did separate my boot partition and install grub on it then it was run one or two times but now facing same problem " grub rescue" , " you need to load the kernel first" 
etc. 

i am new in linux mint please help to solve the prob.

here is my boot info.

[http://paste.ubuntu.com/1547675/](http://paste.ubuntu.com/1547675/)

---

### Post by oldfred on 2013-01-19
Moved to your own thread. We start to get confused with users with similar but different issues.

It looks like you have repaired or installed with and without separate /boot partition. Old grub & kernel entries are in / in /boot folder and new entries are in /boot partition. 

It looks like you should be able to boot.

If not, it may be an issue on /boot and when or where mounted. Normally entry should be /boot/vmlinuz etc not directly to /vmlinuz....

You could use e to edit grub and add /boot to front of /vmlinuz.. and /initrd..... lines in boot stanza.

I generally prefer smaller system partitions of 10 to 25GB and no separate /boot for most desktops. Those configured more as servers with RAID, LMV or other special cases may need the separate /boot.

---

