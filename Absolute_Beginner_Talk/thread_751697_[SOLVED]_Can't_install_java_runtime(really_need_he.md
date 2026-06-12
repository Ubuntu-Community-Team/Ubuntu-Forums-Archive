---
title: "[SOLVED] Can't install java runtime(really need help!)"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by mstrchfmjolnirty on 2008-04-10
Hey everyone, I'm fairly new to Ubuntu...and Linux for that matter, earlier this afternoon I was working on installing a p2p client such as Limewire or  Frostwire...I realize that both are built on the same Java Runtime engine but as I installed Limewire I got all the way to the step where it installs the Java Runtime, it froze at about 50% and I let it sit for about 30 minutes to no result...so I restarted the  machine and tried to install Java Runtime 1.5 on its own from Add/Remove Programs...this came up with an error stating:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

So I went to terminal and didn't really know what to do with the menu that came  up from "sudo dpkg --configure -a" So I tried to simply install both 1.5 and 1.6 from the terminal with:

> sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin

and it came up with the same error....

I am so  lost right now, any help is greatly appreciated!

---

### Post by ferdostar on 2008-04-10
What gave you ```
sudo dpkg --configure -a
```
EDIT: I suppose you did it, but have you checked that the multiverse repository enabled?
EDIT2: In fact it's not necessary to double post ([http://ubuntuforums.org/showthread.php?t=751589](http://ubuntuforums.org/showthread.php?t=751589))  If somebody can help, it will do it ;)

---

### Post by mstrchfmjolnirty on 2008-04-10
basically it came up as an error i posted it as the attachment, when i tried this it failed and another user said to add sudo...

---

### Post by ferdostar on 2008-04-10
Have you tried to run it manually? 
1) Open a terminal (Accessories -> Terminal)
2) Type ```
sudo dpkg --configure -a
```
and see what is going then.

---

### Post by mstrchfmjolnirty on 2008-04-10
I did that but its just a help menu...I don't really know where to go  with  it from there...

---

### Post by ferdostar on 2008-04-10
What do you mean it's a help menu?
Have you enabled all repositories (System>administration>software properties) and updated your system ```
sudo aptitude update && sudo aptitude upgrade
``` 
Can you post please the output of ```
sudo dpkg --configure -a
```

---

### Post by mstrchfmjolnirty on 2008-04-10
Hmm, when I entered the first code you put in it put up that same error...it seems  that when I try to install anything I get this...the out put of that changed though here it is:


> Setting up java-common (0.26ubuntu1) ...



Setting up odbcinst1debian1 (2.2.11-16) ...



Setting up unixodbc (2.2.11-16) ...



Setting up gcc-3.3-base (1:3.3.6-15ubuntu2) ...

Setting up libstdc++5 (1:3.3.6-15ubuntu2) ...



Processing triggers for libc6 ...

ldconfig deferred processing now taking place

---

### Post by ferdostar on 2008-04-10
1) Have you enabled all the repositories and then run the update and upgrade? 
2) Have you tried to install java runtime?
```
sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```
* you can change 5 to 6 to install java 1.6
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by mstrchfmjolnirty on 2008-04-10
I believe all repositories are enabled and I went in and there were 2 under 3rd party that were not checked so I checked them and it said something about being out of date so it updated and gave me the same error that this problem began with although I just restarted the machine and java runtime just installed perfectly I believe...

---

### Post by ferdostar on 2008-04-10
> **mstrchfmjolnirty said:**
> I believe all repositories are enabled and I went in and there were 2 under 3rd party that were not checked so I checked them and it said something about being out of date so it updated and gave me the same error that this problem began with although I just restarted the machine and java runtime just installed perfectly I believe...

That's good! Now, rest to mark the thread as solved and have fun :)

---

### Post by mstrchfmjolnirty on 2008-04-10
Sweet thank you soo much!

---

