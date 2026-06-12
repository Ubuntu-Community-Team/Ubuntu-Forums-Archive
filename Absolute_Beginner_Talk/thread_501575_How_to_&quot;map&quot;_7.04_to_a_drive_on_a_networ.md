---
title: "How to &quot;map&quot; 7.04 to a drive on a networked Windows XP machine?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by TheTaylorEffect on 2007-07-15
Hello All,

I'm still relativley new to Linux, but I have a great background in general networking. I'm not sure if the term "Drive Mapping" has any meaning in the world of Linux... but for those of you that aren't familiar with the terminology, a mapped drive is a pathway to a drive on a network that makes it appear as a local path for local applications.

We've got a fairly large Windows sever on our network (750gb drive), and my roommates and I compile all of our collectively downloaded Torrent booty there.

We do this by simply 'maping' our local machine to the drive on the server. Than we use the 'mapped' path in the local bit torrent client as the download folder (so the downloads would get dumped directly into the hard drive on the the headless server machine, rather then storing them on my local hard drive).

I was wondering if there is anyway to "map" a drive on a Windows computer into Fiesty, for the same purpose.

Its important that this "mapped" pathway reconnects automatically with every reboot. Is this possible?

Thanks in advance!

-MT

---

### Post by Jamie Jackson on 2007-07-15
Here are some notes to myself on the matter. Everything beginning with "my" is a variable you need to replace.
```

#mount windows
sudo apt-get install smbfs
sudo mkdir -p /media/myMountPoint
# temporarily
sudo smbmount //myRemoteHost/myRemoteHostShareName /media/myMountPoint -o username=myRemoteHostUsername,workgroup=myWorkGroupName,rw,fmask=775,uid=myLocalUsername

```
To mount permanently, go [here]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html").

---

### Post by TheTaylorEffect on 2007-07-15
Thanks Jamie!

It worked like a charm... as for mounting it perminantely, I opted to just add the command to a luncher, since the map was to a laptop (which isn't always connected to the same network).

But, your code worked like a charm!

Thanks again,

Michael

---

