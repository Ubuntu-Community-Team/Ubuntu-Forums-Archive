---
title: "Help"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by pazzyjazzy on 2008-01-27
i had a problem in upgrading my gaim to pidgin .. so the dumb side of me uninstalled few files of gaim from synaptic manager , now i dont hav gaim ,, i am getting errors in terminal and obviously i dont hav pidgin because it is asking me to download weirdass .deb files .. so if anyone has some nice easy solution please tell me asap .. thx xD

---

### Post by rhc on 2008-01-27
Go to add-remove from upper panel.(applications)
Search for Pidgin and install it.
Doesn't it work?

---

### Post by pazzyjazzy on 2008-01-27
nice idea .. but now i am having conflicts in the synaptic package manager .. i deleted 1 or 2 files .. now everything is miserable .. :( .. what to do now ?? O.o

---

### Post by rhc on 2008-01-27
[http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

Go there.
3 files.Download.
Version 2.3.1
Files   pidgin  (617.3 Kb)  ,  pidgin-data  (6.7 Mb)  ,  libpurple0  (1.5 Mb) .
Before installing them,look for them if they are in Synaptic.
If so uninstall them before.

---

### Post by stump138 on 2008-01-27
fix any issues with apt first:
```
sudo apt-get install -f
```

then you can try to fix pidgin
```
sudo apt-get install pidgin
```

---

### Post by rhc on 2008-01-27
> **rhc said:**
> [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

Go there.
3 files.Download.
Version 2.3.1
Files   pidgin  (617.3 Kb)  ,  pidgin-data  (6.7 Mb)  ,  libpurple0  (1.5 Mb) .
Before installing them,look for them if they are in Synaptic.
If so uninstall them before.

edit: Just open the files that you download or double click them.these are deb files so you shouldn't do anything more.

---

### Post by swoll1980 on 2008-01-27
try sudo apt-get install -F

---

### Post by swoll1980 on 2008-01-27
if that doesn't work do sudo dpkg configure -a

---

### Post by swoll1980 on 2008-01-27
> **rhc said:**
> edit: Just open the files that you download or double click them.these are deb files so you shouldn't do anything more.

if apt is broke the .deb will not work either

---

### Post by pazzyjazzy on 2008-01-27
i hav these files .. my frnd downloaded earlier so he gave me .. but now its asking me for other dependencies.. its becoming interesting .. lemme try this thing now .. anything else u hav in mind .. please lemmeknow .. thx xD

---

### Post by Lord Illidan on 2008-01-27
It is ```
sudo apt-get install -f
```

But first tell us exactly what the dependencies are.

---

### Post by pazzyjazzy on 2008-01-27
jazzy@jazzy-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jazzy@jazzy-laptop:~$ 


what now/? O.o :mad:

---

### Post by stump138 on 2008-01-27
have you tried 
```
sudo apt-get install pidgin
```
since you have repaired apt?

---

### Post by pazzyjazzy on 2008-01-27
LOL .. dpkg  is so confusing ..  anything easier than that ..

---

### Post by pazzyjazzy on 2008-01-27
jazzy@jazzy-laptop:~$ sudo apt-get install pidgin
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
  pidgin: Depends: pidgin-data (< 1:2.2.1-z) but 1:2.3.1-1~getdeb1 is to be installed
          Depends: libsilc-1.0-2 but it is not installable
E: Broken packages
jazzy@jazzy-laptop:~$

---

### Post by stump138 on 2008-01-27
you don't need to install pidgin for a .deb...

it is in the repositories, you can even get it from System->Administration->Synaptic Package Manager and do a search for pidgin.

---

### Post by pazzyjazzy on 2008-01-27
pidgin:
  Depends: pidgin-data (<1:2.2.1-z) but 1:2.3.1-1~getdeb1 is to be installed
 Depends: libsilc-1.0-2  but it is not installable

---

### Post by stump138 on 2008-01-27
try 
```
sudo apt-get update && sudo apt-get install pidgin-data pidgin
```

---

### Post by xeth_delta on 2008-01-27
Hope not to be intruding, pazzyjazzy, How did you try upgrading in the first place? Did you use apt-get?

---

### Post by pazzyjazzy on 2008-01-27
No idea man.......new bie in the field of linux:guitar:

---

### Post by xeth_delta on 2008-01-27
> **pazzyjazzy said:**
> No idea man.......new bie in the field of linux:guitar:

I understand, but to be able to help you we (at least I) need a bit more of information on how exactly you tried to upgrade. Did you download anything from the pidgin website?

---

### Post by xeth_delta on 2008-01-27
One more question. What version o Ubuntu are you using? 7.10 Gutsy Gibbon should have had pidgin by default.

---

### Post by hilzabub on 2008-02-12
I am experiencing the same issue.  I upgraded by replacing all instances of feisty in my sources.list to gutsy, then doing apt-get update and apt-get dist-upgrade.

The only problem I am experiencing so far is an inability to install pidgin.  Here's what I get:

stephen@saintjohn:~$ sudo apt-get install pidgin
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
The following information may help resolve the situation:

The following packages have unmet dependencies:
  pidgin: Depends: pidgin-data (< 1:2.2.1-z) but 1:2.3.1-1~getdeb1 is to be installed
          Depends: libpurple0 (>= 1:2.2.1) but it is not going to be installed
E: Broken packages



I have run apt-get install -f, apt-get -f, apt-get install -f pidgin, and every other variant I can think of that.  Same with libpurple0.  Synaptic isn't any better.

------------

Edit:  

It turns out that there was an old version of libpurple0 lurking on my box from an abortive attempt to install pidgin a month or so ago.  Doing 
sudo apt-get remove pidgin-data

followed by
sudo apt-get install -f pidgin

fixed the problem and got things working.

---

### Post by xeth_delta on 2008-02-12
> **hilzabub said:**
> I am experiencing the same issue.  I upgraded by replacing all instances of feisty in my sources.list to gutsy, then doing apt-get update and apt-get dist-upgrade.

The only problem I am experiencing so far is an inability to install pidgin.  Here's what I get:

stephen@saintjohn:~$ sudo apt-get install pidgin
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
The following information may help resolve the situation:

The following packages have unmet dependencies:
  pidgin: Depends: pidgin-data (< 1:2.2.1-z) but 1:2.3.1-1~getdeb1 is to be installed
          Depends: libpurple0 (>= 1:2.2.1) but it is not going to be installed
E: Broken packages



I have run apt-get install -f, apt-get -f, apt-get install -f pidgin, and every other variant I can think of that.  Same with libpurple0.  Synaptic isn't any better.

------------

Edit:  

It turns out that there was an old version of libpurple0 lurking on my box from an abortive attempt to install pidgin a month or so ago.  Doing 
sudo apt-get remove pidgin-data

followed by
sudo apt-get install -f pidgin

fixed the problem and got things working.

Glad to know you managed to fix it! The way you upgraded is not the recommended one, though. For more information on how to upgrade without issues, please have a look at [http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

---

