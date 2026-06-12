---
title: "How do i view my HDD while running the Live CD"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by slipk487 on 2006-04-01
i dont know i to view my HDD while rinning the Live CD and i need to to free up space because i cant log in because of the lack of free space

---

### Post by taurus on 2006-04-01
Yes, you can view your harddrive from LiveCD.  Assuming that you have Ubuntu (or Dapper) on /dev/hda3, from a terminal, do
```

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda3 /mnt/ubuntu
cd /mnt/ubuntu

```
Now, you can probably empty /mnt/ubuntu/tmp with the sudo command to free up some space or remove some files that you don't need...
```

sudo rm -rf /mnt/ubuntu/tmp/*

```
Then, unmount it before reboot as
```

cd /
sudo umount /mnt/ubuntu

```

---

### Post by ace2005 on 2006-04-01
[QUOTE=slipk487]i dont know i to view my HDD while rinning the Live CD and i need to to free up space because i cant log in because of the lack of free space[/QUOTE]

Well with knoppix you have links to all your hard disks on the kde desktop, and you can delete the files when it opens in konqueror but in ubuntu it would depend on whether you are using ubuntu or kubuntu :KS ?

---

### Post by slipk487 on 2006-04-01
thx it worked and know i just need to see if it will let me login when i reboot

---

