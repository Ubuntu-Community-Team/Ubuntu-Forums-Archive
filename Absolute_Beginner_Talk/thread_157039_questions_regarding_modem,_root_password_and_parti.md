---
title: "questions regarding modem, root password and partitions"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-04-08
Hi,
I recently installed ubuntu on my notebook Toshiba Satellite A25-S207
It detected most of the hardware, but is having problems detecting modem.
I have two questions:
1. How do I make my modem work?
2. I used the default setting on partitions during the installation, now I have two partitions, Partition 1 (35 GiB) and Swap Partitions (1.36 GiB). I want to split Partition 1, so I can have a seperate partition for storing data. How can I do this since Create and Delete options are disabled.

Any help on these issues will be greately appreciated, thanks in advance.
Rameez.

---

### Post by K.Mandla on 2006-04-08
You might try gparted or qtparted, which are graphical partition editors. I prefer gparted myself. Both can be installed with the Synaptic Package Manager, or through the terminal.

---

### Post by rameez on 2006-04-08
will it allow me to modify the partition since it is the system partition?

---

### Post by towsonu2003 on 2006-04-14
1. check out second link in my signature
2. I believe it will it allow you to modify the partition. Backup your files, than launch the partition utility (whichever you want) and try out. It is not supposed to change anything unless you hit a button like save or write (or similar). Basically, you'll shrink partition 1 and add a new partition to its end.

---

### Post by mrchrisblau on 2006-04-14
Your subject mentioned something about root... what, if any, is your question about that?

---

### Post by rameez on 2006-04-15
[QUOTE=mrchrisblau]Your subject mentioned something about root... what, if any, is your question about that?[/QUOTE]
Oh, I had a question about root use in ubuntu but found out the answer thats why I edited the message.

---

