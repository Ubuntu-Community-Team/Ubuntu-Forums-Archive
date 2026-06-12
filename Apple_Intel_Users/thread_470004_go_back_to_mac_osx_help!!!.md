---
title: "go back to mac osx help!!!"
date: 2007-06-10
forum: Apple Intel Users
---

### Post by reem on 2007-06-10
Im new to ubunto so downloaded it and installed it on my macbook and i believe that in the pertition part i didnt seperated it to osx and ubunto and now its impossible to get back to osx.
if someone knows how i can get back to osx and still save my files i would like to hear  about it thanks

---

### Post by gilgongo on 2007-06-10
Did you back up your stuff off the OSX install before you did this? If so, it may be easier simply to re-install from scratch.

---

### Post by reem on 2007-06-10
no i didnt backup anything is there any possibility to do it via the ubuntu?

---

### Post by gilgongo on 2007-06-10
So you have Ubuntu running? If so, can you show me what you get if you open a terminal and type:

df -h

---

### Post by reem on 2007-06-10
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 491M   33M  458M   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 491M   33M  458M   7% /lib/modules/2.6.20-15-generic/volatile
varrun                491M  100K  491M   1% /var/run
varlock               491M     0  491M   0% /var/lock
udev                  491M  124K  491M   1% /dev
devshm                491M     0  491M   0% /dev/shm
tmpfs                 491M  2.8M  488M   1% /tmp
/dev/sda1              71G  2.0G   66G   3% /media/disk
ubuntu@ubuntu:~$ 

this is what i got

---

### Post by gilgongo on 2007-06-10
Hm. You appear to have everything (71Gig) on one main partition (mounted on /media/disk for some reason).

Unless I've missed something, I think you have erased your OSX installation. If anyone else is reading this, can they give a second opinion on this? I may not be the expert on this.

---

### Post by reem on 2007-06-10
i really think that this is what happened. but is that means that all my files went with that?
cause if yes i will just go to disk utility on mac and erase the hard disk and reinstall. please give me your best advice on that, thanks

---

### Post by gilgongo on 2007-06-10
Well, in theory you *may* be able to access the data. Try Googleing around for a rescue disk - but I think in practice it'll be easier to simply re-install.

---

### Post by tchorix on 2007-06-11
Hi reem,

I guess you just erased your macosx partition when you installed Ubuntu. This issue has been discussed in this thread:  [http://ubuntuforums.org/showthread.php?t=460677](http://ubuntuforums.org/showthread.php?t=460677)

After trying to recover you data (I'm not sure is possible), you better reinstall macosx, resize your disc, and then install Ubuntu following this tutorial: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
Over there you will find good instructions about how to partition your disk.

cheers
Tch

---

