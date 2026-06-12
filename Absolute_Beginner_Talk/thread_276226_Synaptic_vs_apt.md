---
title: "Synaptic vs apt"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2006-10-12
I notice a lot of threads that suggest using apt rather than suggesting synaptic is there a difference between the way the install or uninstall?

---

### Post by aysiu on 2006-10-12
No big difference between *apt-get* and Synaptic.

But there is a difference with *aptitude*:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by cjnkns on 2006-10-12
Hmm interesting I didn't realize that. 

Thanks!

---

### Post by sbassett on 2006-10-12
> **cjnkns said:**
> I notice a lot of threads that suggest using apt rather than suggesting synaptic is there a difference between the way the install or uninstall?


Your best bet would be to drop to command line

```
 CTRL + ALT + F1 
```

and run

```
 sudo /etc/init.d/gdm stop 
```

and then

```
 sudo aptitude dist-upgrade 
```

after logging in.  After this process has completed reboot your pc.

```
 sudo shutdown -r now 
```

---

### Post by velle on 2006-10-16
To sbassett:

Sorry but I do not really get the point of any of what you are replying could you please explain:

[LIST]
[*]What does "CTRL + ALT F1 do"? On my Ubuntu nothing happens.
[*]What does this do "sudo /etc/init.d/gdm stop" ?
[*]And what does all this help?
[/LIST]

Thomas Wessel

---

### Post by CatKiller on 2006-10-16
> **cjnkns said:**
> I notice a lot of threads that suggest using apt rather than suggesting synaptic is there a difference between the way the install or uninstall?

The main reason that people suggest terminal commands rather than use of the GUI is because it's much more concise. If you give someone a command, they can paste it into a terminal without having to interpret it too much, and it's only going to be three words or so. To explain the same process with a GUI, it's all "Click on System, click on Administration, click on the thing that looks like a wobbly fish... no, the blue one..." which is more than three words and might not even work.

And, as aysui says, aptitude handles uninstallation of dependencies much more cleanly.

---

### Post by dannyboy79 on 2006-10-16
ctrl + alt F1 is suppose to bring up a quick command line interface i believe. he suggests this instead of having to go up to applications, then accessories, then terminal, then type in the sudo /etc/init.d/gdm stop which i think will stop graphic interface? which I agree with you, is pointless, you can do a sudo aptitude dist-upgrade without shutting down gdm without any negative effects! also, From the man-page:

dist-upgrade, in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages"

Well, if you want to do a distro-upgrade, use dist-upgrade. For instance, moving from Debian -stable to Debian -testing. Dist-upgrade is a special upgrade that is used if you are fetching packages from a new location, which is specified in /etc/apt/sources.list

If you want to simply upgrade the packages you have installed for your current distro, use 'apt-get or aptitude upgrade'.

i could be wrong on what gdm stop does.

---

### Post by sbassett on 2006-10-31
Apologies. I was merely sharing those suggestions that I have heard regarding dropping to console CTRL+ALT+F1). It seems I had omited a + in my original thread. Also, /etc/init.d/gdm stop halts the X server (I was much more accustomed to the 'inti 3' command back in the day). This would lower your total processes running. And as I stated, this is merely from other well wishers and I am passing this along.

---

### Post by devilsadvocate1987 on 2006-10-31
dist-upgrade is more aggressive than just upgrade in adding and dropping packages. Sometimes when the changes are more overarching and affect multiple packages, requiring perhaps significant changes in the dependancies, then a dist-upgrade is more likely to be able to handle it.

---

