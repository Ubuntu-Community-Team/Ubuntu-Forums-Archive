---
title: "I cannot change my permissions of my external"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by ThinkingAboutWater201 on 2007-10-02
Any help????

---

### Post by jw5801 on 2007-10-02
What happens when you try?

---

### Post by ThinkingAboutWater201 on 2007-10-02
> **jw5801 said:**
> What happens when you try?

It wont let me it greys everything out

---

### Post by jw5801 on 2007-10-02
So... you've opened Nautilus, right clicked on a file and all the options were greyed out?

Please provide a touch more information. What format is the external drive in? Has it worked previously, but isn't any more? What exactly are you trying to do that requires you to change the permissions on it?
Post the outputs of: ```
ls -l /media/
mount | grep /media
```I am of course assuming that you have let Gnome automount the drive since you haven't told me otherwise.

---

### Post by ThinkingAboutWater201 on 2007-10-02
> **jw5801 said:**
> So... you've opened Nautilus, right clicked on a file and all the options were greyed out?

Please provide a touch more information. What format is the external drive in? Has it worked previously, but isn't any more? What exactly are you trying to do that requires you to change the permissions on it?
Post the outputs of: ```
ls -l /media/
mount | grep /media
```I am of course assuming that you have let Gnome automount the drive since you haven't told me otherwise.


It is a LaCie harddrive Its probalay NTFS. And now Sudo doesnt work! We are trying to make it shared because we have like gb's of music and we want to put it on that external and then share it on the ubuntu computer.
And it still works
Is that enough info?

---

### Post by jw5801 on 2007-10-02
If it's NTFS you cannot write to the drive without using different drivers (it's a proprietry Microsoft format) you should be able to read from it though. sudo won't work because the drive will be mounted as read only. If you want full read/write support for NTFS then you'll need to install these drivers:```
sudo apt-get install ntfs-3g
```Then mount the drive using the ntfs-3g driver, first unmount it:```
sudo umount /*wherever_its_mounted*
```
You'll need to replace the italics with whatever the mountpoint of the drive is, if you're unsure then post the output of the two diagnostic commands I gave you in my last post and I'll tell you. Then you'll need to mount it again with the right driver:```
sudo mkdir /media/ntfs-3g #you need to create a directory to mount to first
sudo mount -t ntfs-3g /dev/*device-name* /media/ntfs-3g
```
Once again you'll need to replace the italics with whatever the device is called (it will be sda1 or sdb1 or hda1 or something along those lines). If you're unsure where to find that, post the output of the commands in my previous post and I'll tell you. Make sure you run them *before you unmount the drive* though, otherwise I won't be able to tell anything useful from them.

---

### Post by ThinkingAboutWater201 on 2007-10-02
> **jw5801 said:**
> If it's NTFS you cannot write to the drive without using different drivers (it's a proprietry Microsoft format) you should be able to read from it though. sudo won't work because the drive will be mounted as read only. If you want full read/write support for NTFS then you'll need to install these drivers:```
sudo apt-get install ntfs-3g
```Then mount the drive using the ntfs-3g driver, first unmount it:```
sudo umount /*wherever_its_mounted*
```
You'll need to replace the italics with whatever the mountpoint of the drive is, if you're unsure then post the output of the two diagnostic commands I gave you in my last post and I'll tell you. Then you'll need to mount it again with the right driver:```
sudo mkdir /media/ntfs-3g #you need to create a directory to mount to first
sudo mount -t ntfs-3g /dev/*device-name* /media/ntfs-3g
```
Once again you'll need to replace the italics with whatever the device is called (it will be sda1 or sdb1 or hda1 or something along those lines). If you're unsure where to find that, post the output of the commands in my previous post and I'll tell you. Make sure you run them *before you unmount the drive* though, otherwise I won't be able to tell anything useful from them.

He says he had the ntfs-3g Its is called NTFS Configuation Tool because he has it
I told you we don't have sudo it says "sudo: /etc/sudoers/ is owned by uid 1000, should be 0"
And it wont let me umount because we are not a superuser and i think root it and since we dont have sudo we cant get in to root because i know the command to login as root

---

### Post by ThinkingAboutWater201 on 2007-10-02
It looks lke were either gonna find other ways or just gonna totally delete it and maybe reinstall!

---

### Post by ThinkingAboutWater201 on 2007-10-02
Unless you have a better idea!

---

### Post by jw5801 on 2007-10-02
If you posted the output of the commands that I gave in my second post it would be incredibly helpful. ```
ls -l media
mount | grep /media
```
And when you said sudo wasn't working I assumed it was related to this problem and you were telling me that sudo didn't work when trying to access the drive, not that sudo itself was broken. To help me diagnose this problem can you please post (copy and paste) the output of ```
ls -l /etc | grep sudoers
```

---

### Post by jw5801 on 2007-10-02
> **ThinkingAboutWater201 said:**
> Unless you have a better idea!

We should be able to fix it without resorting to a complete reinstall. We'll just have to fix sudo to start with. The drive isn't a problem, but sudoers being owned by something else is extremely odd.

---

### Post by ThinkingAboutWater201 on 2007-10-02
> **jw5801 said:**
> We should be able to fix it without resorting to a complete reinstall. We'll just have to fix sudo to start with. The drive isn't a problem, but sudoers being owned by something else is extremely odd.

okay please stay with me

---

### Post by jw5801 on 2007-10-02
Can you copy and paste the output of this command:```
ls -l /etc | grep sudoers
``` and post it here?

---

### Post by ThinkingAboutWater201 on 2007-10-02
i will

---

### Post by psusi on 2007-10-02
Looks like you totally screwed your filesystem permissions with a chown -R command.  You need to reinstall.

---

### Post by ThinkingAboutWater201 on 2007-10-02
> **jw5801 said:**
> ```
ls -l /etc | grep sudoers
```

It didnt work it just gave me techinal crap then we tried to sudo and it got the same problem!

Ill try the other one now

---

### Post by ThinkingAboutWater201 on 2007-10-02
> **jw5801 said:**
>  ```
ls -l media
mount | grep /media
```


that didnt work eiter

---

### Post by ThinkingAboutWater201 on 2007-10-02
> **ThinkingAboutWater201 said:**
> that didnt work eiter

Aparetnly were going to have to re-install

sorry

---

### Post by jw5801 on 2007-10-02
Those commands weren't meant to fix the problem, they were *supposed* to output "technical crap" which you could post here so that I could interperet it. Don't worry about the mount or media commands, just give me the output of the first one you tried.It should give you something like this> -r--r-----  1 root   root       403 2007-06-22 01:24 sudoersExcept yours probably won't say root, it'll say your username.

To fix that you'll need to boot into a failsafe terminal (I think that gives you root?) or else boot off a LiveCD to change the owner of sudoers. Or you could take the easy way out and reinstall.

---

### Post by ThinkingAboutWater201 on 2007-10-02
> **jw5801 said:**
> Those commands weren't meant to fix the problem, they were *supposed* to output "technical crap" which you could post here so that I could interperet it. Don't worry about the mount or media commands, just give me the output of the first one you tried.It should give you something like thisExcept yours probably won't say root, it'll say your username.

To fix that you'll need to boot into a failsafe terminal (I think that gives you root?) or else boot off a LiveCD to change the owner of sudoers. Or you could take the easy way out and reinstall.

um okay he's looking at something  come back in about say so... 10 minutes?

---

### Post by jw5801 on 2007-10-03
That's a long 10 minutes! Well if you haven't reinstalled yet then you should be able to fix the issue by rebooting, and when you get to the grub menu (you may have to press escape to see it) selecting the "recovery console" option. Then you should wind up at a root command line where you want to type (write this down, or you'll need another computer to see it while you're doing it) ```
chown root:root /etc/sudoers
```Then you want to type```
ls -l /etc/ | grep sudoers
``` which should show you a line like this:
```
-r--r-----  1 root   root       403 2007-06-22 01:24 sudoers
```
Then you'll want to reboot to get out of recovery mode so type ```
shutdown -r now
```to reboot into the normal mode.

---

### Post by psusi on 2007-10-04
There are likely other files that have screwed up permissions that will cause problems elsewhere.  Best just to reinstall.

---

