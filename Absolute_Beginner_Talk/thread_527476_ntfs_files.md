---
title: "ntfs files"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by em11488 on 2007-08-16
I have an external with all my files from my laptop formatted in ntfs. when I try to copy them to my ext3 linux harddrive it wont. Is there anyway to get ubuntu to copy these files or no. if you respond, please respond with a very simple answer. I just started using ubuntu so I dont know anything about those tar.gz packs or how to use them or what to do.
I greatly appreciate the help. thanks

---

### Post by Rocket2DMn on 2007-08-16
By default, Ubuntu can only see files on ntfs drives (I'm not sure if it can read them or not - it certainly can't write them), but if you install ntfs-3g, you can read/write files on an ntfs partition
Check out this little HowTo: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by bodhi.zazen on 2007-08-16
ntfs-config is a gui front end for ntfs-3g : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

