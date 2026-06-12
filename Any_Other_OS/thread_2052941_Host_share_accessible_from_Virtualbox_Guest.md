---
title: "Host share accessible from Virtualbox Guest"
date: 2012-09-04
forum: Any Other OS
---

### Post by manuleka on 2012-09-04
Platform: Mint 13 Mate + latest updates
Virtualbox 4.1.12
---
Goal: 
1. Automount ntfs Partitions
2. Share the automounted partitions
3. VirtualBox Windows XP Guest can access these partitions [read+write]

Now before i set the partitions to automount, i'm not familiar with fstab but after doing some research online i found that this is a basic setup for automounting ntfs, (exact script added to fstab)

```

# ntfs partitions
# dat1
UUID="E490C9BA90C99388" /home/blakmunky/Documents/dat1 ntfs users,defaults 0 0
# dat2
UUID="7135D46A6156EDD1" /home/blakmunky/Documents/dat2 ntfs users,defaults 0 0
# dat3
UUID="50C8691CC8690218" /home/blakmunky/Documents/dat3 ntfs users,defaults 0 0

```

do i need to add some sort of permissions on these lines so i can freely access (read+write) to these mount points (and subfolders) without having to use username:password and not having to set this on samba as well

---

