---
title: "smb share in fstab"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Karakh on 2007-11-27
Hi guys, I am able to mount the share using the console by using:

> sudo mount -t smbfs //shared/Main /mnt -o username=admin,password=admin

but no luck in fstab, tried numerous tutorials to no avail, any suggestions? 

Thanks.

---

### Post by Dr Small on 2007-11-27
In fstab, try adding this entry:
```
//shared/Main /mnt/ smbfs auto,user, username=admin,password=admin
```

Edit, I have no knowledge in fstab, as I have never done anything in it, but that above is what I have put together from other tutorials that I have been reading. It is not guaranteed to work.
Here is one place you may be interested in reading:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Dr Small

---

### Post by Karakh on 2007-11-28
Thanks for that, I'll try it as soon as I get home from work. Not sure how I missed that link, Ive been googling this for days.

---

### Post by TeaSwigger on 2007-11-28
> **Karakh said:**
> Thanks for that, I'll try it as soon as I get home from work. Not sure how I missed that link, Ive been googling this for days.

It's easy to miss stuff, sometimes the jewels are buried in the mountains of cyberdirt. Ah well, we should be glad Samba didn't come around in the '50's. ;)

A couple others I found helpful just in case you might have missed these:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
and Stormbringer's guide to doing the samba:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by Karakh on 2007-11-28
Sorry guys, still no luck. I know its bad practice, but is there any way to just automatically run the command at startup?

---

### Post by mrtrick on 2007-11-28
Here's how I do it on our Redhat boxes at the office. Works every time. I would think it would translate to Ubuntu well. 

> //remoteserver/remoteshare /mnt/localmountpoint      smbfs username=username,password=password,workgroup=domain,uid=uid,rw 0 0

Hope that helps....

---

### Post by Karakh on 2007-11-28
I decided just to add it to rc.local. It'll probably cause me problems down the line, but hopefully by then I'll be a little more Linux savvy.

Thanks for all your help guys. It never ceases to amaze me how helpful the people on this forum are.

---

