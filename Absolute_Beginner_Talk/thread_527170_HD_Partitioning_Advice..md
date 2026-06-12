---
title: "HD Partitioning Advice."
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by wobwill on 2007-08-16
Hi, 

I need some basic advice on partitioning a hard disk please. 

I have an 80G hard disk on a laptop running v7.04. I only intend to run Ubuntu on this machine and if all goes well will dual boot  my desktop as well, (especially as have found ntfs-3g!) - I want to keep windows because I see no point in cutting off my own nose to spite my face. One day I may even change over to vista (shock, horror, gasp - cries of 'string that man up'). 

However. I currently have a something like the following (but can't find a disk management program that will tell me clearly)

Swap 1025Mb
Ext3 17.4Gb

I would like to turn the rest into one big partition that has the home folders for all the user accounts in it, as well as the settings. 

Pleased would someone tell me how to go about this?

Thank you in advance. 

Will.

---

### Post by Hobo Joe on 2007-08-16
Use the live CD to run GParted, then simply remove all the other partitions and make a new one out of the empty space. Unless you have Windows on the machine.

[This]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") will tell you how to go about moving your home folder to that new partition.
On the command that has 'null' and 'sparse', MAKE SURE that you put DOUBLE dashes in front, rather than just one. there is an error on the page that messes it up. Make it look like this:
```

find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/

```

---

### Post by wobwill on 2007-08-16
Hi hobo joe,

Have got to the point of trying to move Home to the new partition. After running the code in your post I get a lot of lines telling me 'permission denied' and 'no such file or directory'. When I go to the new partition the only thing I can find in there is a 'lost and found' folder I can't access. 

There is very little in home folder  at the moment. There are two folders esme (girlfriend) and william. william has recently copied album, desktop, and a .odt file in it. I have not set up email or calendar etc yet.

Do I just carry on with the advice in the guide or not?

Will.

---

### Post by wobwill on 2007-08-16
Ok,

So carried on with the advice in the guide as no response from the forum. I have followed the guide commands exactly (copy -paste) and have lost home - I now can't seem to log in at all using either my password or my girlfriends. 

Do I have reinstall or is there a way of re-finding home and placing it in the new partition?

Will.

---

