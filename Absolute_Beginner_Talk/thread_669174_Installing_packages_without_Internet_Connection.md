---
title: "Installing packages without Internet Connection"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by venu1729 on 2008-01-16
The comp on which I've installed Ubuntu, doesn't have an internet connection. I wish to install a few packages on it which are available on the repositories. 

I want to download the packages individually from a different computer, and get them installed in Ubuntu.
My hunch is putting the downloaded packages in a specific directory like apt-cache or something and doing a apt-get install should work. But I don't know the exact directory in which I have to put the downloaded packages, for apt-get install to work.
Please help me out.

Thanks.

---

### Post by miesnerd on 2008-01-16
i am by no means a pro at this, as I find its easier with ubuntu (genearlly) to just get an internet connection. But since I dont know your specifics, you can easily get a cd or a flash drive, throw the packages on there (make sure they're .deb packages) and double click. 

A program that ubuntu by default comes with called GDebi will take it from there.
The only problem is satisfying dependencies. You need to make sure that you have all the packages that whatever program you want to install you also have those packages. 
If need be, you can either check that program's website where it will list them or...
do what I said above with GDebi, and if it has dependencies that are not met, write them down (or copy- paste) and find them, then install them, then your package. 
Its really nice how that works out. Honestly, that's what makes debian based linuxes my favorite.
I know you can do that with lots of others, but it just seems to work better with debian (imo) than with tpm's or ebuilds.

---

### Post by venu1729 on 2008-01-16
thank you. this should work.

Just out of curiosity, I want to know if I can install packages using apt-get without internet.
My understanding is that, when we do a $sudo apt-get install , the package manager first searches the apt-get cache ((I want to know, where it is located), and if it finds it in this, it will install from there, otherwise search in the configured online repos. Please correct me if I am wrong.

---

### Post by njparton on 2008-01-16
I think there's a DVD edition available that comes with pretty much everything.  You will of course miss out on updates though.

---

### Post by Joeb454 on 2008-01-16
True, you could always get the DVD edition and install using that, or you could search [www.getdeb.net]("http://www.getdeb.net") and transfer the files to your PC from a flash drive as posted above :)

---

### Post by miesnerd on 2008-01-16
> **venu1729 said:**
> thank you. this should work.

Just out of curiosity, I want to know if I can install packages using apt-get without internet.
My understanding is that, when we do a $sudo apt-get install , the package manager first searches the apt-get cache ((I want to know, where it is located), and if it finds it in this, it will install from there, otherwise search in the configured online repos. Please correct me if I am wrong.

To answer your question, yes, and this is another area where within debian linux, ubuntu particularly excels.
For example, if the package you wanted was on the 8.04 pre-release, you could burn the cd, pop it in, and ubuntu would recognize it and as you if you wanted to start the package manager.

But to answer your question in a more relevant way (which I guess I should have done first-- sorry!) you can open synaptic and there's an option in there ( i cant look right now cuz im in a different linux distro) but you can change it to where it lets you add the cd packages. I dont know if you can do this with a flash drive, btw.

---

### Post by electricchild on 2008-03-11
Hey guys. I need a bit of help with this. I know you said we can just use the Ubuntu desktop environment to click and drag our .deb files to the right place, but what if I am just using a CLI? IE I have a debian distro running with just CLI and I want to install .deb files from a flash drive.

Can you point me in the right direction on how to do that?

---

