---
title: "HDD external"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by ~L~ on 2008-04-15
i have an external HDD which I use with IDE to USB cable . I installed the ubuntu distro and now it tells me cannot mount it. I want to use it because I have all my music etc inside, Thanks
It is formatted ntfs

---

### Post by Trail on 2008-04-15
Any more details?

Did you plug it in, and an error message popped up automatically saying it couldn't be mounted? If not, how did you try to mount it? What is the error message?

---

### Post by ~L~ on 2008-04-15
when i turn on the drive it pops up and says unable to mount the volume.
[http://i42.photobucket.com/albums/e310/Morgoth_Bauglir/Screenshot-1.png](http://i42.photobucket.com/albums/e310/Morgoth_Bauglir/Screenshot-1.png)
please help me for I have all my backup on that drive : >

---

### Post by Tatty on 2008-04-15
this problem occurs if you have been using your external drive in windows and you have unplugged the drive without unmounting it properly.  

You need to plug it back in to windows, then unmount it by clicking the hardware icon in the taskbar, and selecting the drive to unmount.  Alternatively you can force the drive to mount in ubuntu- although the safety of the data cant be guarenteed.

---

### Post by ~L~ on 2008-04-15
i am not using windows at all :o
just ubuntu:(

---

### Post by Sidewinder1 on 2008-04-15
It may be a permissions issue. Try this:
 ```
Sudo chown -R yourusername:yourusername /media/disk
```

Replace  "yourusername" with your actual username, Enter your password when it asks and you should be good to go....HTH

---

### Post by ~L~ on 2008-04-15
cannot access 'disk' no such file or directory

---

### Post by ~L~ on 2008-04-15
bump please i have all my backup data there ; <

---

### Post by RiceMonster on 2008-04-15
> **~L~ said:**
> cannot access 'disk' no such file or directory

Change "disk" with the name of your external hd.

---

### Post by Sidewinder1 on 2008-04-15
Rice's advice is correct and to be used with the "sudo chown" command above. Perhaps you can tell what it's named in Nautilus

---

