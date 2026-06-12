---
title: "need to save folder (with 3 files) to flash drive with console"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2006-11-27
I have jacked my computer up and I need to know how I can get a folder off my desktop and transfer it to a flash drive. I only have access to the console.

---

### Post by jordanmthomas on 2006-11-27
First, you need to mount your flash drive:
```
mkdir flashdrive
sudo mount /dev/sdxy flashdrive
cd flashdrive
cp -r ~/Desktop/foldername ~/flashdrive
sudo umount /dev/sdxy

```
to find what you need to put in for xy look at the output of 
```
sudo fdisk -l
```

hopefully this helps

---

### Post by onesojourner on 2006-11-27
awesome. thanks for the help that worked perfect.

---

