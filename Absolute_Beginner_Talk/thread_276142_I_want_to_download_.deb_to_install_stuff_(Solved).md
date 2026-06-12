---
title: "I want to download .deb to install stuff (Solved)"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by shivam on 2006-10-12
I don't want to use the apt utility to get packages directly from the net and install. Rather i would like to download the package as a source or a precompiled setup like .rpm .

But i am unable to get a website like [http://www.rpmfind.com/](http://www.rpmfind.com/) form where i can search for such software for ubuntu 

If someone has knows any good site for downloading software for ubuntu then do post the links.

---

### Post by bulldog on 2006-10-12
What's wrong with apt-get or synaptic??

When you use apt-get all will be updated automaticly.

Can't see why you should use another method.

---

### Post by Perfect Storm on 2006-10-12
It's also much safer to use synaptic/apt/aptitude


But you can find ubuntu .deb here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by aysiu on 2006-10-12
Like bulldog, I'm confused as to why you don't want to use apt.

The whole point is to make life easier for you. If you have a .deb by itself, you'll have to track down and install all the dependencies manually.

If you use apt, it tracks down and installs all the dependencies for you.

That said, this has a whole bunch of individual .deb files: [http://packages.ubuntu.com](http://packages.ubuntu.com) may help.

---

### Post by PriceChild on 2006-10-12
debs are ubuntu/debian's equivalent for rpms.

rpms are built for redhat.... not ubuntu.

Alien is a dangerous process and my cause instability in your system.

---

### Post by petri on 2006-10-12
RedHat based(?)systems use .rpm and Debian based systems use .deb :-D

---

### Post by kevinlyfellow on 2006-10-12
You can download .deb packages from packages.ubuntu.com.  .deb files are the precompiled packages for debian based distributions and the apt program is just an easy way to automate everything.  .deb files are to debian as rpm files are to red hat

---

### Post by shivam on 2006-10-12
well the whole purpose behind me not using apt-get is that once downloaded i want to save the package on my disk so that i just have to install it rather than download it again again when ever i do a fresh installation of ubuntu.
also i can use the packages on other pc's without internet connections. It make some sence i guess.

---

### Post by petri on 2006-10-12
In Synaptic menu Preferences and tab Files(? nonenglish version) there is radiobutton "Leave packages in cache" Could that help, I don't know. :-k

---

### Post by PriceChild on 2006-10-12
But the packages are downloaded to your disk!

Unless you apt-get clean, check out /var/cache/apt/archives If you backup the debs found here that's the equivalent to what you want :)

---

### Post by aysiu on 2006-10-12
When you use *apt-get* (or, better yet, *aptitude*), the packages get downloaded and stored in /var/cache/apt/archives

---

### Post by shivam on 2006-10-12
ok so i can save the packages from there for use in future.
Thanks for the help ....

---

