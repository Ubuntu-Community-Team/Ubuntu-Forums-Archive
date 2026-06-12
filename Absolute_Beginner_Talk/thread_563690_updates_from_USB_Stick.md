---
title: "updates from USB Stick"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by howiehowie93 on 2007-09-30
Hi,
I'm using Ubuntu 7.04  on a laptop that i dont connect up to the www as i work away from home. Recently I put a cover disk in from a PC Magazine; a program popped up and told me there were more recent files on it which i should install - it was the update manager i think.

this was most unexpected but a brilliant feature! i have a work pc that i can connect to the www -hence this message and downloaded OO.o (the latest 2.20 or something. I transfered this to a USB stick and hopped that it would be recognised automatically as having upgraded files on - but no :-(.
is there anyway to have upgrade manager easily do this?

thanks in advance
H

---

### Post by candtalan on 2007-09-30
updates are managed by apt (synaptic I think). The closest I know how to get near what you want might be 'aptoncd'

the updates are quite complex things, because each and every individual item has to be exact and correct, depends on your existing state.

good luck.

---

### Post by snkiz on 2007-09-30
I've Done A Couple Of Updates From Cd I Don't See Why A UsB Stick Would Be Any Different. You May Have To Point Your Package Manager Manualy To Your UsB. Also When You Use The Package Manager On Your Connected Pc To Get The Updates There Is An Option To Save The Packages To Disk, Do It That Way Save To Your UsB And It Should Work. Failing That Try To Add The Directory You Saved InTo Your Sources List There Is A Gui For That In System Options.

---

### Post by ruibernardo on 2007-09-30
You could copy the .deb files from the USB stick into the directory /var/cache/apt/archives/ and then click reload on Synaptic or type "sudo apt-get update". The files should be then available to upgrade or install.

---

### Post by ruibernardo on 2007-10-12
I recently put some time into this problem. Just saving the files to that directory isn't enough. You would have to run:

```
cd /var/cache/apt/archives
sudo dpkg-scanpackages . /dev/null | gzip > ./Packages.gz
sudo apt-get update
```to make them really available to apt-get/Synaptic.

While in this subject, I've created a script that uses dialog (ncurses) as GUI and can update an offline Ubuntu from (in the worst case) a LiveCD and a USB stick. It was created precisely for the kind of problem of this thread, so I leave a link to the thread about this script here as an option to who has a similar problem.

[Howto: NoNetDebs - upgrade Ubuntu without Internet (or with low-bandwidth connection)]("http://ubuntuforums.org/showthread.php?t=572819")

---

