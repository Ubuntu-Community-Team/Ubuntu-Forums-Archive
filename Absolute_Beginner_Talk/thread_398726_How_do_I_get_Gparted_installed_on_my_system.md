---
title: "How do I get Gparted installed on my system?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2007-04-01
How do I install gparted the GNOME Partition Editor on my system?
I found it in the Synaptic Package Manager but when I try to install it I get
errors. Is the SourceForge site down? Or is the file no longer available?
I did a search on yahoo for gparted. I found a file to download (I think it was on
the sourceforge site).
When trying to install it I get lib's not found errors, directory not found errors.
If you want me to post the configure.log I will but it's big.
There has to be an easier way. I have downloaded many packages with the
package manager without problems until now.
Any suggestions???

---

### Post by bulldog on 2007-04-01
Download the GParted live cd and burn it to a cd-r.
Boot from this item and you'll have a nice graphical partitioner.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Campingman on 2007-04-01
In terminal 

Sudo aptitude install gparted

Just worked ok for me

---

### Post by Traks on 2007-04-01
In Terminal:

> sudo apt-get install gparted

worked for me

---

### Post by linuxjerk on 2007-04-01
That apt-get install worked great.
Thanks guys

---

### Post by Maestro23 on 2007-04-01
> **linuxjerk said:**
> How do I install gparted the GNOME Partition Editor on my system?
I found it in the Synaptic Package Manager but when I try to install it I get
errors. Is the SourceForge site down? Or is the file no longer available?
I did a search on yahoo for gparted. I found a file to download (I think it was on
the sourceforge site).
When trying to install it I get lib's not found errors, directory not found errors.
If you want me to post the configure.log I will but it's big.
There has to be an easier way. I have downloaded many packages with the
package manager without problems until now.
Any suggestions???

Do you have all your Repositories enabled?

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Edit: Nevermind, I see they got you on the right path.

---

