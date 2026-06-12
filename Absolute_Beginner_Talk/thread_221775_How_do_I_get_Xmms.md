---
title: "How do I get Xmms?"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Wadeisabeast on 2006-07-24
I want to try a different media player other than Xfmedia on Xubuntu.  And it's not in the Synaptic Package manager.

---

### Post by Jagot on 2006-07-24
Unless you've deleted some repositories from your sources.list it should be.

[http://packages.ubuntu.com/dapper/sound/xmms](http://packages.ubuntu.com/dapper/sound/xmms)  

Try from the command line:

```
sudo aptitude update && sudo aptitude install xmms
```

---

### Post by jordilin on 2006-07-24
xmms is in the repos. You should have the universe and multiverse repos apart from main and restricted. Take a look at /etc/apt/sources.list

---

### Post by jrev on 2006-07-24
Why not install Automatix ?
It will put your depositories uptodate and propose you to install a lot of complementary applications.
I did it last week and am happy about it ;)

---

### Post by wildseven on 2006-07-24
automatix is cool, but for easy installations automatix is not needed.

```
 sudo apt-get install xmms 
```

---

### Post by Jagot on 2006-07-24
Use aptitude, not apt-get:

[http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)

---

### Post by aysiu on 2006-07-24
Step 1: Get extra repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Step 2: Install XMMS: ```
sudo aptitude update
sudo aptitude install xmms
```

**Edit**: Actually, you don't need Step 1. Apparently, it's in the regular repositories. But Step 1 may not be a bad idea, as extra repositories will make more software available for you to easily install.

---

