---
title: "Synaptic + dial-up"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by slink on 2006-04-21
Hi

I'm considering to install Dapper on my iMac next june when it'll be released but my internet connection is dial-up modem so... will I be able to download Synaptic's packages on any other computer with broadband, burn them on a CD , copy them on my iMac and then tell Synaptic to install these files offline ?

This way I would use Synaptic just to check updates but not to download packages. 

And even, can I upgrade the system that way ?

Is that a good idea?

---

### Post by Qrk on 2006-04-21
Yes, you can do it that way. Use synaptic to get a list of all the packages that need to be upgraded, and then go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to download them all. Burn all of them to a CD or the like. If you transfer them to your iMac via a CD, you can use these commands to install them:

```
cd /media/cdrom0
sudo dpkg -i *.deb
```

Sadly, I do not know how to automate downloading the packages unless your other computer runs ubuntu. It may be easier just to use dialup

---

### Post by Bloch on 2006-04-21
This thread is of interest to those who have no direct internet access on their computer:
[http://ubuntuforums.org/showthread.php?t=136955&highlight=packages+offline](http://ubuntuforums.org/showthread.php?t=136955&highlight=packages+offline)

I hope that link works. If not the thread is in the ubuntu cafe entitled  "We need an add-on CD" and initiated by aysiu.

---

