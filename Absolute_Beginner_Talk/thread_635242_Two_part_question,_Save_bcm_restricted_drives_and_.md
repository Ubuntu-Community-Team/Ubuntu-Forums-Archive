---
title: "Two part question, Save bcm restricted drives and move /boot and /root partitions"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Teknyk on 2007-12-08
Question #1 is probably something easy that I just can't find.
I have a Broadcom wireless adapter and it works fine using the restricted drivers. My only issue is a have to plug into my LAN to so the restricted drivers manager can get it. I would like to burn a copy to a disc so I don't have to plug into my LAN just to get it working when/if I have to reinstall. Is there an easy way to copy it off my system as it is right now? Can I get a copy from where ever the driver manager gets it?
This is in preparation for question #2

Question #2
I currently have one large partition with straight Ubuntu. (XP was dumped when GG was released :biggrin: ) I have seen some of the posts for resizing or moving partitions for /home and /root but none for /boot.
Since my /boot file is only 17M right now I am hoping to resize partitions to the following;
/boot = 500M
/root = 15G
/home = all the rest (up to my wimpy 80G total capacity)

So can /boot be moved/mounted
As a single user laptop should I even worry about /boot and /root being on their own or is this, (ready for it?)... "/moot"? :lolflag:

I am not worried about smoking my current install as everything important is already backed up, as are all my "fixes" but I would like to try resizing just for the learning experience. I read somewhere here "If it aint broken you aint learning"

---

### Post by Teknyk on 2007-12-09
Ok I was able to resize and move my /home to its own partition. I'll just wait to set /boot on its own partition until I have to reinstall next time. I'm going tp go searching for a way to backup my broadcom drivers for my wireless now. If anyone knows an easy way to do this please let me know. :-s

---

### Post by louieb on 2007-12-09
> **Teknyk said:**
> I'm going tp go searching for a way to backup my broadcom drivers for my wireless now. If anyone knows an easy way to do this please let me know. :-s
Sounds like **aptoncd **is what your looking for.

---

