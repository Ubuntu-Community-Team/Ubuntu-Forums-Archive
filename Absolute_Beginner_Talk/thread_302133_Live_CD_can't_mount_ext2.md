---
title: "Live CD can't mount ext2"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by maybeme on 2006-11-18
Hi,

I did something very stupid:
I mistyped me when editing visudo :o
Now I don't have the right to do something as su, and I don't have a root account. So I have to edit visudo/sudousers via a live CD. I tried with the 6.06 CD, but I get this error when I try to mount the drive:

error: device /dev/hda1 is not removable

error: could not execute pmount

What should I do? I only found smoe tutorials/sripts for windows partitions.

---

### Post by huygens on 2006-11-18
Hi Maybeme,

Once you have booted on the Live CD, open a console/terminal (Applications->Accessories->Terminal). Then type the following commands:
```
sudo mkdir /mnt/foo
sudo mount /dev/hda1 /mnt/foo
```This should autodetect your partition type and mount it. Then if you had only one partition named / on your normal Ubuntu installation, you just have to do the following (N.B. you cannot use visudo from the Live CD, it will not modify - I expect - the sudo configuration of your installation):
```
cd /mnt/foo/etc
sudo cp sudoers sudoers.rescue1
sudo chmod +w sudoers
sudo vi sudoers
```If you don't know vi, you can use nano instead, replace vi by nano in the last line above.
Once you have corrected the file, you should remove the write permission. Just type this:```
sudo chmod -w sudoers
```That's should do it,
Huygens

---

### Post by maybeme on 2006-11-18
Thanks alot!

---

### Post by huygens on 2006-11-19
> **maybeme said:**
> Thanks alot!
you're most welcome :-) but did it work? Have you your sudo configuration corrected?
Huygens

---

