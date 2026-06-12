---
title: "Differnence between Fedora and Ubuntu?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Fletchinator on 2006-09-21
What is the difference between Fedora Core 5 and Ubuntu?  they look very similar to me.

---

### Post by Brunellus on 2006-09-21
Ubuntu is a single-CD distro.  Fedora is a 5-CD distro.

Ubuntu uses Debian's package management tools:  .deb , dpkg, and apt.  Fedora uses Redhat's package management tools:  .rpm, rpm, and yum.

---

### Post by tkjacobsen on 2006-09-21
Most of the administrative tools are very different. Fedora has a system-config-* for everything.. Also they have preconfigured selinux. 

The biggest plus for ubuntu is the big repository.. When I used fedora I had a lot of trouble finding .rpm packages when i needed some software. This is much easier in Ubuntu,  for most commen use,it will not be a problem though.

I also thing fedora looks better and more professional than ubuntu.

The speed is allmost the same. (comparing dapper and fc5)

---

### Post by Fletchinator on 2006-09-21
what is the difference between those package management tools, and what is .rpm?

---

### Post by tkjacobsen on 2006-09-21
.rpm is the red hat package manager. Like debians .deb. While yum is the default package manager in fedora, you can install apt-get and synaptic, then it is much similar to using apt-get and synaptic in ubuntu.

EDIT. I don't really know the difference between .rpm and .deb. Rpm's biggest problem is its slow dependency resolving..

---

### Post by tkjacobsen on 2006-09-21
> **Brunellus said:**
> Ubuntu is a single-CD distro.  Fedora is a 5-CD distro.


You can also install fedora from one cd. just the 'linux askmethod' cheatcode in the boot manager. 

You'll need an url for a mirror

---

### Post by Metacarpal on 2006-09-21
> **Fletchinator said:**
> what is the difference between those package management tools, and what is .rpm?

Having worked on an rpm-based system (Mandrake) for quite a while, I can tell you one of the biggest differences.

Have you ever tried to install something on Fedora, only to be informed that it needs some other program or library that you don't have, and it doesn't really tell you how to fix that?  I often found myself in that situation, commonly called "dependency hell".

If you download a .deb package in a Debian-based system (like Ubuntu) and it requires other packages that you haven't installed, it checks to see if they're available from your download sources.list and tells you that it needs to install them, too.  You say yes, it downloads them, and all is well.

---

### Post by Kilz on 2006-09-21
One important difference if you happen to have a 64bit system. .rpm is designed to be multiarch. .deb is not. That means you can easily install 32bit and 64bit applications.
Example in 64bit SuSE if I want the i386 version of Wine. I click a little box on yast. It installs everything and it runs.
Example of 64bit Ubuntu if I want the i386 version of Wine. I must force architecture in a i386 deb file and manually copy in a library file.

But no matter what rpm based disrto, none, and I repeat none have a community even close to Ubuntu. To me it makes up for the extra headaches since I run 64bit.

---

### Post by jordanmthomas on 2006-09-21
If I recall correctly, you have to jump through several hoops to get NTFS filesystems to mount in Fedora because they won't include NTFS support in their kernel.  At least, I think that's they way it was last time I used Fedora.

---

### Post by Brunellus on 2006-09-21
I should also add that 'modern' rpm distributions include some provision for automatic dependency resolution, either by using apt4rpm or other such tools (like Fedora's 'yum' tool).  

I ran SuSE 9.1 before I ran Ubuntu...dependency hell was not fun.  It was possible get apt running, but then there was the headache of figuring out what repos to add to your sources.list.  

In the end, I jumped ship to Ubuntu, and haven't looked back.

In fairness, I've never used Fedora and yum.  I hear it's a good distro, and it certainly does a few things better than Ubuntu:  SELinux jumps to mind.

---

### Post by az on 2006-09-21
> **Fletchinator said:**
> What is the difference between Fedora Core 5 and Ubuntu?  they look very similar to me.

A distribution is a collection of free-libre software put together by it's (the distro's) community.  It's the same software, but the individual apps, the development they steer, the decisions they make all make the distribution unique.

---

### Post by james_san on 2006-09-21
Well to put it in simple words: They both look very similar, because they are both Linux at the heart, and use a program called Gnome for the desktop. It is Gnome that you see when you are using your computer (as opposed to all the stuff that is happening in the background that you can't see).

So: On the outside they look similar, but the main difference between different distributions is the way they configure things (like hardware detection). Ubuntu is very easy. Fedora Core is probably also very easy (I haven't used it since version 3).

What I like about Ubuntu is that it is supported by a company, and so lots of things get done properly. (Fedora is managed by a community, and has no official support that I know of). The fact that they use different package formats ("deb" and "rpm") doesn't really matter to a new user. They both work much the same in modern linux distributions.

In summary: Try Ubuntu. You will (hopefully) like it. If you want to do a bit more exploring after a few months, try installing Fedora Core. Then you will get to understand what a distribution really is (You never know what something is defined by until you have seen a different way of doing it).

---

