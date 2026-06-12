---
title: "Can't install anything in Ubuntu 7.10"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by binu305 on 2008-03-17
Recently  i have installed Ubuntu 7.0 from a CD. But when I try to install any software , it will ask a dependency file.I don't have an Internet connection.So please tell me what are the minimum dependencies needed for installing an application?

---

### Post by Xiong Chiamiov on 2008-03-17
The nifty thing about package managers is that not only do you not have to go find a site to download some application, but the package manager also downloads and installs anything else you'll need to get it to run (a dependency).  The dependcies vary depending on what it is you're wanting to install, so you'll have to look them up and download them all separately on another computer and install them yourself.  Lack of net access certainly makes life more difficult.

---

### Post by aysiu on 2008-03-17
If you don't have an internet connection, software installation in Ubuntu will range anywhere between inconvenient and painful. Work on getting that connection working as your top priority.

---

### Post by Jimmyfj on 2008-03-17
You need an Internet connection in order to install programs in Ubuntu. All software packages  are stored in repositories on a server. You could order Debian GNU/Linux which comes on a 3 dvd install set that has more than 27.000 packages to chose from. But on Ubuntu you need the Internet.

---

### Post by binu305 on 2008-03-17
Thank you for quick reply.

---

### Post by erginemr on 2008-03-17
If you can access internet from another machine or location, you can also download the DVD version of Ubuntu from:
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

which, supposedly, packs more packages inside the DVD.

---

### Post by erginemr on 2008-03-17
And the following is a good read on offline Ubuntu machines with a few techniques involved:
[http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/](http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/)

And here is a very promising method for offline installations and updates:
[http://ubuntu.wordpress.com/2006/07/08/installing-packages-on-computers-with-slow-connections-redux/](http://ubuntu.wordpress.com/2006/07/08/installing-packages-on-computers-with-slow-connections-redux/)

---

### Post by erginemr on 2008-03-17
Alternatively, you can use Synaptic itself to dowload the needed packages from another computer;
by letting it create a downloader script, running the script from a different Linux box (not necessarily Ubuntu), storing all downloaded packages in a storage medium (such as a pen drive or CD-R), bringing them back to your machine, using Synaptic again to have it them copy to the appropriate location (FYI, they will be stored in /var/cache/apt/archives actually, but you don't have to bother with this), and finally, letting it install those packages.

In the attached screenshots, I have tested installing the package "kcron" this way and it worked like a charm.

---

### Post by binu305 on 2008-03-17
I think this will work for me.

Thank you

---

### Post by binu305 on 2008-03-17
> **erginemr said:**
> If you can access internet from another machine or location, you can also download the DVD version of Ubuntu from:
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

which, supposedly, packs more packages inside the DVD.



I couldn't find a DVD version for download

---

### Post by thisismalhotra on 2008-03-17
> **binu305 said:**
> I couldn't find a DVD version for download

Please look carefully .. Links to DVD version are bottom of this page (the same link as before)

This Text from the sire: -

```
DVD downloads

For Ubuntu 7.10, our latest release, you can download DVDs from one of the following locations:

    * Australia
    * Europe
    * Finland
    * France
    * Germany
    * Greece
    * Netherlands (1)
    * Netherlands (2)
    * Russian Federation
    * South Africa
    * Spain
    * Sweden
    * Taiwan
    * Taiwan (2)
    * United Kingdom
    * United Kingdom (2)
    * United States
    * United States (2)

```


[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

