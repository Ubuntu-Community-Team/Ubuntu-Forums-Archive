---
title: "Installs and dependencies"
date: 2011-11-28
forum: Any Other OS
---

### Post by bigseb on 2011-11-28
I want to work a bit with virtual box and Wine. In order to save on bandwidth I managed to download both elsewhere. But I noticed that when I install via synaptic there are usually some dependencies that are added.

Can I run the downloaded .deb for wine and vb on my pc and just download any missing dependencies? What is the best way to do this? If code is needed please provide.

Thanks.

---

### Post by WasMeHere on 2011-11-28
Hi bigseb,

I think you should regard the versions to be different, at least in the way they are compiled and linked. Often you can get brand new versions of software as deb install packages. On the other hand you get thoroughly tested versions for Ubuntu via the repositories.

In other words, installing via the repositories will give you one version with its dependencies, that are taken care of by apt-get or Synaptic or Software Center. Downloading deb files and installing should also should also give you a complete version unless it is described in the readme file that you need some other package.

I recommend that you install via the repositories unless you know that you need a brand new version to perform an important task.

Have fun finding out :-)
Olle

---

### Post by bigseb on 2011-11-28
It's confusing 'cos When I downloaded Wine from sourceforge the .deb was about 18Mb, but in Synaptic the total downolad came to 280 Mb!!! The Virtualbox download was 63Mb but in Synaptic its only 13Mb!!

Btw, I see the Synaptic Wine install includes Winetricks. Does that mean if I install Wine using Synaptic it already includes J# redistributibles and directx?

---

### Post by WasMeHere on 2011-11-28
You get more with the deb download of VirtualBox. See also
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1884709_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1884709")

I don't know those details about Wine, I have an old installation from the repositories but use it very seldom.

---

