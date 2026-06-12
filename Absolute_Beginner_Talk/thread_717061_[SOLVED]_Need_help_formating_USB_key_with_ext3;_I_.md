---
title: "[SOLVED] Need help formating USB key with ext3; I can't write to it.."
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2008-03-06
I just finished running Gparted inside VMware, using it to format this 4 gig USB thumb drive to ext3, along with a smaller fat32 partition after it.  Both partitions were created with no problem.  After shutting VMware down, unplugging the key, then plugging it back in, both partitions automounted and opened up in Nautilus.  But still, I have no write ability with the ext partition.  I can do anything I want with the fat32 partition.

How do I get full access to an ext3 partition that I created?

---

### Post by mikeyphi on 2008-03-06
Right-click the icon, select Properties / permissions and see if you can change access

---

### Post by taurus on 2008-03-06
Try changing the ownership of the mount point for the ext3 partition from root to your login name.  _Assuming_ it is mounted to /media/disk and your login name is diablo, run

```
sudo chown -R diablo:diablo /media/disk
ls -la /media
```

---

### Post by diablo75 on 2008-03-06
I remembered that I had installed a couple nautilus scripts that allow me to right click on a folder (the drive itself, in this case) and say "root-nautilus-here", which then asks for my admin password.  After doing that, I am then able to change access permissions, which were grayed out before.

I think I got it now.  Thanks guys!

---

