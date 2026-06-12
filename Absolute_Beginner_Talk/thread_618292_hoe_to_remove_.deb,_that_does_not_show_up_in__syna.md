---
title: "hoe to remove .deb, that does not show up in  synaptic?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by studo77 on 2007-11-20
I installed Swiftweasel using this .deb:
swiftweasel-2.0.0.9_athlon64-64bit_ubuntu-AMD64.deb
from:
[http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=553631](http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=553631)

It does not show up in Synaptic.

How can i remove it?

The resaon is that i suspect this for messing up java in my 32bit Swiftweasel and Firefox. Those i have removed and am now intending to reinstall using the script here:
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

Any suggestions?

My guess is using dpkg, but how? I will need to know the name, just where to get it?

---

### Post by Dr Small on 2007-11-20
```
sudo dpkg -r swiftweasel
```

---

### Post by taurus on 2007-11-20
Try

```
sudo dpkg -r swiftweasel
```

---

### Post by Dr Small on 2007-11-20
> **taurus said:**
> Try

```
sudo dpkg -r swiftweasel
```
Well, at least two of us giving the same answer must mean we both know what we are talking about, or we are both fools :p

Lol.

Dr Small

---

### Post by taurus on 2007-11-20
> **Dr Small said:**
> Well, at least two of us giving the same answer must mean we both know what we are talking about, or we are both fools :p

Lol.

Dr Small

I am not sure about you but 90% of the time, I just guess so I must be a fool then.  ;)

---

### Post by studo77 on 2007-11-20
Not calling anyone fools here.

I tried yours, and it did not work.

I installed it again using the terminal, and there my name showed up. Reverse engineering, smalltime.


Ended up with:
sudo dpkg -r swiftweasel-athlon64

Otherwise, nice thread and always a fast response in here. So now i just need my bank to do something. Java works great now, exept for my bank.

---

### Post by taurus on 2007-11-20
Try using opera.  Saw this problem before.  Firefox can't connect to some bank but opera works just fine.

---

### Post by stchman on 2007-11-20
> **studo77 said:**
> I installed Swiftweasel using this .deb:
swiftweasel-2.0.0.9_athlon64-64bit_ubuntu-AMD64.deb
from:
[http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=553631](http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=553631)

It does not show up in Synaptic.

How can i remove it?

The resaon is that i suspect this for messing up java in my 32bit Swiftweasel and Firefox. Those i have removed and am now intending to reinstall using the script here:
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

Any suggestions?

My guess is using dpkg, but how? I will need to know the name, just where to get it?

Yes it will.

Bring up synaptic.  Click the Status button and then click Installed (local or obsolete).  Your Swiftweasel will be there.

Any time you install a package that is not in synaptic it will go there.

---

### Post by stchman on 2007-11-20
> **taurus said:**
> Try

```
sudo dpkg -r swiftweasel
```

He can also use:

```
sudo apt-get autoremove swiftweasel
```

apt-get will remove packages not installed through apt-get.

---

### Post by studo77 on 2007-11-20
Thanks taurus for the Opera advice. Will try it out, but i have had my bank running in previus install of Gutsy 64/Swiftweasel32. So do not know where to go right now.

As for the last two. I should have been more specific, it did not show up under local in Synaptic. I know that it should have popped up in there, but it did not.

And for the name ir is not called swiftweasel, there are numerous variations of it. Mine was Swiftweasel-athlon64

---

### Post by taurus on 2007-11-20
And you do have 64bit (or 32bit) java on your machine, right.  Make sure you have the right version of java for your browser.

---

### Post by por100pre1 on 2007-11-20
Maybe is not the case, but I know about a bank that can be accessed with Firefox for Windows under WINE but NOT with Ubuntu's Firefox.

---

### Post by studo77 on 2007-11-21
> **por100pre1 said:**
> Maybe is not the case, but I know about a bank that can be accessed with Firefox for Windows under WINE but NOT with Ubuntu's Firefox.

I have thought of going that route, it would probably work. But my bank says it is possible to use Firefox/Ubuntu.

Using Wine is a problem in 64bit Gutsy, it does not work, and i am not that hardcore in Ubuntu to get it working.

---

