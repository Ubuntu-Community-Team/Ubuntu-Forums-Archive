---
title: "Can I alter Windows partition"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by David Floyd on 2007-01-23
I have very recently installed 6.06 and I have a few difficulties which I'll deal with in different threads.

But!

I needed to increase the size of one of my Windows partitions today and used Partition Magic (in Windows) to do so.

Disaster!

Grub stalls with error 17 and goes no further, which means I can't get into Windows.

I think the solution is to re-install Ubuntu, which, hopefully, will recreate GRUB.

Is this the correct procedure?

And going back to the original problem; if I need to change the size of a Windows partition in the future, will I have to, or indeed, can I, deal with this within Ubuntu, because I obviously can't use Partition Magic in Windows.

Is there a solution to this problem?

Thanks for any help, 

David

(PS  the problem is with my new laptop, I'm writing this from my desk PC in Windows)

---

### Post by bionnaki on 2007-01-23
never use partition magic.

see this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3)

---

### Post by mikewhatever on 2007-01-23
How did you go about resizing the Windows partition?

---

### Post by David Floyd on 2007-01-24
> **mikewhatever said:**
> How did you go about resizing the Windows partition?

As I said - I used Partition Magic

David

---

### Post by Bachstelze on 2007-01-24
To resize the NTFS partition, I recomend to use a Live CD that has gparted in it (Ubuntu's or the official GParted Live CD). To reduce the risks of data loss, amke a defrag of the partition befire but **make backups of any valuable data before doing anything !**

---

### Post by David Floyd on 2007-01-24
> **HymnToLife said:**
> To resize the NTFS partition, I recomend to use a Live CD that has gparted in it (Ubuntu's or the official GParted Live CD). 

Thanks for that - I will see how I get on when I've got it all running again.

David

---

