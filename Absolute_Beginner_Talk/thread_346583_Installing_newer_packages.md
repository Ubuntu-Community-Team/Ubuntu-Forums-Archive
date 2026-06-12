---
title: "Installing newer packages"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by randomperson83 on 2007-01-25
I need subversion 1.4.x for compatibility with some of my existing tools. The default edgy repository contains 1.3.x, which for my purposes doesn't work. Now, feisty appears to have a subversion 1.4.x in it, but when I downloaded the package it wanted to install a bunch of items that didn't exist in the edgy repository (of course). I tried adding the feisty repository to /etc/apt/sources.list, but it wanted to upgrade 728 packages... which sounded like it would be a bad idea. 

So... if theres a package out there I want, is there a way to just install that package and its dependencies from some X repository (like for example, the feisty repository) without affecting my existing packages? Thanks.

---

### Post by taurus on 2007-01-25
Why not remove the old version with synaptic/apt-get/aptitude, then download the latest version from source and build it for your machine?

---

### Post by randomperson83 on 2007-01-25
I considered that, and if theres not another way to do so then thats what's going to happen. But the thing about compiling from source is that if there are upgrades or anything like that then you cant simply just tell the package manager to 'update' it, you have to recompile and make install again... 

So yeah, if theres not an easy way to do that, then I'll just compile from source. I'm guessing there isn't an easy way?

---

### Post by taurus on 2007-01-25
Or upgrade your machine to Feisty Fawn.

---

### Post by pay on 2007-01-25
You could add the source repo from feisty. That way it won't upgrade your binary packages. You'll then be able to install subversion with```
sudo apt-get build-dep subversion
sudo apt-get --build source subversion
```You will also keep up to date with the latest version that way, but you will still have the problem with having to compile it again.

---

### Post by randomperson83 on 2007-01-25
pay: That sounds like a good idea, but doesn't work:
```
E: Build-Depends dependency for subversion cannot be satisfied because the package libneon26-dev cannot be found

```

taurus: Isn't Feisty supposed to be alpha/beta? I don't have a problem installing a few packages that are beta, but a whole system? Hmm.. though I guess technically since the subversion package is only beta for Ubuntu, and upstream thinks its stable then maybe all/most packages are? 

I guess I'm still not 100% used to the way Ubuntu partitions off versioning to different releases.

---

### Post by pay on 2007-01-25
You could just compile it without libneon support with sudo apt-get --build source subversion, but it might fail. It looks like libneon26-dev is only in feisty. But I don't know what libneon is, so I don't know what features won't be built.

---

### Post by randomperson83 on 2007-01-25
Yeah, it did. Bah. :)

---

### Post by randomperson83 on 2007-01-25
Yeah, it did fail. Bah. :)

---

### Post by elektronaut on 2007-02-06
For anyone who wants to compile subversion 1.4: Here's a HowTo: [http://ajopaul.wordpress.com/2006/12/11/setting-up-a-svn-14-server-using-apache-22-on-ubuntu/](http://ajopaul.wordpress.com/2006/12/11/setting-up-a-svn-14-server-using-apache-22-on-ubuntu/)

---

