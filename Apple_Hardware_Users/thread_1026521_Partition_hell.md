---
title: "Partition hell"
date: 2008-12-31
forum: Apple Hardware Users
---

### Post by S.G. on 2008-12-31
Well, I have a Macbook Pro 3,1, and it double booted. I followed the [COLOR="Red"][guide]("https://help.ubuntu.com/community/MacBookPro1-1_1-2/Intrepid")[/COLOR] to install Intrepid (the Bootcamp simplest version). 

Then I had to install rEFIt, to synchronize. Afterwards I was able to uninstall it and everything was ok.

Then I made a big mistake. I wanted another Linux partition, so I moved the Leopard partition to the right... from Ubuntu, using Gparted. 

Of course, since the partitions were being managed from inside Leopard, now I can't boot or even see the Intrepid partition. 

I don't mind about data, but I had spent a lot of time installing lots of programs I need...

Is there any way to get to use it again?

Thanks in advance.

---

### Post by cyberdork33 on 2008-12-31
You will probably have to sync the partitions again with rEFIt. Try that first. You can make a rEFIt CD to boot from. (PS if you are planning to have multiple operating systems on your mac like that, it really would make the most sense to install rEFIt and leave it on the drive...)

Another option might be booting from the OSX Install Disc and choosing the OSX partition as the startup disc again. That should re-bless it.

---

### Post by pxwpxw on 2008-12-31
Any time you use gparted to change partition settings, it will reset the MBR partition table. That will require refit partition sync to restore the MBR before you can start ubuntu. (this applies to hardy or intrepid gparted).

So it is also a good idea to install the refit package in ubuntu, then you can run gptsync to restore the MBR table from ubuntu after using gparted.
(the next time).
```

sudo apt-get install refit
sudo gptsync /dev/sda

```

---

