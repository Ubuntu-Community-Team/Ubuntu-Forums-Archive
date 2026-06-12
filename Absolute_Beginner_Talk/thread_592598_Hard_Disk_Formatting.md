---
title: "Hard Disk Formatting"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by jackbn on 2007-10-26
I am totally new to Linux. 

I installed Ubuntu 7.10 on a clean hard drive.

I wanted to change the username and partitioning, so I tried to reformat the drive for another go at it.  I find no way to reformat within 7.10. I tried fdisk on a Windows ME floppy, but no matter what I did, the existing 7.10 is still on the drive.

Q1:
HOW TO TOTALLY REFORMAT (for Linux only)?

Q2:
HOW TO REPARTITION within 7.10?

Q3:
Is there a way to eliminate the username/password at startup?

Thanks

---

### Post by oldos2er on 2007-10-26
1. Run the installer from the Live CD, choose 'Guided--use entire disk.' The disk will be formatted.
2. You can't change partitions you're currently booted from or that are mounted. Do this while booted from the LiveCD.
3. Type 'sudo gdmsetup' in a terminal.

---

### Post by Nachtengel on 2007-10-26
There is a graphical partition editor for adjusting partitions called gparted.  Getting it is as simple as:
```
sudo apt-get install gparted
```

this will show up under the administration menu in Gusty.  If you're still using Feisty, it will show up under Accessories in the main program menu.

---

### Post by jackbn on 2007-10-26
Sorry, but I don't yet speak this dialect of Greek.

What is a Live CD? Is it the iso CD I wrote from the Ubuntu 7.10 download, or something else? And if something else, how do I get a Live CD?

And how do I get the command line screen?

Thanks

---

### Post by Frak on 2007-10-26
> **jackbn said:**
> Sorry, but I don't yet speak this dialect of Greek.

What is a Live CD? Is it the iso CD I wrote from the Ubuntu 7.10 download, or something else? And if something else, how do I get a Live CD?

And how do I get the command line screen?

Thanks
The default iso is the LiveCD iso.

And Applications->Accessories->Terminal

---

### Post by kleo skywalker on 2007-11-15
Yes, the Live CD is the CD you burnt and installed from. The easiest way to do what you want would be to install again - this time choose manual partitioning. This way, your hard disk will be formatted and you can partition it the way you want. And you can choose a new username you like. (If you have any doubts about manual partitioning, post back.)
I don't know how to get rid of the login window, and I'm not sure if that's advisable. I suggest you don't try to get rid of it unless you are absolutely sure that doing so is secure and doesn't break anything.

---

