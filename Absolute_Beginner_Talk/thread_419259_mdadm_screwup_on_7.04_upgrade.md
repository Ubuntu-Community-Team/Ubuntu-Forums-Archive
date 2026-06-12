---
title: "mdadm screwup on 7.04 upgrade"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-04-22
I screwed up on my upgrade to 7.04....I hit forward button before the required mdadm files had downloaded.  I noticed that everywhere these files were required they could not be found and install reverted to emergency configuration?  Do I need to do a reinstall and include these files?  System booted up find and seems to working OK so far?????????  Are these files associated with RAID????  I don't have SATA hard drives just old IDE.

---

### Post by oleoleole on 2007-04-24
> **rggavubt said:**
> I screwed up on my upgrade to 7.04....I hit forward button before the required mdadm files had downloaded.  I noticed that everywhere these files were required they could not be found and install reverted to emergency configuration?  Do I need to do a reinstall and include these files?  System booted up find and seems to working OK so far?????????  Are these files associated with RAID????  I don't have SATA hard drives just old IDE.

If you need to use RAID, you must have mdadm. To reinstall:
```
sudo aptitude reinstall mdadm
```

If you dont have any RAID-devices, its not necesarry at all to have them. I needed to remove it completelly, because it fscked up my initrd and denied to boot.

---

### Post by rggavubt on 2007-04-24
Thanks for the reply.  I don't have raid...using a old freebee PC that I'm trying Ubuntu on.  Everything seems to still be working OK so I think I'm OK.

---

