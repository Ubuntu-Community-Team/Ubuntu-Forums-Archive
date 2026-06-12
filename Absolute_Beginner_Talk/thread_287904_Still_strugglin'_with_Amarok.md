---
title: "Still strugglin' with Amarok"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Belgatom on 2006-10-29
The story so far: 

Installed amarok via apt-get. Received version 1.3.9. AmaroK looked excellent but unfortunately did freez a few times per session. Tried solving this but as a total beginner in Linux, prefered to uninstall and evaluate built-in music manager. But that's not really what I wanted. So I looked into Amarok some more. A few places gave me the advise to upgrade to version 1.4.2 (or higher). Been trying to do this using [this thread]("http://ubuntuforums.org/showthread.php?t=286324"). But I stranded. 

Not nowing how to continue, I decided to risk it and install via the "apt-get" method as before. What I got is written underneath, hope someone can help me on my way. AmaroK really has everything to offer and I would love to get it working. 


> sudo apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: libvisual-0.4-0 (>= 0.4.0) but it is not installable
E: Broken packages


---

### Post by mahy on 2006-10-29
Try to install libvisual alone, it'll tell you why it can't be installed.

---

### Post by Belgatom on 2006-10-29
Ok, I tried. 

> sudo apt-get install libvisual
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libvisual

So sources.list problem???

---

### Post by picpak on 2006-10-29
Try installing libvisual-0.4-0.

---

### Post by Belgatom on 2006-10-29
OK, tried it.

> sudo apt-get install libvisual-0.4-0
Reading package lists... Done
Building dependency tree... Done
Package libvisual-0.4-0 is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libvisual-0.4-0 has no installation candidate


It's all a bit confusing for this new convert...

---

### Post by picpak on 2006-10-29
I'm guessing that your package is obsolete. Try following the instructions here:

[http://kubuntu.org/announcements/amarok-1.4.3.php](http://kubuntu.org/announcements/amarok-1.4.3.php)

---

### Post by Belgatom on 2006-10-29
If you follow the link in my first post, you will find another thread. At the end of that thread, a person gave me the same advise. 

I have followed that advise:

>  wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
 sudo apt-key add kubuntu-packages-jriddell-key.gpg

You will get a message "OK"

I got that "OK". In my home folder, I received kubuntu-packages-jriddell-key.gpg. 
It did however talk about opening backports? 

> you need to enable dapper-backports to be able to install Amarok 1.4.3. This includes unsupported updates for other popular packages including KTorrent and K3b.

No idea what this meant but did find some sources that talked about backports. I added these. My sources.list now looks like this:

> # Line commented out by installer because it failed to verify:
# deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb [http://ftp.belnet.be/packages/ubuntu/ubuntu](http://ftp.belnet.be/packages/ubuntu/ubuntu) dapper main restricted universe multiverse
deb-src [http://ftp.belnet.be/packages/ubuntu/ubuntu](http://ftp.belnet.be/packages/ubuntu/ubuntu) dapper main restricted universe multiverse

deb-src [http://imbrandon.com/packages](http://imbrandon.com/packages) dapper amarok
deb [http://kubuntu.org/packages/amarok-143](http://kubuntu.org/packages/amarok-143) dapper main

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse


As you notice, the amarok-143 source is there aswell. My question is, how do I now proceed.

---

### Post by picpak on 2006-10-29
Run the following:

```
sudo apt-get update
sudo apt-get install amarok
```

You may have to remove the previous Amarok.

---

### Post by Drakkor on 2006-10-29
Can't you just use the Synaptic package manager to download and install it ?

---

### Post by picpak on 2006-10-29
Wait a minute, is this Dapper or Edgy?

---

### Post by Belgatom on 2006-10-29
It's dapper. 

Concerning Synaptic, whenever I click AmaroK, it complains about other packages.

---

### Post by picpak on 2006-10-29
What are the other packages?

---

### Post by Belgatom on 2006-10-29
In "simple mode" :
> 
Cannot install "amarok"

This application conflicts with other installed software. To install "amarok" the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict. 


In "advanced mode" : 

When I select "amarok" and mark it for installation, I get: 

> amarok:
 Depends: amarok-xine but it is not going to be installed
 Depends: libtunepimp3 (>=0.4.2) but it is not installable
 Depends: libvisual-0.4-0 (>=0.4.0) but it is not installable

---

### Post by picpak on 2006-10-29
Hmm...very odd, indeed.

If it helps, here are some direct links to the package files:

[libtunepimp3_0.4.2-3ubuntu3~dapper1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libt/libtunepimp/libtunepimp3_0.4.2-3ubuntu3~dapper1_i386.deb)
[libvisual-0.4-0_0.4.0-1~dapper1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libv/libvisual/libvisual-0.4-0_0.4.0-1~dapper1_i386.deb)
[amarok-xine_1.4.3-0ubuntu8~dapper1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/a/amarok/amarok-xine_1.4.3-0ubuntu8~dapper1_i386.deb)

Install them by typing

```
cd Desktop
sudo dpkg -i *.deb
```.

---

### Post by Belgatom on 2006-10-29
That did it!

Thank you very much for sticking with it. 

I have one more question. Let's say tomorrow, a newer version of AmaroK is released. How does one update in Linux?

---

### Post by picpak on 2006-10-29
Well, with the repository given to you in [http://kubuntu.org/announcements/amarok-1.4.3.php](http://kubuntu.org/announcements/amarok-1.4.3.php) , it will automatically update.

---

