---
title: "GUI CLI Problem"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by MRO46 on 2007-03-26
Ok, I installed Ubuntu server earlier today, no problem at all.  It starts up and everything is fine and dandy.  Problem I have is that when the system starts, I get a Command Line Interface, I thought Ubuntu was a GUI!?  Have I missed something blatantly obious when I installed the OS!?

I really need to get the GUI up and running, and enjoy the world that is Linux!

---

### Post by Lord Illidan on 2007-03-26
The server does not come with a GUI installed, as most linux servers are managed from the command line. Nevermind, it is easy installed. Just log on, make sure you are connected to the internet and type in :

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop
```

If you don't intend to use this machine as a server, then reinstall plain ubuntu, it will make things easier.

---

### Post by MRO46 on 2007-03-26
Thankyou very much!!

---

