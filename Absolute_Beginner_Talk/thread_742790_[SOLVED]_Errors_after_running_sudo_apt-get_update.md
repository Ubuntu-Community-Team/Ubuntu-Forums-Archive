---
title: "[SOLVED] Errors after running sudo apt-get update"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-04-02
Hello everyone,

after running a *sudo apt-get update* in terminal I got the following error (end of the string):

[I]Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources
Fetched 53.8kB in 15s (3583B/s)
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz)  Hash Sum mismatch
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/gutsy/non-free/source/Sources.gz)  Hash Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
XXXXl@al-Adab:~$[/I]

Any idea? Thanks!

---

### Post by Oldsoldier2003 on 2008-04-02
> **al.adab said:**
> Hello everyone,

after running a *sudo apt-get update* in terminal I got the following error (end of the string):

[I]Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources
Fetched 53.8kB in 15s (3583B/s)
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz)  Hash Sum mismatch
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/gutsy/non-free/source/Sources.gz)  Hash Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
XXXXl@al-Adab:~$[/I]

Any idea? Thanks!

looks like you had a dirty connection or the archive lists are corrupt. I'm betting more on the former than the latter. try running sudo apt-get update again and maybe change your download source if the errors persist.

---

### Post by al.adab on 2008-04-02
Thanks. I tried again and got the same error - don't know what you mean by "dirty" connection? :)
How can I change my download source?

---

### Post by kellemes on 2008-04-02
> **al.adab said:**
> Thanks. I tried again and got the same error - don't know what you mean by "dirty" connection? :)
How can I change my download source?

Silly test..
Can you try the following please?
```
sudo aptitude update
```

---

### Post by wormser on 2008-04-02
> **al.adab said:**
> How can I change my download source?

System> Administration> Software Sources: Download from:

---

### Post by al.adab on 2008-04-02
Tried to run *sudo aptitude update* and got no error. Does this mean I should preferably run this command in the future (instead of [I]sudo apt-get update[/I)?]

---

### Post by Oldsoldier2003 on 2008-04-02
> **al.adab said:**
> Thanks. I tried again and got the same error - don't know what you mean by "dirty" connection? :)
How can I change my download source?

If you are on a slow link or modem sometimes a bad connection messes up your data. Data problems can also come from outher bits of wuipment failing along the way as well.  Its much more likely than one of the archives having corrupt packages as I'm sure we would have more reports by now.

to change your download source:
Administration>Software Sources
on the first tab change the "download from: " to another server

---

### Post by Oldsoldier2003 on 2008-04-02
> **al.adab said:**
> Tried to run *sudo aptitude update* and got no error. Does this mean I should preferably run this command in the future (instead of [I]sudo apt-get update[/I)?]

thats strange because they both draw from the same sources... try running apt again and if you get the errors i would consider filing a bug report on it.

---

### Post by kellemes on 2008-04-02
> **al.adab said:**
> Tried to run *sudo aptitude update* and got no error. Does this mean I should preferably run this command in the future (instead of [I]sudo apt-get update[/I)?]

Well, if it works, it works.. I'm just not sure it does.. it seems apt-get has an issue with the hash sum and aptitude doesn't..
It seems these bug-reports are related..
[https://bugs.launchpad.net/ubuntu/+source/apt-mirror/+bug/130813]("https://bugs.launchpad.net/ubuntu/+source/apt-mirror/+bug/130813")
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/208863]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/208863")

You can use aptitude if it works..
or remove the 2 repositories from the sources list.. for now anyway..

---

### Post by al.adab on 2008-04-02
I run the "choose the best server option" + tested other two servers as well as the the "main server" (original settings). In all cases I get the following message after reloading: 

[I]COULD NOT DOWNLOAD ALL REPOSITORIES INDEXES
[http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz:](http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz:) Hash Sum mismatch
[http://packages.medibuntu.org/dists/gutsy/non-free/source/Sources.gz:](http://packages.medibuntu.org/dists/gutsy/non-free/source/Sources.gz:) Hash Sum *mismatch*[/I]

As for a)  *sudo apt-get update[/I and b) [I]sudo aptitude update *: 

a) following error message: 

[I]Hit [http://ubuntu.fastbull.org](http://ubuntu.fastbull.org) gutsy-backports/restricted Sources              
Fetched 11B in 10s (1B/s)                                                      
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz)  Hash Sum mismatch
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/gutsy/non-free/source/Sources.gz)  Hash Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
XXXX@al-Adab:~$ [/I]

b) no error message. 

Anything I should do or worry about?

---

### Post by kellemes on 2008-04-02
> **al.adab said:**
> I run the "choose the best server option" + tested other two servers as well as the the "main server" (original settings). In all cases I get the following message after reloading: 

[I]COULD NOT DOWNLOAD ALL REPOSITORIES INDEXES
[http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz:](http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz:) Hash Sum mismatch
[http://packages.medibuntu.org/dists/gutsy/non-free/source/Sources.gz:](http://packages.medibuntu.org/dists/gutsy/non-free/source/Sources.gz:) Hash Sum *mismatch*[/I]

As for a)  *sudo apt-get update[/I and b) [I]sudo aptitude update *: 

a) following error message: 

[I]Hit [http://ubuntu.fastbull.org](http://ubuntu.fastbull.org) gutsy-backports/restricted Sources              
Fetched 11B in 10s (1B/s)                                                      
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz)  Hash Sum mismatch
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/gutsy/non-free/source/Sources.gz)  Hash Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
XXXX@al-Adab:~$ [/I]

b) no error message. 

Anything I should do or worry about?

Do you have any specific reason to use the medibuntu repositories?

---

### Post by al.adab on 2008-04-02
*Do you have any specific reason to use the medibuntu repositories?*

well...I suppose I do, just now I really can't remember what I need them for, I suppose media software? Just can't remember...

---

### Post by al.adab on 2008-04-02
So can we say that I can just ignore this error message and hope it magically disappears by itself or is there anything in your opinion I should do now/in the future or the error message doesn't really matter altogether...and yes, now I recall being asked to download the medibuntu reps, so I suppose I do need them. Thanks

---

### Post by kellemes on 2008-04-02
> **al.adab said:**
> So can we say that I can just ignore this error message and hope it magically disappears by itself or is there anything in your opinion I should do now/in the future or the error message doesn't really matter altogether...and yes, now I recall being asked to download the medibuntu reps, so I suppose I do need them. Thanks

Yes, I'd hope (and assume) this issue will magically disappear since it seems to be a reported bug.
I'd use aptitude instead.. or synaptic (assuming this will work with the medibuntu repo).

You can use aptitude almost the same as apt-get..
```
sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude install X
sudo aptitude remove X
```

Let us know if you keep having problems with this..

---

