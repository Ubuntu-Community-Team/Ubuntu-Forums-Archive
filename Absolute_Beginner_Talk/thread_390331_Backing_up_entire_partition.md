---
title: "Backing up entire partition"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2007-03-21
Hey!
I want to backup an entire partition on 2 dvd's (7.5 gigs) and then
a) format entire HD
b) install windows
c) create 2 extra partitions using partition magic (1 for ubuntu and 1 for data to be used between both OS's)
d) use the backup i created and put it into the linux partition
e) enable a dual-boot system

What's the best method to do this backup and then placing the backup on a new partition?

Thanks :)

---

### Post by Ptero-4 on 2007-03-21
you can type:
```
dd if=/dev/partition of=~/image.iso
```
in the terminal (/dev/partition is the device name of your linux partition and image.iso is the name of the output iso image), and then use nautilus to burn it in a double layer DVD.

---

### Post by tonycm1 on 2007-03-21
Awesome Tip!! 

One more question though.... after i'm done doing everything i need to do, how would you suggest I re-copy this image to a fresh partition afterwards? Is there a specific procedure or just a simple copy would do it?

---

### Post by Ptero-4 on 2007-03-21
type:
```
sudo dd if=/dev/cdrom of=/dev/partition
```
where /dev/partition is where your image (which I assume you burned to a DVD) will be dumped into and /dev/cdrom is your DVD burner, you`ll need root acccess hence the sudo in front and also you need to make sure that the destination partition isnt mounted.

---

### Post by mikawber on 2007-03-24
I tried to do this and save it to my external hard drive and I got an error saying file size exceeded. It got to 4GB and stopped. My entire partition is 20GB and my hard drive has over 200GB free. Any idea why?

---

