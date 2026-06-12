---
title: "synaptic package manager dissapears"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Gill Bates on 2007-01-07
I'm new and I loaded ubuntu from the alternate cd to some old hardware.  Everything looked great as firefox, openoffice, and everything else worked great.  Then I tried to run a dvd and It told me I needed packages.  After digging around I ran the synaptic package manager.  After that the dvd still wouldn't work so I tried rebooting.  Now when I run the synaptic package manager it takes my pasword, acts like it's doing something, and then goes away.  Firefox says it's loading and then goes away also.  Terminal still works.  Any ideas?

---

### Post by taurus on 2007-01-07
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Gill Bates on 2007-01-07
That's where I was digging around earlier.  Are you suggesting that maybe I should sudo to that apt-get command or perhaps go to easyubuntu?  I don't suppose you know why firefox won't come up anymore?

---

### Post by taurus on 2007-01-07
Go with either easyubuntu or automatix.  They both work equally good especially for codecs and mulitmedia plugins.

Try to run firefox from a terminal to see what's the problem is.

```
firefox
```

---

### Post by Gill Bates on 2007-01-07
segmentation fault

---

### Post by taurus on 2007-01-07
Are you running Dapper or Edgy?  And what version of firefox do you have?

---

### Post by Gill Bates on 2007-01-07
I just installed it off of the alternative CD which I downloaded yesterday.  I couldn't use the livecd because of the age ao my hardware ( 2001 bios w/amd 800 cpu).  I do applications work on solaris but no systems and I'm brand new to linux.

---

### Post by taurus on 2007-01-07
Is that the Dapper alternate CD or Edgy alternate CD?

---

### Post by Gill Bates on 2007-01-07
dapper from here [http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

---

### Post by Gill Bates on 2007-01-07
I found this post.

[http://www.techiegroups.com/showpost.php?p=602599&postcount=3](http://www.techiegroups.com/showpost.php?p=602599&postcount=3)

Basically i moved the bin files from /var/cache/apt to /var/cache/apt/eraseme and the problem went away.  thanks.

---

### Post by taurus on 2007-01-07
If you are using Dapper, then you are probably using firefox 1.5!  See if it works if you remove and install it again.

Applications -> Accessories -> Terminal
```
sudo aptitude remove firefox
sudo aptitude update
sudo aptitude install firefox
firefox
```

---

### Post by Gill Bates on 2007-01-07
Update:  I was getting ready to chuck this mother board.  Everything, including the DVDs I burned was failing.  I kept getting segmentation errors which someone said were usually memory related so I pulled out the first dimm and moved the second dimm to it's slot.  The clouds suddenly parted and the sun started shining.  Even my DVDs started working.  Thanks all.

---

