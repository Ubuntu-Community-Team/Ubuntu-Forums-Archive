---
title: "unable to mount ntfs"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by rkakkar on 2008-01-09
i have an external 80gb hdd which connects through usb and its an ntfs partition. however when i try to mount it, kubuntu throws the following error:

```
hal-storage-removable-mount-all-options refused uid 1000
```

what does this mean?

---

### Post by Pevichaey5 on 2008-01-09
FOSS may be required to mount NTFS partitions

i am just going to find out if that is true

---

### Post by codesplice on 2008-01-09
Try mounting the disk using the ntfs-3g package.

ex:
```

$ sudo ntfs-3g /dev/disk /mnt/point
```

I guess you'll also need to install that package if you don't have it, too :p

---

### Post by FuturePilot on 2008-01-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/115768](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/115768) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				First install ntfs-config
```
sudo apt-get install ntfs-config
```
Then
```
sudo cp /etc/hal/fdi/policy/20-ntfs-config-write-policy.fdi /usr/share/hal/fdi/policy/10osvendor/
```
```
sudo /etc/init.d/hal stop
sudo /etc/init.d/hal start
```

---

### Post by rkakkar on 2008-01-11
> **FuturePilot said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/115768](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/115768) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				First install ntfs-config
```
sudo apt-get install ntfs-config
```
Then
```
sudo cp /etc/hal/fdi/policy/20-ntfs-config-write-policy.fdi /usr/share/hal/fdi/policy/10osvendor/
```
```
sudo /etc/init.d/hal stop
sudo /etc/init.d/hal start
```

$ sudo cp /etc/hal/fdi/policy/20-ntfs-config-write-policy.fdi /usr/share/hal/fdi/policy/10osvendor/
cp: cannot stat `/etc/hal/fdi/policy/20-ntfs-config-write-policy.fdi': No such file or directory

---

### Post by FuturePilot on 2008-01-11
> **rkakkar said:**
> $ sudo cp /etc/hal/fdi/policy/20-ntfs-config-write-policy.fdi /usr/share/hal/fdi/policy/10osvendor/
cp: cannot stat `/etc/hal/fdi/policy/20-ntfs-config-write-policy.fdi': No such file or directory

Try running the ntfs-config tool first. It must create that file when it's run.

---

### Post by rkakkar on 2008-01-11
> **FuturePilot said:**
> Try running the ntfs-config tool first. It must create that file when it's run.

hey it worked!! thanks a lot! :)

---

