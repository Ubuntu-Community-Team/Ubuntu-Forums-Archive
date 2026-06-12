---
title: "Using alternate CD to boot?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by |2eM!x on 2007-10-02
Is it possible to run the alternate CD and let it run live?  I'm not sure how to explain it, but I mean run ubuntu off the alternate cd without installing?  Because I am getting an error using a partition "Because of an unknown reason its impossible to resize this partition check var/log/syslog or see virtual console 4".  And so I cant figure that out but I still want to delve into linux an ubuntu.  Any help?  Thankyou.

---

### Post by bodhi.zazen on 2007-10-02
The alternate CD is for installation only, it does not provide a desktop or live session.

Install form alternate CD: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Can you post the log file ?

```
sudo cat /var/log/syslog
```

Feel free to pipe that to a file and post it as an attachment :

```
sudo cat /var/log/syslog > error.log
```

then attach error.log here

---

### Post by |2eM!x on 2007-10-02
Dangbo.  Do you have any suggestions about my partition?  I do not want to format windows, I want to test ubuntu.

---

### Post by bodhi.zazen on 2007-10-02
First you can run from a live CD

Second you can use VirtuaBox or VMware

Third you can try Wubi : [http://ubuntuforums.org/showthread.php?t=396526](http://ubuntuforums.org/showthread.php?t=396526)

If you are running Vista, partition with the vista partitioning tool

If you are not running vista, defragment your windows partition first, from within windows, then re-try.

If that fails, try the grpated live cd, it is a more recent version of gparted :

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	
Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

---

