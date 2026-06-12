---
title: "[SOLVED] vmware is installed, but it has not been (correctly) configured"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by mouseboyx on 2007-12-09
When i install vmware server it says everything goes fine but when i run it it says

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


I have tried reconfiguring it but nothing works.

Is there an environment variable to make it think that its installed correctly, because it is.

---

### Post by Dr Small on 2007-12-09
Have you tried running:
```
sudo /usr/bin/vmware-config.pl
```

---

### Post by mouseboyx on 2007-12-09
yes i figured out the problem:

vmware-server is a piece of crap and i dont need to run it.
sorry for wasting your time.

---

### Post by jonward690 on 2007-12-09
Hey man I no vmware is not that great.Try virtual box seriously it is great,I love it I have seemlesly intergrated windows and kubuntu for a couple weeks now and I love it.

---

### Post by Dr Small on 2007-12-09
Well, have you tried VirtualBox ? I just installed it the other night and it works fine.

Dr Small

---

### Post by mouseboyx on 2007-12-09
Thanks,

---

### Post by shamrock_uk on 2008-01-22
A bit late, but may help anyone searching for similar. Following these instructions on the [Gentoo wiki](http://forums.gentoo.org/viewtopic-t-464881-highlight-vmwareserver.html[/url) got rid of this error for me (mine was also correctly configured). 

Just do ```
sudo mv /etc/vmware/not_configured /etc/vmware/not_configured_backup
``` and re-run vmplayer. 

Worked like a charm for me. 

Also, if you get a failed message when it is trying to start vmware services after running the config programme, simply restarting them with ```
sudo /etc/init.d/vmware restart
``` got them all working.

---

### Post by d3athp3nguin on 2008-02-28
> **shamrock_uk said:**
> A bit late, but may help anyone searching for similar. Following these instructions on the [Gentoo wiki](http://forums.gentoo.org/viewtopic-t-464881-highlight-vmwareserver.html[/url) got rid of this error for me (mine was also correctly configured). 

Just do ```
sudo mv /etc/vmware/not_configured /etc/vmware/not_configured_backup
``` and re-run vmplayer. 

Worked like a charm for me. 

Also, if you get a failed message when it is trying to start vmware services after running the config programme, simply restarting them with ```
sudo /etc/init.d/vmware restart
``` got them all working.

Worked for me running a debian system.  I'd switch to another Virtual Machine if I didn't have to deal with Microsoft and its installation/registration limits on XP installs...

---

### Post by MasterSushi on 2008-03-14
> **shamrock_uk said:**
> A bit late, but may help anyone searching for similar.

This worked for me as well. Thank you very much for posting this, I would have never tried that.

---

