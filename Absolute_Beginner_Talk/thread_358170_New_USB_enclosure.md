---
title: "New USB enclosure"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2007-02-10
Hi !all, I have recently bought a USB /IDE HDD enclosure. I have the drive jumpered to Master. It is not being picked up by my Ubuntu OS. It's a new IDE 80GB drive within the enclosure. I wish to use this as storage and backup using rsync (if I can get my head around it). I may be missing some essential to do's to get it up and running.So if you can help I would appreciate it.
Thanks and regards:)

---

### Post by neilp85 on 2007-02-10
After plugging it in use dmesg to try and figure out where it was mounted. Should be something like /dev/sr0. After that you can mount the device using ```
sudo mount /dev/sr0 <some path>
```

---

### Post by Sbarton on 2007-02-11
Thanks neilp85 for your reply. Due to some probs with another PC I have not got down to doing this. Hopefully tomorrow.
regards

---

