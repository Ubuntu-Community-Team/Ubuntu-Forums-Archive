---
title: "My MacBook boots Ubuntu only at second try"
date: 2018-08-23
forum: Apple Hardware Users
---

### Post by sbac on 2018-08-23
I have a MacBook from 2017, first with Xubuntu 16.04 and since yesterday with Ubuntu 18.04 LTS. It's the only OS in my Mac and it worked fine until now.
Even when it had Xubuntu 16.04, since a week ago (so the problem is independent of the update), the system did not boot or reboot the first time I power it on. 
I have to power it off pressing the button and after that (now with 18.04 LTS) it shows the GNU GRUB 2.02 menu where I can select several ways of booting Ubuntu (I tried them all with no result). 
I press return to use Ubuntu as default and the system boots fine after that.

I tried boot-repair without result. The resulting URL is [http://paste.ubuntu.com/p/3wZTsMwSjm/](http://paste.ubuntu.com/p/3wZTsMwSjm/)

---

### Post by howefield on 2018-08-23
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by francoisdelabre on 2018-10-08
I had an issue with a Macbook (late 2006) and Ubuntu 16.04, where boot was OK one every two starts.
On the second boot, the Grub menu had a 30 seconds timeout to choose an entry whereas the default is 10 seconds.

It seems Grub has a different configuration when it detects a previous boot did not succeed.
I had a look at the grub.cfg configuration file and it does different things when the "recordfail" attribute is set.
On my configuration, the difference was mainly on the GFXmode setting.

So I added the following line to the Grub configuration in */etc/default/grub* to force the text mode :
GRUB_GFXPAYLOAD_LINUX=text

The grub configuration then needs to be regenerated with [I]sudo update-grub
[/I]
Hope this helps!

---

### Post by gsahli on 2018-10-10
The idea above may work...
It sounds to me like you have a drive spin-up time issue.

---

