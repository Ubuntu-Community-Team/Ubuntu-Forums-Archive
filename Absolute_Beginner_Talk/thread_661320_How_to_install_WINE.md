---
title: "How to install WINE?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by koreninja on 2008-01-07
Hey,

Sorry if this has been asked 1000 times I searched around and couldn't really find an answer. I read this page and it was kind of vague. [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

I went to [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) and did the initial stuff... I did..

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

then

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

then i did

sudo apt-get update

And i'm lost now. I guess I have to go into APT and install it from there? How do I get to APT? Or is that just the add/remove in applications?

Sorry if this has been asked tons.
Thanks in advance. 
KN

---

### Post by mcduck on 2008-01-07
simple 'sudo apt-get install wine' will download and install it for you. Or you can go to System/Administration/Synaptic Package Manager, search for wine and then install it.

This might also be useful to read: [How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by rabbito on 2008-01-07
how do you get the Synaptic Manager to update to the current WINE though? the one Gutsy comes with is 9.42 but on WINEHQ there is 9.52. I really like the simplicity of using the Synaptic

---

### Post by JoshuaRL on 2008-01-07
I think you have to get that from their site.  If you try Synaptic it will automatically get the one in the Ubuntu Repositories.

Try the install directions from their site:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

That's what worked for me to get 5.2

---

### Post by bwtranch on 2008-01-07
If you have your repositories enabled. I think the best way is through apt

sudo apt-get install wine

sudo apt-get update

sudo apt-get upgrade

This should install the latest version.

---

### Post by bwtranch on 2008-01-07
Sorry for the re-post, but I thought of something. If you are going to do some installs from tarballs and such, it is a good idea to have build essential in your toolbox just do:

sudo apt-get install build-essential

and they ask you for your original CD.iso

This eliminates some library problems that you may run into installing from source code.:)

---

