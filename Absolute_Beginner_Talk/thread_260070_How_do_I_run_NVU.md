---
title: "How do I run NVU"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by linuxuser28 on 2006-09-18
I downloaded NVU from there website, extracted the folder to my desktop, but I do not know how to run it.
[http://www.nvu.com/index.php](http://www.nvu.com/index.php)

---

### Post by Brunellus on 2006-09-18
> **linuxuser28 said:**
> I downloaded NVU from there website, extracted the folder to my desktop, but I do not know how to run it.
[http://www.nvu.com/index.php](http://www.nvu.com/index.php)
Installing software on Ubuntu is generally NOT like installing software in Windows.  Instead of looking for individual websites/files, we have a package manager (synaptic) that will install things from a central database (repository) and keep them updated.

Nvu happens to be a program in the repositories.

[http://monkeyblog.org/ubuntu/installing.html#installing_with_synaptic](http://monkeyblog.org/ubuntu/installing.html#installing_with_synaptic)

If you don't find it, you might have to enable the 'universe' and 'multiverse' repositories:

[http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories)

---

### Post by bluefrog on 2006-09-18
sudo updatedb
locate nvu

writing nvu in a console should work.

Alternatively if you don't need the latest nvu, enable unvierse repository in synaptic and install nvu from there. Then use the applications > development > nvu menu

James

---

### Post by Obor on 2006-09-18
Is there a reason why you don't want to install from the repositories? You can install NVU (i'm not sure if it is the latest version) from synaptic package manager. Just search for NVU. 

Or terminal
```

sudo aptitude install nvu
```

If not follow the guide - [How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

Edit: My typing is very slow  :)

---

### Post by moma on 2006-09-18
EDIT: Ahh, people had already answered to the above question. This reply is unnecessary duplicate.

--------------------------------------------------------------
You can get NVU from the Ubuntu's repository.  The version in the Ubuntu's repo is up2date, as far I can see.

0) Search for NVU using Apt or Synaptic.
$ [COLOR="Green"]apt-cache search nvu[/COLOR]
nvu

$ [COLOR="Green"]apt-cache show nvu[/COLOR]
Package: nvu
Priority: optional
Section: **universe**/web
Installed-Size: 26440
....
Filename: pool/universe/n/nvu/nvu_1.0-0ubuntu4_i386.deb
.....

1) It is in the Universe repository.  
Enable (uncomment) Universe lines in your /etc/apt/sources.list -- if not already done.
$ [COLOR="Green"]sudo gedit /etc/apt/sources.list[/COLOR]
and update package list in your PC
$ [COLOR="Green"]sudo apt-get update[/COLOR] 

2) Use Synaptic Package Manager or Apt command line and install NVU.
$ [COLOR="Green"]sudo apt-get install nvu [/COLOR]

Start it from the Applications -> Programming menu or fire it from command line. 
$ [COLOR="Green"]nvu [/COLOR]

---

### Post by linuxuser28 on 2006-09-18
> **Brunellus said:**
> If you don't find it, you might have to enable the 'universe' and 'multiverse' repositories:
I did not know about that. That solved the problem. Thanks :D

---

