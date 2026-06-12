---
title: "Redirect the Repository to local sources"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by leverettson on 2007-09-27
So is it fair to say that without an internet connection you can't do much upgrading with Ubuntu? We have several machines we've loaded with 7.04 and as part of our project (a high school)  we need to share a folder on one of the Ubuntu machines and be able to see it from another. When I click admin/folder sharing it tells me I need to install samba and NFS, I uncheck Samba because I'm not trying to talk to any windows machines. NFS doesn't seem to install and my guess is it's because there is no internet connection. 
In another part of the building I have a very high speed internet connection and a Terastation. So my idea is to download an entire repository to the terastation, then configure Ubuntu to look to the terastation for its updates rather than the internet.
I suppose it's possible that the first machine I do this on I will need to pack it up to the internet connection to at least get the NFS files so it can then talk to the terastation, but further updates, I would be good to go. 
A really neat trick would be if I could put the files needed to install NFS on a CDRom and config Ubuntu to look to the CDRom. Then after NFS is loaded I could Config Ubuntu to look to the terastation for all further updates.
Before I go banging my head on the concrete wall for the next couple of weeks, is this even possible? Has anybody done it and if so do you have any advice.

Regards,
Leverettson

---

### Post by gnudoc on 2007-09-27
first of all, i'm glad to hear you're working on ubuntu on ahigh school setting - far too few schools seem to be using what should be the no-brainer choice for a school!

while i've not really done exactly what you're proposing, it should be do-able. aptoncd is a project that creates a cd rom repository for you. just install it on an ubuntu computer that does have net access (a simple sudo aptitude install aptoncd will do - or the equivalent in synaptic), use it to create a cdrom repository containing what you need for your isolated computer.

as far as creating a local repo on your terastation goes, these links should do the trick.

[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror](http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror)
[http://ubuntuforums.org/showthread.php?t=20217](http://ubuntuforums.org/showthread.php?t=20217)

however, if you are goiing ahead with that, then i don't think you should need anything extra on your isolated box. the steps that i would envisage (and bear in mind that i've not actually done this) are:
1) set up your local repo using apt-mirror
2) physically connect local computers to the network on which sits your repository (in your case, the terastation)
3) install ubuntu from a default cd onto the said computers
4) change the apt sources file to point at your local repo.

the page on popey.com gives a good step-by-step guide for parts 1 and 4.

---

