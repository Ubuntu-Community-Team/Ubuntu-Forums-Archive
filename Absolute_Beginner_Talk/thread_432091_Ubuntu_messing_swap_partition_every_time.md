---
title: "Ubuntu messing swap partition every time"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2007-05-03
I'm getting really tired of this...
Every time ubuntu 6.1 is loosing my swap partition, for some (god knows why) reason it is changing that UUID on etc/fstab and is not being able of restoring it I need to manually do a mkswap, configure fstab, and swapon on every boot. 
Any way of fixing it? 
Is it possible of getting rid of this UUID stuff, I really enjoyed linux better when it was only the plain fstab configuration.

Regards

---

### Post by ctroberts on 2007-05-03
Check this out "After running mkswap, swap space is discarded, system fails to hibernate (invalid swap signature)"

[https://launchpad.net/ubuntu/+bug/66637](https://launchpad.net/ubuntu/+bug/66637)

---

### Post by steve.horsley on 2007-05-03
The installer helpfully puts a line above the fstab entry telling you which /dev it is referring to. You can just edit the file and replace that pesky UUID with the original /dev/... and everything works fine. I do this on every install I do.

---

### Post by kmoffat on 2007-05-06
Is there no drawback to this simple fix?

---

### Post by Lucifiel on 2007-05-06
> **kmoffat said:**
> Is there no drawback to this simple fix?

No, there isn't.

I had a problem of converting my ntfs partition to fat32 and then ext3 and it wouldn't show up in Ubuntu. Fixing the fstab entry worked.

If you're afraid of messing up fstab, back it up then.

Edit: The worst a messed up fstab entry can do, is cause the device to not be mounted.

---

