---
title: "Ubuntu is great so far!! But, have a few questions?"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by ervyxx on 2006-12-23
Hi!

Have installed Ubuntu 6.10 and everything is working fine. Synaptics is a great way to install/update applications.


This by far the first Linux OS which has almost all my hardware working out of the box.

Things which I didn't expect to work but, works fine:

1. Canon Digital IXUS 750 Digital Cammera
2. Canon LiDE 25 Scanner
3. Generic USB Memory Card Reader
4. Transcend 1 GB Flash Drive

Things which I haven't tried after installing Ubuntu on the HDD but, didn't work when I booted from the Live CD:

1. Canon Pixma iP3000 (Need to get those Canon Drivers mentioned here on the forum)

OK, so far, so great. Now about my questions?

1. Graphics is working fine but, do I still need to install the ATI drivers? I mean I have those ATI Integrated Graphics Motherboard Xpress 200. Will the acceleration available in the drivers better the performance of my system and improve DVD playback? If yes, can I install the drivers from Synaptics or if not, should I download and install them?

2. Synaptics is a great way to install/update software on Ubuntu. But, is it possible for me to download the updates or software from my workplace and install it through Synaptics at my home. Am asking coz, I have a very very slow Net connection at home and I have a Dedicated 640 Kbps ADSL connection at my office. If it can be done, how do we do it?

I'm an absolute newbie. You can assume, I've no past experience with Linux.

Thanks in advance. :-k

---

### Post by pay on 2006-12-23
For 2d, the open source drivers should be fine. But if you want to play games then you would need the fglrx driver

You can install downloaded .deb files with```
sudo dpkg -i <package>.deb
```

---

### Post by ervyxx on 2006-12-23
hey pay,

Thanks for the reply!

I won't be playing games but, I'll be watching a lot of DVDs. What do you recommend?

Also, how do I download packages from the Official Ubuntu Repositories? Got the install part from you but, need to know how to download the same from my work place?

---

### Post by pay on 2006-12-23
I would recommend that unless if you are experiencing problems then just use the drivers that you are using. Download the packages from here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by ervyxx on 2006-12-23
thanks pay. I'll keep the same drivers and see.

Thanks for the packages link.

What is the difference between, normal & backport packages?

Also, if I download the packages and install it @ home manually, will that specific application appear in synaptics as installed or will I break Synaptics?

Since, am a newbie, don't want to break many things.

Man, am enjoying linux. Only 146 MB used from my 1 GB memory. XP eats about 500 MB.

LOL

---

### Post by steve.horsley on 2006-12-23
> What is the difference between, normal & backport packages?
When an Ubuntu version is released, it is feature-frozen for stability - bug fixes only. Backports is packages where new features have been added, which are due for inclusion in the next upcoming release, and have been ported back to the old release. So they are versions with new features and possibly new bugs.

> Also, if I download the packages and install it @ home manually, will that specific application appear in synaptics as installed or will I break Synaptics?
I believe that they will appear to be installed in the normal way. However, some packages have a list of dependencies as long as your arm, in which case you could be downloading a package, taking it home only to find the next dependency so you still can't install for weeks. You may soon decide that this is not a good way to install software.

---

### Post by ervyxx on 2006-12-23
Hey Steve,

Thanks for the reply. I know that manual install may not be a good thing but, I have no option. At home I have a 48 Kbps NET connect where it's impossible to install large packages. At office, I have a 640 KBps connection.

That's the reason for manually doing it. :(

Thanks for explaining the backport difference.

---

### Post by smoker on 2006-12-23
hi, ervyxx,

if you were willing to pay something, you can order a dvd with all the packages from here:

[http://www.linuxemporium.co.uk/products/ubuntu_6.10/](http://www.linuxemporium.co.uk/products/ubuntu_6.10/)

hope this helps

---

### Post by Sef on 2006-12-23
Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

### Post by macogw on 2006-12-23
You can use Aptoncd (google it) to make an apt repository on a cd so you can burn it at work and then add it to your repository list in Synaptic, apt-get stuff from it, and it'll show up in Synaptic just like if you downloaded the programs.

---

