---
title: "[SOLVED] apt-get upgrade"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by piperdown10 on 2008-03-17
So I'm trying to follow [this]("http://ubuntuforums.org/showthread.php?t=624644") thread's advice on installing wine. I get all the way to 'sudo apt-get upgrade' and it hangs, so I close out the terminal and type 'sudo apt-get upgrade' and get this:

> noob@ubuntu:~$ sudo apt-get upgrade
[sudo] password for noob:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
noob@ubuntu:~$ sudo dpkg --configure -a
Setting up capplets-data (1:2.20.1-0ubuntu1) ...

And thar she hangs. Any help? Is there a way to cancel out the intitial upgrade and start over?

Thanks ahead of time.

---

### Post by handydan918 on 2008-03-17
> **piperdown10 said:**
> So I'm trying to follow [this]("http://ubuntuforums.org/showthread.php?t=624644") thread's advice on installing wine. I get all the way to 'sudo apt-get upgrade' and it hangs, so I close out the terminal and type 'sudo apt-get upgrade' and get this:



And thar she hangs. Any help? Is there a way to cancel out the intitial upgrade and start over?

Thanks ahead of time.

i get this same issue on a clean install just trying to install the first round of updates. 
After trying everything I could think of (apt-get install -f, dpkg --reconfigure -a , aptitude safe-upgrade, etc...) I gave up and just run it as installed. 
This is why Ubuntu goes well with virtual machines running Debian stable hosts...

---

### Post by piperdown10 on 2008-03-18
That's the problem though, I don't have any version of wine installed now. I needed the newest version and so I removed the old one and now have nothing.

---

### Post by plucky on 2008-03-18
piperdown10,

I would remove those lines from the **sources.list** and use the method specified at the **Wine HQ** website located [here](http://www.winehq.org/site/download-deb)

Just tried it and it works.


Good Luck

---

### Post by piperdown10 on 2008-03-18
So I decided to give this another go and I went in and tried it again. I went into the terminal and typed 'sudo dpkg --configure -a' and it started doing something which worked! I guess I'm not patient enough because it's finished the apt-get upgrade. Now I need my Gutsy disc so I can finish the Wine install.

Thanks for the advice plucky. I'm gonna get this working, somehow.

---

