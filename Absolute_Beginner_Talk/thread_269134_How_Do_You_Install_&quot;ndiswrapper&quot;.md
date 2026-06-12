---
title: "How Do You Install &quot;ndiswrapper&quot;?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Nut on 2006-10-01
Yeah, I read the install file, but I really don't get it because I'm just starting to learn how to use Linux... So, yeah.

Help!

---

### Post by pay on 2006-10-01
If you are compilling source make sure you install gcc```
sudo aptitude install build-essential
```What part of the guide don't you understand?

---

### Post by blx_286 on 2006-10-01
> **Nut said:**
> Yeah, I read the install file, but I really don't get it because I'm just starting to learn how to use Linux... So, yeah.

Help!

In Terminal, type ```
sudo apt-get install ndiswrapper-utils
sudo apt-get install ndisgtk_0.6-1ubuntu1_all.deb
``` or you can use the Synaptic Package Manager to install these.

The second line installs the GUI (graphic user interface) for ndiswrapper. Once it's installed, it can be found at >System >Administration >Windows Wireless Drivers.

Also, check out the other post on the rt2500 drivers, because I don't remember if they use ndiswrapper or not.

---

### Post by Nut on 2006-10-01
I love using this phrase so I'll use it again...

"Speak retard to me."

I'll try that though.

---

### Post by aysiu on 2006-10-01
[Where's the terminal?](http://www.psychocats.net/ubuntu/terminal)

Paste this command in the terminal: ```
sudo aptitude update && aptitude install ndiswrapper-utils
```

If the package is not found, try this: ```
sudo apt-cdrom add
sudo aptitude update && aptitude install ndiswrapper-utils
```

---

### Post by Nut on 2006-10-01
What will ndiswrapper do exactly?

Does it need to be in a certain place to start the intallation from the terminal?

What will happen when I install it with that little thing you told me to put in the terminal?

---

### Post by Nut on 2006-10-01
Neither worked...

**The first one came out as this...**

sudo aptitude update && aptitude install ndiswrapper-utils

first resulted in:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

**And the second this:**
Yeah, it wanted me to put a disc in and press enter.

---

### Post by aysiu on 2006-10-01
You should put the disk in--whatever you used to install Ubuntu in the first place.

---

### Post by pay on 2006-10-02
You need to run it as root (hence the comment are you root?
change```
sudo aptitude update && aptitude install ndiswrapper-utils
```to```
sudo aptitude update && sudo aptitude install ndiswrapper-utils
```

---

### Post by haxer on 2006-10-02
When im starting up windows wireless drivers they ask me to install drivers but where do i find these? :rolleyes:

---

### Post by haxer on 2006-10-02
Please help :P

---

### Post by az on 2006-10-02
The windows driver that ships with your card has an .inf file with it.  Use that.

You may need a more recent version of the driver, too.  The one that shipped with your card may be too old.

See here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

