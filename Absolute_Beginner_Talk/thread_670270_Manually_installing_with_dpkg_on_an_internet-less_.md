---
title: "Manually installing with dpkg on an internet-less laptop..."
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by skyedeveloper on 2008-01-17
I'm running Ubuntu 7.10 on a laptop without an internet connection and I'd like to be able to install additional packages - I understand these can be downloaded from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Is there any way I can download packages ensuring that all dependencies are downloaded along with them? (on packages.ubuntu.com, selecting one dependency leads to another, which in turn leads to another and it seems to go on forever...)

I'll be downloading these packages and transferring them to my internet-less laptop via a flash disk.

Also, dpkg is the right way to go once I've got the packages on my laptop? Or is there another way of manually installing them.

Thank you for your help. Appreciate it!

---

### Post by dstew on 2008-01-17
Many of the dependencies listed in most packages are already taken care of with the original Ubuntu installation. What package do you want to install? If a package needs other files to be installed, it will give you a list when you try to install it. Without internet, you just have to go and get the dependent packages. But, it doesn't go on forever. Usually after one or two cycles of this kind of thing, you are ready to go.

---

### Post by mikewhatever on 2008-01-17
Try this [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/). Dpkg is the way, but I can't imagine solving all the dependencies manually.

---

### Post by mcduck on 2008-01-17
If you can get the laptop connected to Internet at least once, so that apt-get can download repository indexes, it's possible to use Synaptic/apt-get to generate a list of packages it needs to install whatever you want to install.

In Synaptic you can just select what you'd like to install,and then go to File/Generate package download script.

(but like I said, before you can do that you need to run 'apt-get update' at least once, otherwise apt-get/Synaptic has no way of knowing what packages might be available.)

---

