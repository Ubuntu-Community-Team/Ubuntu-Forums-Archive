---
title: "Can I reassign the unused portion of a partition? (OS X)"
date: 2012-05-10
forum: Apple Hardware Users
---

### Post by nvillec on 2012-05-10
So I just partitioned the hard drive in my MacBook Pro 5,5  and successfully installed Ubuntu (12.04) alongside OS X. During the  partition process I guess Disk Utility decided to allocate the majority  of the free space (~51GB) even though I specified only 20. 



  This is really just a learning experience/experimentation and I don't  need a lot of space for Ubuntu, so when installing I chose to give it  about 20GB to play with. Now I have this remainder of the partition that  isn't being used. 



  My question is can I reassign that space to OS X without disturbing anything?


  Thanks!

---

### Post by sffvba[e0rt on 2012-05-11
*Thread moved to **Apple Users**.*


404

---

### Post by conal on 2012-05-11
I have managed this in the past by booting form an OS X install disk (10.5), and using disk utility from that to resize the os x partition and recliam the space.

Remember to back-up files if you are going to play with partitions!

Another Warning: As far as I remember the process destroyed yaboot (the power pc mac's boot loader that ubuntu uses) so I had to rewrite that to the hard drive form a live ubuntu cd. You might have a similar problem with your boot-loader, maybe someone with an intel mac can advise here?

Also I think you should turn off disk-journalling in OS X before starting the process. 

It is possible that you can use gparted from an ubuntu live cd to do this as well OS X as well - but I haven't tried that. 

Thanks

---

