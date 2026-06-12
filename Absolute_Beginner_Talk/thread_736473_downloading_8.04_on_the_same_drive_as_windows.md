---
title: "downloading 8.04 on the same drive as windows"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by leviticusforjesus on 2008-03-26
will this conflict? can i move the installation to another drive once its complete? is 3.2 gb large enough for 8.04?

---

### Post by SunnyRabbiera on 2008-03-26
It shouldnt, but you may need more space if you want more productivity.
If you have a small hard drive you may want to get a larger one.

---

### Post by stefangr1 on 2008-03-26
You can install it on the same drive as windows, as long as it is on a separate partition. At startup, grub gives you the possibility to choose what you want to start.

You can move your install to another disk drive, but then you will have to reinstall grub, since it won't know where to look for it otherwise.

I think 3.2 GB is just enough for an install, but it's to limited for normal usage.

---

### Post by leviticusforjesus on 2008-03-26
im putting it on an 80gb drive but will it function with windows?
i dont have a partition.
and i mean can i move the installation to the smaller drive or will it be embedded?

---

### Post by SunnyRabbiera on 2008-03-26
yes you can put both systems on the same drive, this is called a dual boot around these parts.
as for installing ubuntu on a small drive you can but the space you say you have might not be enough if you want the full experience.
you can look up guides on these forums on dual boots, just keep in mind that ubuntu hardy is beta and is not recommended for everyday use at this point.
In this case i suggest you keep to the system you have now until hardy is out of beta that way you can have a stable system, unless you are a tester there is no reason to install hardy.

---

### Post by stefangr1 on 2008-03-26
It is not possible to install multiple operating systems on one partition. In fact, your main partition (which is called root) needs to be formatted in the filesystem that is used by Ubuntu.

If you have downloaded the Ubuntu live cd, you can just put in in your computer and try it out, when you then have your second hdd available within some time, you can install it on that one.

---

### Post by waspbr on 2008-03-26
same drive but different partition , you can use the live Cd to resize your current partition, setting about 10 GB for your ubuntu install.

---

### Post by iSplicer on 2008-03-26
You need to resize your Windows partition, then install ubuntu on the unpartitioned space. This will automagically install GRUB, allowing you to choose between windows or ubuntu when you start your PC

---

