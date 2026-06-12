---
title: "reinstall win xp by keeping ubuntu"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by aliov_85 on 2007-08-31
Hello everybody,

I've a problem with my win xp and I want to reinstall it with keeping my ubuntu installed with it's configuration. A friend made a mistake and the grub doesn't work anymore. I'm sure that ubuntu (feisty) is kept.

So I've to resolve the grub problem  and eventually reinstall it.

So I would like to ask you guys if someone can give me any advice to proceed.

thanks in advance

Ali

---

### Post by jombeewoof on 2007-08-31
you're going to have to reinstall grub. there is nothing that I know of that will make windows not overwrite the boot sector. 
after you are finished installing windows it becomes a little tricky

assuming you have 2 hard drives /dev/sda and /dev/sdb
assuming windows is on /dev/sda1 and ubuntu is on /dev/sdb1
boot back into the live cd and get to a command prompt
```

cd /
sudo mkdir /ubu
sudo mount /dev/sdb1 /ubu
chroot /ubu
cd /boot/grub
grub install /dev/sda

```
reboot
grub should be back and should still load to windows if you didn't change where you had windows installed.

---

### Post by ThrobbingBrain66 on 2007-08-31
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

