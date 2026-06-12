---
title: "Installing Ubuntu in any moment..."
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by xzin on 2007-12-11
Hi, I have just re-installed Windows XP, because it was full of junk and such, and I wanted to have fresh start. When installing windows I made my C disk to be size of 120GB, and left 200GB free for ubuntu.

Now when I check with compmgmt.msc command, it shows that I have 200GB left unreserved space. Okay, that is correct. So, I am installing ubuntu and it asks where I install it and how much space i give, can I safely just press "use biggest free space available" or something like that, im not sure because I dont have english version :)
Or will it take space from windows C disk too, and use almost whole disk?

---

### Post by Existentialist on 2007-12-11
The installer will allow you to use the 200gb of unpartitioned space to create partitions for ubuntu.  As long as you do not delete the windows partition, none of the ubuntu files will be located on the windows partition.  After you install and boot, ubuntu will probably automatically mount the windows partition so you will be able to see the files in it, but windows will not be able to see the linux partitions unless you use a FAT file system which I would not recommend.

---

### Post by logos34 on 2007-12-11
> **xzin said:**
> So, I am installing ubuntu and it asks where I install it and how much space i give, can I safely just press "use biggest free space available" or something like that, im not sure because I dont have english version :)
Or will it take space from windows C disk too, and use almost whole disk?

yep.  In english, on the 'Select a disk' screen it is the option 'use largest continuous free space' I believe.  It will show you the partition table before making any changes permanent.

---

### Post by jken146 on 2007-12-11
You can choose whatever partitioning scheme you want when you install, but if you're not really fussed you can just pick one of the guided options (I think there is one to use the remaining empty space - this creates a / partition and a swap partition).  A guide: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by stchman on 2007-12-11
> **xzin said:**
> Hi, I have just re-installed Windows XP, because it was full of junk and such, and I wanted to have fresh start. When installing windows I made my C disk to be size of 120GB, and left 200GB free for ubuntu.

Now when I check with compmgmt.msc command, it shows that I have 200GB left unreserved space. Okay, that is correct. So, I am installing ubuntu and it asks where I install it and how much space i give, can I safely just press "use biggest free space available" or something like that, im not sure because I dont have english version :)
Or will it take space from windows C disk too, and use almost whole disk?

If you do indeed have free space then select to use the largest continuous free space.  Ubuntu will make all the necessary swap partitions and such.  Since you have 200GB I would leave about 40GB of it free and create a 160GB EXT3 partition for storage.  Once you have allocated the 160GB as EXT3 the 40GB will still be the largest continuous free space on the drive.

---

