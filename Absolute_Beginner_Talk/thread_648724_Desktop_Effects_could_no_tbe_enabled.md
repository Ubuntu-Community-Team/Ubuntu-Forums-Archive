---
title: "Desktop Effects could no tbe enabled?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by hilariousness16 on 2007-12-23
[http://i215.photobucket.com/albums/cc239/hilariousness16/Screenshot.png](http://i215.photobucket.com/albums/cc239/hilariousness16/Screenshot.png)


Someone please explain what's going on?

I got a ATI RADEON XPRESS 200M

---

### Post by spiderbatdad on 2007-12-23
have you installed the compizconfig-settings-manager from synaptic?```
sudo apt-get install compizconfig-settings-manager
```
Then try again to enable effects.

---

### Post by spiderbatdad on 2007-12-23
you might also need xserver-xgl from synaptic instead of those restricted driver.

---

### Post by hilariousness16 on 2007-12-24
linux@linux-laptop:~$ sudo apt-get install compizconfig-settings-manager
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by hilariousness16 on 2007-12-24
E: /var/cache/apt/archives/sun-java6-jre_6-03-0ubuntu2_all.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/sun-java6-bin_6-03-0ubuntu2_i386.deb: subprocess pre-installation script returned error exit status 1

:guitar:

---

### Post by hilariousness16 on 2007-12-24
ok nvm everthing is installed like u told me but didn't fix anything?

---

### Post by spiderbatdad on 2007-12-24
```
sudo apt-get update
```
you may have interupted the update manager when you started trying to install packages. I'm not sure.

---

### Post by adam.tropics on 2007-12-24
> **spiderbatdad said:**
> you might also need xserver-xgl from synaptic instead of those restricted driver.

Not any more...yay! If you use the current proprietary drivers from ATI, [download here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.443.1-x86.x86_64.run"), install [guide here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"),(use method 2) you can use AIGLX instead of worrying about xgl....much much simpler. Performance on the 200m isn't perfect, but it's good enough, and far far better than it was not so long ago.

As mentioned above, install compizconfig-settings-manager, and I would suggest fusion-icon as well. Not sure if that is in the repos, but it's available [here]("http://ubuntuforums.org/showpost.php?p=3184350&postcount=4"). Incedentally, Compiz-fusion also has a forum, which can for the most part be very helpful. Check it out [here.]("http://forum.compiz-fusion.org/index.php")

Happy Christmas.

---

### Post by hilariousness16 on 2007-12-24
did that and didn't work -.-

still same message

---

### Post by Lostincyberspace on 2007-12-24
Have you tried using envy to install you driver?
Heres the link.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

