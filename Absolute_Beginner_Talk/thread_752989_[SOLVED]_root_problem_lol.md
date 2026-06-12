---
title: "[SOLVED] root problem lol"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by xaocan on 2008-04-12
I'm using Ubuntu for a while now but I have a damn stupid problem. Today I was bored and I i tried to change my user's privileges and i removed the administrate option of my user :lolflag:.

How do i return it ^^. Don't tell me reinstall and these kind of things I know them myself.

---

### Post by wormser on 2008-04-12
Boot into recovery mode and...

```
adduser username admin
```

---

### Post by sisco311 on 2008-04-12
Reboot your computer and select Recovery Mode from the Grub menu.
When the computer first starts up, you have a few seconds to push esc to go into GRUB.

When the command prompt appears, issue the command:
```
usermod -a -G admin ***username***
```
to add your user to the admin group and
```
reboot
```
to  reboot.

---

### Post by xaocan on 2008-04-12
THX everybody! I'm admin again :guitar:

---

### Post by kshane on 2008-04-12
> **sisco311 said:**
> 

  ...
__________________
sex the unix way: unzip; strip; touch; finger; mount; fsck; more; yes; umount; sleep; exit 0



I just LOVE your tag line!!!

Kevin

---

