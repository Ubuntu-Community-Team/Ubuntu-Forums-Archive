---
title: "Guidelines to set up simple home server"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by egaertner on 2007-10-24
I have an old 733Mhz P3 // 128mb ram box that I'm turning into a home server.  For the time being, my interests include local file sharing, lamp webserver, and ftp access into the webserver goods.  

I have a 20GB drive and a 300GB drive.  My current design plan is to have 19GB on the first drive be the main root install, ext3.  Following that up with a 1GB swap.  The second drive I was going to partition as a whole, as ext3.  I'm not too familiar with design practices in linux or their respective partition types, if anything better can be suggested for my small needs.

Once I have done that, I'm undecided what I should mount to the 300GB.  From my understanding of the architecture, mounting /home to the 300GB seems like a logical choice.  I also understand that by default, all web hosting goes under /var/www as well. 

Would it be better to mount /var on the 300GB as well, and split up the partition space?  Or rather, should I change the apache config to point towards a www folder I can just drop in home somewhere.

Finally, any common tricks or tips to getting windows boxes to see and mount the linux partition as a share?

I realize a lot of this is probably personal preference, but if you had to choose...

Thanks

---

### Post by p_quarles on 2007-10-27
Unless you're going to be hosting amazon.com or YouTube, you will never need more than a few gigs for an Apache server's document root directory. The advantage of giving /var its own partition is that you could hypothetically resize it if your data ever outgrew it. 

Setting up a Windows share on a Linux server is pretty easy. You will need to install Samba (which can also be used as a printserver, if you're interested). There are many tutorials out there, but this is a decent one to start with:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

There are also numerous guides to Samba and other Linux server software on this site:
[http://www.howtoforge.com/](http://www.howtoforge.com/)

Hope this helps.

---

