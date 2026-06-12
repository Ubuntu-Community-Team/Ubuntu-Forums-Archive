---
title: "How do I reset the Ubuntu Sound system to its very initial configuration?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-03-19
Hi
Thank you for reading my post
Is there any way to fully reset the sound system configuration? I mean  I make my linux sound system to become the same as after I installed Ubuntu?
I made some changes here and there any now the sound is very crazy, It looks like that it comes through an spiral pipe :(

Thanks.

---

### Post by (((X))) on 2008-03-19
Read my last post
[http://ubuntuforums.org/showthread.php?t=727738](http://ubuntuforums.org/showthread.php?t=727738)

---

### Post by (((X))) on 2008-03-19
If you still want to reconfigure sound, purge alsa-base and alsa utils.
Install them back again
run alsaconf as super user(requires alsa-utils)
alsaconf will try to detect your soundcard.

---

### Post by legolas_w on 2008-03-19
> **(((X))) said:**
> Read my last post
[http://ubuntuforums.org/showthread.php?t=727738](http://ubuntuforums.org/showthread.php?t=727738)

Hi, Thank you for keeping an eye on my problem.
I tried your last solution but it does not works for me.
Thanks.

---

### Post by legolas_w on 2008-03-19
> **(((X))) said:**
> If you still want to reconfigure sound, purge alsa-base and alsa utils.
Install them back again
run alsaconf as super user(requires alsa-utils)
alsaconf will try to detect your soundcard.

Hi
I tried to remove those package and I got the following error:

```


sudo dpkg -P alsa-base alsa-utils
[sudo] password for legolas:
dpkg: dependency problems prevent removal of alsa-base:
 ubuntu-minimal depends on alsa-base.
dpkg: error processing alsa-base (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of alsa-utils:
 ubuntu-minimal depends on alsa-utils.
 gdm depends on alsa-utils.
dpkg: error processing alsa-utils (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 alsa-base
 alsa-utils


```

I also applied  Howto: Happy ALSA, OSS, ESD, with Duplex - Sound Settings located at [http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753) and I do not know how to reverse those commands.
Do I need to manually reverse them in order to install alsa again or installing the alsa packages will reverse tips of that thread automatically?

Thanks.

---

### Post by (((X))) on 2008-03-19
esound was edited as well, but I don't have any esd.conf in /etc/esound/
or asound.conf
Perhaps because I use alsa.
Just purge libesd-alsa0 and install libesd0 back, maybe other packages you deleted as well.

---

### Post by legolas_w on 2008-03-21
Hi
I Install libesd0  and there is no changes in the voice system
I can not hear the voices correctly yet.

Any suggest which prevent reinstalling Ubuntu is very welcome.

BTW, will it fix if i upgrade to Ubuntu 8.4 beta?


thanks.

---

### Post by legolas_w on 2008-03-22
Any comment, guys there should be some place that sound system store its configuration, please let me know where is it?
Also, can some one please share his/her sound system configuration?

Thanks

---

### Post by unutbu on 2008-03-22
(((X))) might know better than me, but if alsa-base and alsa-utils are the packages that need to be reconfigured then perhaps 
```

sudo dpkg-reconfigure alsa-base
sudo dpkg-reconfigure alsa-utils
```

---

### Post by legolas_w on 2008-04-02
Thank you for reply but I had I had no luck with:

```
sudo dpkg-reconfigure alsa-base
sudo dpkg-reconfigure alsa-utils
```

is there any way to reset players configuration?
I have mplayer, amarok, exaile, ..

Thanks

---

### Post by legolas_w on 2008-04-04
Hi
It will be a nightmare to reinstall linux and all applications and customization.
Please let me know if you know any other solution in order to fix the voice system.
for example, how I can remove all sound related software and configuration from the linux and then install them again?

Thanks

---

### Post by diplomat.x on 2008-04-15
Hi legolas_wa. Even i want to reset the sound. Here is my thread lol [http://ubuntuforums.org/showthread.php?t=755042](http://ubuntuforums.org/showthread.php?t=755042)
Lets hope either of our threads get an answer.

Bumping this thread to the top.

---

### Post by diplomat.x on 2008-04-15
My problem solved. YAY. Give it a shot legolas.

[http://ubuntuforums.org/showthread.php?t=755668](http://ubuntuforums.org/showthread.php?t=755668)

---

