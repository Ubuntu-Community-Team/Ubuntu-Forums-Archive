---
title: "Adding a script to boot up"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by semperfiguy on 2007-11-24
Hello, I have decided to give up on the nm-applet after it being unable to work with WPA and WPA2 properly.  I can get it connected manually by typing commands into the terminal, so I put all these commands into a script that I have to run manually everytime I reboot my computer.  My question is:  How do I get this script to run on boot up before I even get to the GDM screen?

---

### Post by kamasabi on 2007-11-24
Load it up in your sessions?  I haven't ever tried before, but it might work

---

### Post by semperfiguy on 2007-11-24
Load it up in my sessions? what exactly does that mean? putting it in my .Xsession file?  I know it needs to be root when it runs the script because of ifdown, ifup, etc... So I was thinking somewhere in the boot process would probably be best.

---

### Post by kamasabi on 2007-11-24
Sorry, what I meant was System --> Preferences --> Sessions through the GUI and add it to your startup programs.  As far as it having to be in root, all I did was something like this (using my UT3 dedicated as an example):

```

sudo /UT3Demo/Binaries/us3demo server vCTF-Suspense .........

[password goes here]


```

Just add your password to the next line.  I have never tried adding this to my sessions before, but as far as solving the having to log in as root in a script, this worked for me.  It saves me the trouble of typing out the entire mess in the terminal.

---

### Post by jordanmthomas on 2007-11-24
put it in 
```
/etc/rc.local
```
and it will be run as root on bootup.

---

### Post by semperfiguy on 2007-11-24
Thanks, I added it to /etc/rc.local and it worked fine.

---

