---
title: "Weird screen on iMacG5 when booting ibex"
date: 2008-12-22
forum: Apple Hardware Users
---

### Post by MMXGN on 2008-12-22
Hello,

I downladed the alternate install cd, and installed ubuntu on my imacG5 (revB). The problem is, that when I try to boot my newly installed system, I
get the following weird screen where my computer seems to has stopped responding.
[[IMG]http://img88.imageshack.us/img88/2817/22122008003ao1.th.jpg[/IMG]](http://img88.imageshack.us/my.php?image=22122008003ao1.jpg)
Is there anything I can do to successfully boot my newly installed ibex?

---

### Post by tiresia on 2008-12-22
Have you tried to give the option video=ofonly at the yaboot prompt?

---

### Post by MMXGN on 2008-12-22
Thanks. It now works :)

---

### Post by stream303 on 2008-12-22
That kind of looks like mine. :)

If you don't want to enter that every time you boot, be sure to put *video=ofonly* in your /etc/yaboot.conf file, and then issue

```
sudo ybin -v
```

to make the system aware of the change.  I don't like the splash screen, so I also use *nosplash*

CPU frequency scaling - if you want to save some power and heat, be sure to fix powernowd script as seen about half-way down the page here:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

or just use cpudyn instead.

That looks like an early model like mine.  If that is one that doesn't have any als (automatic light sensor) or isight camera, and is just plain with an nvidia geforce video card, know that there will be a slight shift in the video to the right by about half-inch.  This is due to the driver that affects all current ppc distros - it isn't ubuntu specific.  Just wanted to let you know so you don't go tearing out your hair trying to fix it with the usual techniques. :)  If it truly bothers you, Debian Etch 4.0r5 "stable" uses an older X driver that doesn't exhibit this problem.

These G5 iMacs make for pretty nice Linux ppc boxes for sure.

---

### Post by MMXGN on 2008-12-23
Thanks for the info.
Installed successfully interpid. But the lack of available applications
kinda bothers me, so I am now installing debian 4.0r6.

---

### Post by tiresia on 2008-12-23
I would try Debian Lenny. 
You can download it here:
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)
For a personal desktop use it is more than 'stable' (in common sense), and you can get newer software.

---

### Post by stream303 on 2008-12-23
Lenny is awesome, but on my 20" G5 iMac with nvidia, he wont encounter the video shift bug coming from freedesktop.org that affects all recent ppc distros on that model if he tries Etch first.  (the problem is in the driver itself, not any configuration issue)

It is easy enough to switch to Lenny once he gets a taste for it. :)  Or do what I did - dual boot!

---

### Post by cyberdork33 on 2008-12-24
> **MMXGN said:**
> Thanks for the info.
Installed successfully interpid. But the lack of available applications
kinda bothers me, so I am now installing debian 4.0r6.
? Any software available for debian should be available to Ubuntu...

---

### Post by stream303 on 2008-12-24
Forgot to mention - With Ubuntu, it is normal for the G5's fans to scream at full blast during installation - after the first reboot, they will calm down.

That's another thing about Debian - the fans are under control during installation for G5's, and they don't mess about with a splash-screen, which can cause problems with Ubuntu unless one knows about these things beforehand. :)

---

