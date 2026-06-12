---
title: "cant install awn dock"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by irunwithknives on 2008-02-14
I  go through all the proper installation procedures, and it even shows in my Applications-Accessories menu, yet doesnt do anything

---

### Post by emarkd on 2008-02-14
There are lots of ways to install AWN.  Which did you use?  [This]("http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository") is probably the best method.

By the way, AWN requires a compositing manager like Compiz.  Is Compiz working?

---

### Post by irunwithknives on 2008-02-14
> **emarkd said:**
> There are lots of ways to install AWN.  Which did you use?  [This]("http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository") is probably the best method.

By the way, AWN requires a compositing manager like Compiz.  Is Compiz working?

yeah, im using Gusty

---

### Post by emarkd on 2008-02-14
ok, but is Compiz working?  and you kinda skipped over my first question... ;)

If nothing else, go to the Terminal and try and start it.  At least you'll get some error output.

```
avant-window-navigator
```

---

### Post by irunwithknives on 2008-02-14
I did this, and this came up with synaptic

avant-window-navigator-bzr:
 Depends: libawn-bzr but it is not going to be installed
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed
 Depends: libawn-bzr but it is not going to be installed

---

### Post by irunwithknives on 2008-02-14
when I do that, it says

irunwithknives@sh:~$ avant-window-navigator
Segmentation fault (core dumped)

---

### Post by irunwithknives on 2008-02-14
ps.
I used that one once, then tried a couple others

---

### Post by emarkd on 2008-02-14
> **irunwithknives said:**
> when I do that, it says

irunwithknives@sh:~$ avant-window-navigator
Segmentation fault (core dumped)

Well there's your problem ;)  So how did you install this?  Did you compile it from the source?  Did you download a .deb from somewhere?  Did you follow the guide I gave you and installed it through Synaptic?

---

### Post by irunwithknives on 2008-02-14
well, I tried the thing you gave me a long time ago, but it didnt work.

Then I tired the compiler
which also didnt work

Then I tried urs again, and it still didnt work

---

### Post by emarkd on 2008-02-14
Can you be more specific?  Didn't work doesn't give us much to go on... ;)

The tutorial I linked to should work.  If you can narrow down your problem a bit, maybe we can get it going for you.

---

### Post by irunwithknives on 2008-02-14
well, im pretty ignorant about this stuff

but it says I need more things that arent there

Depends: libawn-bzr but it is not going to be installed
Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed
Depends: libawn-bzr but it is not going to be installed

is exactly what it says when I do the synaptic install

---

### Post by emarkd on 2008-02-14
Well, I don't know why that is.  Lets try installing the dependencies separately before installing AWN.

Run:

```
sudo apt-get install libawn-bzr
sudo apt-get install libpango1.0-0

```

Those are separate commands.  Run each one, then try installing AWN again.

```
sudo apt-get install avant-window-navigator-bzr
```

---

### Post by irunwithknives on 2008-02-14
Doesnt really work...


irunwithknives@sh:~$ sudo apt-get install libawn-bzr
[sudo] password for irunwithknives:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libawn-bzr: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
E: Broken packages
irunwithknives@sh:~$ sudo apt-get install libpango1.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpango1.0-0 is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++5 libkiten1 unixodbc odbcinst1debian1 gcc-3.3-base gnujump-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
irunwithknives@sh:~$ sudo apt-get install avant-window-navigator-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr158-1) but it is not going to be installed
E: Broken packages
irunwithknives@sh:~$

---

