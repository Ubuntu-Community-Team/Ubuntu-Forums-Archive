---
title: "Help needed with upgrade..."
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by vinoloco on 2006-12-23
Hello all,

Trying to upgrade my system to the newest release...

When I issue the command:  sudo apt-get dist-upgrade    everything runs fine until I get an error which reads the following:

Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz) 404 Not Found


Anyone know what gives here?  Is there something wrong with my sources list?  Would rather not wipe out my old Ubuntu and start a fresh install...

Thanks in advance for the help.

-- vino

---

### Post by BarfBag on 2006-12-23
Hmm.  Those repositories should work.  I'm not sure what could be causing it to do that.  :-k 

I usually don't recommend upgrades.  In my opinion, it's better to start with a fresh install.  But everyone's different.

---

### Post by Sef on 2006-12-23
> Trying to upgrade my system to the newest release...

When I issue the command: sudo apt-get dist-upgrade everything runs fine until I get an error which reads the following:

Did you do this command first:  ```
sudo apt-get update
```?

---

### Post by vinoloco on 2006-12-23
Yes, I did enter the "sudo apt-get update" command and received the same "Failed to fetch..." error code in the console...

Any idea what the problem is?  Can I just ask the update manager to ignore this error and go on with the upgrade?

-- vino

---

### Post by jvc26 on 2006-12-23
Which ubuntu version are you running? If you're trying to go up 2 distros that won't work you would have to up up breezy->dapper->edgy... Have you tried replacing your sources.list at all to see whether there is just an entry on there which is invalid?
Il

---

### Post by Drakkor on 2006-12-23
If it's possible, a clean install seems to be less problematic than trying to upgrade :)

---

### Post by bigbroantonio on 2007-01-08
Have you tried disabling the frecontrib.org repos in /etc/apt/sources.list ?

Just do a 

```
sudo gedit /etc/apt/sources.list
```

and put a # in front of any lines that contain "freecontrib.org"

Save the file, and then try updating again.  It should work.

It worked for me!

Good luck :)

---

