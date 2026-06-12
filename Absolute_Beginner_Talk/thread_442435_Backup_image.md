---
title: "Backup image"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by cabrando on 2007-05-13
I just installed/configured Feisty on my laptop.

I have all the hardware working properly now and was wondering if I can backup my current system to a disk image or any other way so if something happened I can restore my system with all the current settings.

Thanks

---

### Post by Campingman on 2007-05-13
There is a program called partimage which will do what you need.  I successfully imaged and restored a version of Edgy with it.  Partimage has to be used in conjunction with a live cd as the partition to be imaged cannot be mounted at the time.  Here are some links to backing up with partimage
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Have a look and see if this is what you require
The program is in the synaptic package manager

Hope this helps

---

### Post by cotcot on 2007-05-13
Partimage does not work in 64 bit.  In 32 bit it works nice.
In 64 bit you can backup with [this]("http://ubuntuforums.org/showthread.php?t=81311") howto. It works. I have tested it a couple of times (restore included).

---

