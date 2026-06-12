---
title: "cant remove kubuntu"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Miroku on 2007-05-12
i wanted to see how kubuntu looks so i followed this guide at:

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

now, i want to remove it but the command to remove is not really doing anything.

this:

```
sudo aptitude remove kubuntu-desktop
```

leads to:

```

***@ubuntu:~$ sudo aptitude remove kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

any help would be appreciated. thanks. and btw, i am using edgy.

---

### Post by taurus on 2007-05-12
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Miroku on 2007-05-12
mannnn -- i did not want to have to use that -- but i guess no other option. thanks.

---

### Post by oilchangeguy on 2007-05-12
in the future if you want to check out another look/distro, simply create a live cd of the version with that look and run the computer from the cd. that way no changes will be made to your present setup.

---

### Post by taurus on 2007-05-12
You don't have to type that whole thing into a terminal.  Just do the cut 'n paste.  Cut with the left button and paste with the middle button or both left and right at the same time if you only have two-button mouse.

---

### Post by Campingman on 2007-05-12
I am sure you have seen this but just in case this one is for edgy
[http://www.psychocats.net/ubuntu/puregnomeedgy](http://www.psychocats.net/ubuntu/puregnomeedgy)

---

### Post by ajgreeny on 2007-05-12
If you had used aptitude to install the **kubuntu-desktop** you could have easily removed everything that was installed by uninstalling with aptitude as well.  Not much help this time, but worth remembering in future if you want to try **xubuntu-desktop**, for example.  I suppose you could use aptitude now to reinstall kubuntu-desktop again, and then quickly uninstall it again with aptitude.  I don't know for certain, but I can't see why that wouldn't work.  Give it a try and let us know.

---

### Post by Miroku on 2007-05-15
hmmm .. i thought i did install it using aptitude -- am i mistaken?

and what is the point of xubuntu? -- havent done any research on it at all.

and taurus .. yea, lol, i didnt mean i would have type all of this out, i just meant i did not want to enter all those commands because it removed some programs that i wanted to keep (like amarok)

yea, using that long command, everything is back to normal.

---

