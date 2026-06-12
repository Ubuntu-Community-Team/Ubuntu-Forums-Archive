---
title: "reLinux questions &amp; ubuntu customization"
date: 2012-01-24
forum: Any Other OS
---

### Post by blackhex666 on 2012-01-24
p { margin-bottom: 0.08in;I want to make a custom distribution based on ubuntu.I read all posts and tutorials that I found.But I still have some question before I start.Im getting borred of installing all the aplications and all of the customization each time I reinstall linux.And I reinstall a lot because im learning by distroing. 

 ReLinux Questions:
 

 1.How exactly do you install relinux ? You just coppy the files ? Because I didn`t really undurestoot from the txt file included in archive.
 2.You install ReLinux on you`re machine???or on a virtual-linux??i mean you install it on a fresh new distribution that you want to customize?
 3.When you finish can you have the “try linux” ?? or its just install option?


There is a better tool than reLinux??for ubuntu 10.04

---

### Post by Double.J on 2012-01-24
I haven't personally used ReLinux - I have used RemasterSys that's very similar in it's aims - to create a bootable ISO of your system, allowing you to reinstall.

It is worth pointing out that you are not creating a new "distro"; that's a ridiculous amount of work. - you are basically backing up your current configuration to an ubuntu installer disk - you can run a live version of it and install it, but it's still ubuntu, just configured how you want it :)

Looking at the ReLinux sit, it's main plus over remastersys seems to bethat it can be ran from a wubi install - a very handy way to move your install over to a full install. Other than that there seems to be a lot of crossover - seems that ReLinux was started because Remastersys wasn't being maintained, but now is. Having not used ReLinux.. I can't say, but I suspect that for the purpose of just making an ISO, RemasterSys may have more online tutorials?

As for installing, it's a source package - so the readme should tell how - it may just be a bit confusing. You have to install from the terminal; first use archive manager to extract the files, then change to the directory where you've got it - for the case of downloads:
```

cd Downloads/ReLinux-folder

```

Then use the reame commands. A typical install would be the following set of commands to give you a reference:
```

./configure
make
make install

```
./configure may throw out some dependencies you don't have - you'll have to install these prior to attempting to build again.

you can get a deb package of RemasterSys that you don't need to go near the terminal to install, and there's an ubuntu specific page [here]("http://www.remastersys.com/ubuntu.html") - the deb package is half way down... but I'd read the page ;)

and finally you install it on your current install and use it to make a live cd/dvd of your current set up - this can be run as a live disk or usb, and can be installed from.

Once again - not a distribution just turning your system into a live cd ;)

Hope it helps!

---

