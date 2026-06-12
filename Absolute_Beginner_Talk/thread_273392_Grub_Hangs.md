---
title: "Grub Hangs"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by IDeus on 2006-10-08
I am trying to restore my grub. I am following the instructions at 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

What I did was ghosted the previous partition off another drive to the curent one.  When I boot from CD and open terminal as admin and enter the commands

grub
find /boot/grub/stage1

it  just sits there. Does not return or anything???What am I missing?

---

### Post by jordanmthomas on 2006-10-08
First, you need to mount your Ubuntu drive somewhere (Just use System --> Administration --> Disks (or something like that) to mount it in a folder on the Desktop (call it foo for the sake of example)
In your terminal, after mounting your drive to /home/ubuntu/foo
```
sudo su
chroot /home/ubuntu/foo
```
Then continue with the commands listed at the site.

**edit** I guess I should explain what that does...It makes your terminal see / as /home/ubuntu/foo so when grub goes to look for its stuff, it is looking in the right place.  Before the chroot, it would be looking in the directories of the LiveCD.

---

