---
title: "after feisty fawn installation vmware stopped working"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by obaco on 2007-04-20
after feisty fawn installation vmware server stopped working.
it looks its loading but then nothing happens.
how can i fix it?

---

### Post by Obor on 2007-04-20
Because you are running new kernel you need to configure vmware again.
```
sudo /usr/bin/vmware-config.pl
```
Should do it. VMware will stop working after each kernel update...

---

### Post by obaco on 2007-04-20
i already did that....
i found this blog post
[http://www.rickhurst.co.uk/2006/09/20/ubuntu-update-kills-vmware-server/](http://www.rickhurst.co.uk/2006/09/20/ubuntu-update-kills-vmware-server/)


still doesnt work.... i guess it wants something like c compiler?


this is whats in the shell


make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

Execution aborted.

---

### Post by Obor on 2007-04-20
Maybe this will help [http://ubuntuforums.org/showthread.php?t=413646](http://ubuntuforums.org/showthread.php?t=413646)

---

### Post by tatster on 2007-04-20
Hi.

I was having problems with vmware-config.pl bombing about vmmon modules.....
A solution that worked for me was to install g++

```
sudo apt-get install g++
```

This works for me, so I hope it helps you.

Tat.

---

### Post by obaco on 2007-04-20
it still doesnt work... keeps complaining about wmmon and kernel incompatibility.

---

### Post by tatster on 2007-04-21
Hi obaco,

Might be worth checking another thread I've posted in.....

[http://ubuntuforums.org/showthread.php?p=2497876#post2497876]("http://ubuntuforums.org/showthread.php?p=2497876#post2497876")

There was one other thing I tried as well as install G++, detailed in that thread - and it worked for a couple of people over there - so you never know???

Hope this helps,

Tat.

---

