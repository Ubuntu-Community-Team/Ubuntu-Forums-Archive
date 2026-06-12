---
title: "Hard Drive Changes Places"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by yhack on 2008-04-05
Hi,

I've got a HDD which has all my music on and I'm trying to get rhythmbox to play it, but every time I reboot it seems to not be able to find it.
I looked in /media/ and it was originally called 'HDD 2/', then it changed to 'HDD 2_/' and now it's 'HDD 2__/'.

How can I make sure that the partition is only in /media/HDD 2/ every time and doesn't change?

Thanks,
Paul

---

### Post by insineratehymn on 2008-04-05
When your computer is restarting, it isn't completley unmounting the hard drive.

Try this:

sudo umount /dev/HDD2

Use that when you restart your computer, with a little digging you can even find out how to automate it so it is ran an shutdown.

Also use the umount on any of the clones that may have popped up.

---

### Post by yhack on 2008-04-05
Ok I've done some googling and found out a bit about automating it, would this work?

**shutdownscript** in /etc/init.d/
```
sudo umount /dev/sda1 
sudo umount /dev/sdb5
```

```
sudo update-rc.d shutdownscript stop 22 0 6
```

Also, would it ask for a password on shutdown?

---

### Post by SOULRiDER on 2008-04-05
You can add your hard drive to /etc/fstab and it will always mount to where you want it.

Also, if the partition is ext you can label it (i think the program was called e2label) and HAL will always mount it to /media/<hard drives label>.

---

### Post by insineratehymn on 2008-04-06
I don't thing adding something to update-rc.d would require a password at shutdown.

Also, as soulrider said, adding a drive to the fstab will greatly improve the mounting/unmounting efficiency.

---

