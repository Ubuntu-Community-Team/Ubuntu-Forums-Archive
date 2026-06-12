---
title: "[SOLVED] nm-applet missing - loosing connection"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2007-05-18
Hi all,


  I've noticed that nm-applet is missing after a while of usage, and I also loose my connection.

  This is what I got with nm-applet working:

```
victor@victor-laptop:~$ ps ax | grep nm-applet
 4801 ?        Ss     0:00 nm-applet --sm-disable
```

  This is what I've tried after it shut down:

```
victor@victor-laptop:~$ nm-applet &
[1] 7202
victor@victor-laptop:~$ ps ax | grep nm-applet
4801 ?        Ss     0:00 nm-applet --sm-disable
7202 pts/1    S      0:00 nm-applet
```

  I also got this on a terminal I had open without typing any command:

```
(nm-applet:7855): libnotify-CRITICAL **: notify_notification_close: assertion `notification != NULL' failed

(nm-applet:7855): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

  Any ideas?? 

Thanks,


Vic.

---

### Post by Najand on 2007-05-18
Try reinstalling network-manager packages:
```
 sudo apt-get install --reinstall network-manager network-manager-gnome
```

---

### Post by geekphreak on 2007-05-18
If you continue having problems with it, you may want to try wifi-radar. It is not as nice as network manager, but should get the job done

---

### Post by victorbrca on 2007-05-18
Thanks for the reply guys...

I'll try re-installing it at home tonite as my company blocked the repo sites....


Vic.

---

### Post by Najand on 2007-05-18
OK, I am waiting for your feedback.

---

### Post by victorbrca on 2007-05-20
> **Najand said:**
> OK, I am waiting for your feedback.

Hi Najand,

  I got home yesterday and everything was fine. I've been using my laptop today also with no problems, so I still have not re-installed nm-applet.

  It seems that the problem is only happening when I'm at work!! :confused:  I'm using a little linksys travel router to piggy-back into their network. 

  I'm gonna do some testings at home and see if It still happens.



Vic.

---

