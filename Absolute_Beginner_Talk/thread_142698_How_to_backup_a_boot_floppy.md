---
title: "How to backup a boot floppy?"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by Books on 2006-03-11
I boot into Kubuntu using a GRUB boot floppy. I need to make a backup of the floppy to another floppy in case the original is damaged. I've heard that you can't just copy over the files, so how would I go about it?

Thank you!!!

Books

---

### Post by heimo on 2006-03-11
I don't know how you created the boot disk, but you could probably just make another the same way, or if that's not possible, use dd to create copy of it.

Put the floppy to disk drive, run:
```
dd if=/dev/fd0 of=/tmp/bootdisk.img bs=512
```
I'm not sure if you need to prefix that with sudo, or if you also need count=xx parameter. Then you could put a new blank disk in and run:
```
dd if=/tmp/bootdisk.img of=/dev/fd0 bs=512
```

---

### Post by Books on 2006-03-11
Thanks, heimo! It worked.

I don't know what the "bs=512" part is, but I was able to figure out the rest of the commands.

I tried the following and it worked...

```
dd if=/dev/fd0 of=/tmp/bootdisk.img

dd if=/tmp/bootdisk.img of=/dev/fd0

```

For the sake of any newcomers more newbie than I am who will read this in the future, let me translate:

You put in your bootable GRUB floppy disk and type the following into the terminal:
```
dd if=/dev/fd0 of=/tmp/bootdisk.img
```
This means the program "dd" gets an input file from the floppy drive at "/dev/fd0" and makes an output file called *bootdisk.img* in the /tmp/ directory. (I'm guessing that's what 'if' and 'of' stand for.)

You then take out your boot GRUB floppy, put in a blank one, and type the following into the terminal:
```
dd if=/tmp/bootdisk.img of=/dev/fd0
```
This takes the newly created image file called *bootdisk.img* in the /tmp/ directory and outputs the file to the floppy at "/dev/fd0"

And to anyone more experienced than me... if I made any mistakes, please post a correction!

Thank you!

Books

---

