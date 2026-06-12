---
title: "[SOLVED] external drive"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-11-16
I would like to back up my files on an external hard drive, but when i try to access it I get:
"hal-storage-removable-mount-all-options refused uid 1000"  What can I do to get to this drive?:confused:

---

### Post by taurus on 2007-11-16
What filesystem is that harddrive and how do you mount it?

```
sudo fdisk -l
mount
```

---

### Post by ddrichardson on 2007-11-16
The search function is your friend ;-) [here]("http://ubuntuforums.org/showthread.php?t=601210").

---

### Post by FuturePilot on 2007-11-16
Is this an NTFS drive? If so you might want to try this
```
sudo cp /etc/hal/fdi/policy/20-ntfs-config-write-policy.fdi /usr/share/hal/fdi/policy/10osvendor/
```
Then
```
sudo /etc/init.d/hal stop
sudo /etc/init.d/hal start
```

Bug is here
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/115768]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/115768")

---

### Post by skyjacker on 2007-11-16
> **ddrichardson said:**
> The search function is your friend ;-) [here]("http://ubuntuforums.org/showthread.php?t=601210").

This worked for me also. Hope someone else can use it!

```
I clicked 'storage media' in the left column in Dolphin File Manager.
I right-clicked the Disk (it showed up here in dolphin, but not in Konqueror?)
I choose 'properties' > 'mounting'
I unchecked 'mount as user'
```:(:(

---

