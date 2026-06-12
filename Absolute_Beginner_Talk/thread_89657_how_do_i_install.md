---
title: "how do i install??"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by AlMaSoUdI on 2005-11-13
how do i install the apllication with are already in my desktop ??
like i download the gmail-notify-1.6 and the file already in my desktop...so how can i install it ???
in windows just click on it and follow 
so what about linux ??

---

### Post by Xian on 2005-11-13
That package is in the universe repos:

```
$ sudo apt-cache policy gmail-notify
gmail-notify:
  Installed: (none)
  Candidate: 1.6.1-0ubuntu1
  Version table:
     1.6.1-0ubuntu1 0
        500 http://archive.ubuntu.com breezy/universe Packages
```

Read [How-To Add Repositories](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse) and install using [Synaptic](https://wiki.ubuntu.com/SynapticHowto?).

---

### Post by aysiu on 2005-11-13
You install it via Synaptic.
You don't have to download the file separately.
Synaptic will download and install the program with a few clicks.
For more info on how to use Synaptic, go [here](http://www.psychocats.net/essays/winuxinstall.php)

To enable the Universe repositories (to make the application available, along with hundreds of others), go to the first link in my sig.

---

