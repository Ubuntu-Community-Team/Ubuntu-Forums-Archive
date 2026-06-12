---
title: "Getting to the Root of it all"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-05-08
This problem has been confusing me.  Every time I try to install for a dual boot I keep getting an error message which says something along the lines of no root directory, or something like that.

Could somebody tell me what type of partition I need to install a Linux OS?

Cheers

---

### Post by Skrynesaver on 2007-05-08
You need two new partitions on your drive at a minimum, one ext3 and one swap

---

### Post by the lemming on 2007-05-08
Using G-parted I have created a ext3 partition and a swap partition before installing.

However I keep getting an error message saying that I have not defined a root partition.

Where am I going wrong?

---

### Post by Skrynesaver on 2007-05-08
When you set up your partitions, do you assign the ext3 partition to the / mount point?

---

### Post by davahmet on 2007-05-08
That's it exactly.  As a minimum, you must have a root filesystem designated with the mount point "/".

Think of it as a baseline starting point that every program will use as a reference whe  it tries to map locations on your drive.  Without a "/", the bootup manager has no way of know where to point for accessing the start-up programs.

---

### Post by the lemming on 2007-05-09
> **davahmet said:**
> That's it exactly.  As a minimum, you must have a root filesystem designated with the mount point "/".

Think of it as a baseline starting point that every program will use as a reference whe  it tries to map locations on your drive.  Without a "/", the bootup manager has no way of know where to point for accessing the start-up programs.



This may seem like an extreemly novice question but I have apsolutely no idea what the symbol "/" is, does or what to do with it.

Unfortunately I come from a windows environent where I simply pressed mouse buttons to get stuff to happen.  I've never even got Basic programming when I was a kid.  With this in mind could somebody post an idiot's version of what it it that I should be doing or trying to achieve?

I'm sorry to sound so ignorent of Linux speak but I hope people appreciate that all this is indeed a very slow and difficult uphill struggle.

Cheers

---

### Post by Shazaam on 2007-05-09
Think of "/" as "C:" in windows. Not quite correct and crude but it might help.

---

