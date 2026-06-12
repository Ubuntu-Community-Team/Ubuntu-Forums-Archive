---
title: "Installing in two terminals simultaneously"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by spai on 2007-12-12
Why cant I install(run sudo apt-get install <name>) in two terminals simultaneously?
I was installing something in one terminal and then I tried the following another terminal:
```
srikanth@ubuntu:~$ sudo apt-get install perl
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```
Is there a way to get around this?

---

### Post by flamelab on 2007-12-12
I think not !
The same happens when another instance of apt is running (p.ex. Synaptic or terminal aptitude )

---

### Post by Dr Small on 2007-12-12
Not that I know of, because when running one administration (dpkg) applications, it adds a lock file, to prevent 2 from running simutaneously.

To install one app, and then another, just run it like this:
```
sudo apt-get install *app1* *app2* *app3*
```

And so forth.

---

### Post by Mazza558 on 2007-12-12
Nope, there's no way around this, unless you list all the things you want to install, e.g 

> sudo apt-get install perl exaile emerald 

Would install those 3 things.

EDIT: Gah, beaten!

---

### Post by flamelab on 2007-12-12
In addition , you may add **&&** between each task

---

### Post by spai on 2007-12-12
Thanks Dr Small, that tip is really useful. I am going to exploit that a lot :)
But why would they impose such a restriction? 

@flamelab: Ya I know, synaptic + apt used to give me that trouble. But now I rarely use synaptic :)

---

### Post by CatKiller on 2007-12-12
> **spai said:**
> But why would they impose such a restriction? 

Because if they didn't, the whole thing would break. Package management is there to keep track of what you've installed, and what you've removed. If you have two instances running, each doing different things with no knowledge of the other, then there's suddenly no way to keep track of things and the whole thing becomes pointless.

---

### Post by flamelab on 2007-12-12
> **spai said:**
> Thanks Dr Small, that tip is really useful. I am going to exploit that a lot :)
But why would they impose such a restriction? 

@flamelab: Ya I know, synaptic + apt used to give me that trouble. But now I rarely use synaptic :)

Always remember to enter in the console all of the programs you want to be installed the one after the other . It is very simple .

---

### Post by spai on 2007-12-12
> **CatKiller said:**
> Because if they didn't, the whole thing would break. Package management is there to keep track of what you've installed, and what you've removed. If you have two instances running, each doing different things with no knowledge of the other, then there's suddenly no way to keep track of things and the whole thing becomes pointless.

Really? Wouldn't they be writing into a common database when they install maybe called the "already-installed" list?The processes could always lookup the latest update of "already-installed " list and decide whether it needs to install the package or not.


 OK I agree there could be a problem of multiple install if both packages require the same dependency. One could argue the problem of race happening for dependencies. But come on, that is not really a serious threat is it?

---

### Post by Dr Small on 2007-12-12
I really don't know that much about apt, and how it works and all, so there may be bigger problems then that. I don't know. You're best bet, would be to talk it over with the dev's of apt, and see what reasoning they could give for it, because I surely don't have any logical ones.

Dr Small

---

### Post by meborc on 2007-12-12
> **spai said:**
> Really? Wouldn't they be writing into a common database when they install maybe called the "already-installed" list?The processes could always lookup the latest update of "already-installed " list and decide whether it needs to install the package or not.


 OK I agree there could be a problem of multiple install if both packages require the same dependency. One could argue the problem of race happening for dependencies. But come on, that is not really a serious threat is it?

there is no point... as you are consuming still the same amount of cpu power... so why not install all with one command instead of installing stuff in two separate windows...

only time i think this could be useful is if you are making an upgrade of 50+ packages in one window and installing some new stuff in the other

but in the end, it would take as much time as doing these things one after another... and this way it is much cleaner

btw, how didn't you know about the "apt-get install pack pack2 pack3..."? most of tutorials and wikis (not to mention ubuntuguide.org) use these long one-command-installation lines... :) (no sarkasm intended... just interested that this is so badly documented)

---

### Post by spai on 2007-12-12
> btw, how didn't you know about the "apt-get install pack pack2 pack3..."? most of tutorials and wikis (not to mention ubuntuguide.org) use these long one-command-installation lines

Actually never used 'em. I know this is stupid but I have been searching for packages and installing them one at a time, all along:mad:

Thanks guys

---

### Post by meborc on 2007-12-12
> **spai said:**
> Actually never used 'em. I know this is stupid but I have been searching for packages and installing them one at a time, all along:mad:

Thanks guys

you must be the most calm person ever... i would go nuts if i would have to install things one by one

another tip:
you can install many debs together as well **sudo dpkg -i pigin.deb pidgin-data.deb** OR like this **sudo dpkg -i pidgin*** which will install all packages starting wiith pidgin (IN THAT FOLDER of course)

---

### Post by CatKiller on 2007-12-12
> **spai said:**
> Really? Wouldn't they be writing into a common database when they install maybe called the "already-installed" list?The processes could always lookup the latest update of "already-installed " list and decide whether it needs to install the package or not.


 OK I agree there could be a problem of multiple install if both packages require the same dependency. One could argue the problem of race happening for dependencies. But come on, that is not really a serious threat is it?

So both of them would have the file open at the same time? And both of them could add things at the same time? And what happens to the changes that the first instance wrote to the file when the second instance writes its changes to disk? That's exactly the kind of uncertainty that any engineer would design around.

Setting a lock file is both simple and effective. What's not to like? And if you don't like it, it is possible to set the filesystem to never create a /var/lib/dpkg/lock file, and if it ever exists to delete it immediately, but I don't really see that anyone would really want to.

---

### Post by spai on 2007-12-13
> **CatKiller said:**
> So both of them would have the file open at the same time? And both of them could add things at the same time? And what happens to the changes that the first instance wrote to the file when the second instance writes its changes to disk? That's exactly the kind of uncertainty that any engineer would design around.
Yes, that **is** serious trouble. 
> **CatKiller said:**
> 
Setting a lock file is both simple and effective. What's not to like? And if you don't like it, it is possible to set the filesystem to never create a /var/lib/dpkg/lock file, and if it ever exists to delete it immediately, but I don't really see that anyone would really want to.


I will try that sometime :idea:

---

### Post by Flare183 on 2007-12-13
Not possible the repos are locked when you try to install 2things at the same time.

---

