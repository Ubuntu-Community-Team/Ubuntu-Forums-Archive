---
title: "partitions"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-02-06
I have ubuntu and suse installed, I want to purge the suse, I figure this means having to delete the suse partition, then resize the ubuntu partition, then reinstall grub.

the question is how?

---

### Post by Pogeymanz on 2008-02-06
You don't have to reinstall GRUB.

If Ubuntu is the first OS on the hard disk: I think grub only looks at where the OS starts on the hard disk.So, in Ubuntu, in a terminal type
```
sudo gedit /boot/grub/menu.lst
```
and just delete the suse entry.

Then reboot with a LiveCD. Just delete suse and resize Ubuntu from the LiveCD




If Ubuntu is the second OS on the hard disk: first, in Ubuntu, figure out what the "/" partition is for Ubuntu. (sda1, for example). Then, in a terminal type
```
sudo gedit /boot/grub/menu.lst
```

And find the entry for Ubuntu. It will have a line with "UUID" and then a bunch of numbers. Delete that value, including the "UUID" and replace it with the name of the partition found above. Also, you can delete the whole suse entry in this file, as it soon wont exist. Close the file.

Now, you'll probably want to reboot with a LiveCD that has gparted on it.

Now, edit your partitions with gparted. QED.

---

### Post by LarryJ2 on 2008-02-06
I'd install qtparted

> sudo apt-get install qtparted

That will allow you to delete the suse partition  assuming you know which is the suse partition  (like is it /dev/hda3   or  /dev/sda6 or some similar).

Rather than resize, may be you would like to reformat the old suse partition with ext3 and use it as a back up partition or something similar.  Resize is possible but probably you'll have to move the current contents of your ubuntu partition to a temporary partition,  resize the current ubuntu  partition, and then move every thing back.     It's possible, and instructive,  but fraught with "my pc won't boot" pit falls.

---

### Post by Pogeymanz on 2008-02-06
I think you only need to move stuff around if you don't have a LiveCD.

I have personally done this kind of thing 100 times on my laptop. If you could just post a description of your hard drive partitions, I can give step-by-step instructions for what to do, including possible things that can go wrong. My above post is still what you would be doing, but it could be more detailed if I knew your precise set-up.

a description of your hard drive would be something like this:
sda1   Ubuntu "/"
sda2   Ubuntu "/home"
sda3   SUSE  "/"
sda4   swap


and then I would ask if you were increasing your root "/" partition or your "/home" partition.

---

