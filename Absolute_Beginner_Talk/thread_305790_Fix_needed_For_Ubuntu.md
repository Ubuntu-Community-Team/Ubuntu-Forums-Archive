---
title: "Fix needed For Ubuntu"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-11-23
I've been browsing forums for long time. I found problems that need to be fixed to make Ubuntu "perfect". This is my personal opinions

1) X server issues, especially with nvidia drivers

2) Ubuntu fails to boot and hang at loading screen if a sata hhd containing ubuntu is connected to a sata pci card. This is a problem for motherboards that do not have onboard sata ports but a sata pci card. I did not experience such issue with suse linux or susindows i may say.

3) Cannot access ubuntu files on hardrive from life cd. This would make recovery easy.

---

### Post by ironfistchamp on 2006-11-24
3) Do you mean you can't see the files on your Ubuntu Installation when using the Live CD? If so then you can do this. Open a terminal and type

```

sudo mkdir /media/ubuntuhdd
sudo mount /dev/hda1 /media/ubuntuhdd -t reiserfs -o

```

This will mount the first partition on the first PATA hard drive. This assumes that it is reiserfs filesystem but it may be ext3 or ext2. 

I think this is correct. I am not at a Lin machine so I can't check this. 

Hope this helps

Ironfistchamp

---

### Post by kiyometane on 2006-11-25
thaNKS

---

