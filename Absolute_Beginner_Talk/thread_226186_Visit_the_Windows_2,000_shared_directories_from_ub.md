---
title: "Visit the Windows 2,000 shared directories from ubuntu"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by liulm on 2006-07-30
Visit the Windows 2,000 shared directories from ubuntu,how?

---

### Post by OU812 on 2006-07-31
Usually accessing windows partitions is a two-step process:

1. Adding each partition to your /etc/fstab file and
2. Making a directory for your entry.

Instructions can be found here

[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

john

---

### Post by NewWithoutClue on 2006-07-31
Do you mean a Windows Network share, or are you talking about an actual partition on your Disk?

For the Network:
```

sudo apt-get install smbfs
sudo mkdir /home/shares
sudo mount -t smbfs //remote_computer's_address/Share_Name /home/shares
ls /home/shares

```

To unmount the share, issue:
```

sudo umount /home/shares

```

Please note:
There can, and probably will, be permission problems with reading and writing. To learn more about mounting windows shares and shares in generel with smbfs, issue this command and read it's output:
```

man mount.smbfs

```

For a partition, follow the above guy's posted instructions.

Regards,
Paul

---

### Post by liulm on 2006-07-31
Thank you .I do it allow your bewrite,Can visite the Windows share folder.Now I have another problem,When I visite the ubunto shared directories from Window 2,000,the content is not the content of shared folder,but liulm's content.(liulm ia my ubunto pc' name).
why?How can I do?

---

