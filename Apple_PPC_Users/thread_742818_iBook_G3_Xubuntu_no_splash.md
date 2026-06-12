---
title: "iBook G3 Xubuntu no splash"
date: 2008-04-02
forum: Apple PPC Users
---

### Post by wirysage on 2008-04-02
Hey,
I have successfully installed Xubuntu on a iBook G3 late 2003 Model.
I'll walk you through what I have done
1. Normal live cd boot would not work after the white video screen and some memory page it would just go blank screen.

2. I tried booting live-nosplash and it worked great got in and I paritioned and Installed Xubuntu

3. But now I'm getting the same problem of the splash trying to play and getting the blank screen on start up of the installed Xubuntu 

4. On the Live CD it gave me a choice of Live, Live-Powerpc and (Live-nosplash and that worked).

5. What I need to know is how do I edit the yaboot.conf or the xorg.conf or other config file so it bybasses the splash screen and boots so it works like the no-splash cmd did on the live cd.
Thanks
Wirysage

---

### Post by slacka-vt on 2008-04-02
You can boot into your installed system the same way.
After the first boot menu, where you choose "l" for linux
You get to the second stage boot loader.
Here type:
```
Linux video=ofonly nosplash
```

Once logged in you edit your yaboot.conf

```
sudo nano /etc/yaboot.conf
```

~s

---

### Post by stream303 on 2008-04-02
You modifications go on the **append=** line of yaboot.conf, and after making the change, you need to do this to make the change recognized:

```
sudo ybin -v -C /etc/yaboot.conf
```

Some more useful info on yaboot can be seen here:

[https://wiki.ubuntu.com/PowerPCFAQ#head-7e0d9b980507337bf9c80768cabb8396a552335c](https://wiki.ubuntu.com/PowerPCFAQ#head-7e0d9b980507337bf9c80768cabb8396a552335c)

Update:  I went into a little more detaile on a related thread here:
[http://ubuntuforums.org/showthread.php?t=739028&page=2](http://ubuntuforums.org/showthread.php?t=739028&page=2)

---

