---
title: "Different distros +Ubuntu"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by askaggs on 2006-10-14
Hello.
I have Ubunto running on a seperate HD with XP on the "C" drive.I have "musix=linix" and "Dyne-bolic" on CD but would like to install one or both of them. Can I do that like I did with Kubuntu with no partitioning? Idon't want to jump through a bunch of hoops here. I like Ubuntu an have it all set up, but as a musician the other distros are better for me in many ways.
Thanks in advance for any help.
askaggs

---

### Post by taurus on 2006-10-14
You must have an empty partition before you can install another OS.  You can't just install one on top of another and have both working unless you use VMWare or qemu, an emulator...

---

### Post by doobit on 2006-10-14
> **askaggs said:**
> Hello.
I have Ubunto running on a seperate HD with XP on the "C" drive.I have "musix=linix" and "Dyne-bolic" on CD but would like to install one or both of them. Can I do that like I did with Kubuntu with no partitioning? Idon't want to jump through a bunch of hoops here. I like Ubuntu an have it all set up, but as a musician the other distros are better for me in many ways.
Thanks in advance for any help.
askaggs

I don't know about musix, but dyne:bolic doesn't need it's own partition. As long as you have a Linux formatted partition, you can just drag the /dyne folder there from the live CD and then open the configuration button and click the nest button, and install the nest in the /dyne folder to make your settngs persistant. Finally, update grub to make a listing for dyne:bolic. There is a text file on the disk that tells you what info to put there. You just need to make sure grub is pointing to the correct partition.

---

### Post by Kateikyoushi on 2006-10-14
It depends on your current partitioning whether you have to make new partitions or not.
Most likely you have to but the following command will make it clear, please post back it's output.

```
sudo fdisk -l
```

---

### Post by doobit on 2006-10-14
> **taurus said:**
> You must have an empty partition before you can install another OS.  You can't just install one on top of another and have both working unless you use VMWare or qemu, an emulator...

dyne:bolic works a little differently :)

---

