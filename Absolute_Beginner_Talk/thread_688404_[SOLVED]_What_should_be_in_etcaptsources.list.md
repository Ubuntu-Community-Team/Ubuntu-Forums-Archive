---
title: "[SOLVED] What should be in /etc/apt/sources.list?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by bw44 on 2008-02-05
I think something is missing from my /etc/apt/sources.list file.  The only uncommented lines are:```
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
```There are a lot of lines commented out, and comments which seem to refer to lines that aren't there. (I I guess it's a kind of history file as well as an active list.)

I've attached thumbnails of the Software Sources as shown in the Synaptic Package Manager and I don't see anything in sources.list about the medibuntu repository.  Can anyone tell me if the above lines are all that should be uncommented in the file or  should something be added? And how?

Thanks in advance.

PS.  I saw advice in another post about running $ sudo apt-get update to update the sources so I ran it just before I gathered the above info.

---

### Post by emarkd on 2008-02-05
There's nothing wrong with that.  You've got the official Ubuntu repositories enabled.  Some people add third-party repositories for additional software.  [Medibuntu]("http://www.medibuntu.org") is a popular one, but you don't have to add anything and you're probably safer sticking to the official software.

As for the update command, it doesn't effect your sources list.  It downloads the index from each of the repositories in your list and makes sure you have an updated local copy.  When you search for software, it actually searches the local cached list and not the remote server.

---

### Post by mikewhatever on 2008-02-05
Medibuntu is not an official repository, that's why you do not see it in sources list. It is, however, very easy to add it [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).
Post your sources list if you want help with lines. Below is mine, which should be pretty stabdard:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy restricted main
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


---

### Post by bw44 on 2008-02-05
> **emarkd said:**
> There's nothing wrong with that.  You've got the official Ubuntu repositories enabled.  Some people add third-party repositories for additional software.  [Medibuntu]("http://www.medibuntu.org") is a popular one, but you don't have to add anything and you're probably safer sticking to the official software.

As for the update command, it doesn't effect your sources list.  It downloads the index from each of the repositories in your list and makes sure you have an updated local copy.  When you search for software, it actually searches the local cached list and not the remote server.

> **mikewhatever said:**
> Medibuntu is not an official repository, that's why you do not see it in sources list. It is, however, very easy to add it [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

emarkd, and mikewhatever,

Many thanks for the quick and clear answers!  I think I understand how it works now and won't clutter up the forums with the details of my sources.list.  

Will also marked the thread solved.  (That was fast!)

bw44

---

### Post by mikewhatever on 2008-02-05
Do make sure you have more then three uncommented lines, otherwise you'll be missing a lot of software.

---

### Post by bw44 on 2008-02-05
> **mikewhatever said:**
> o make sure you have more then three uncommented lines, otherwise you'll be missing a lot of software.

Uh oh!  Here's what's in the sources.list file now on my desktop system:```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main multiverse restricted universe

```What should I add to make it > three uncommented lines?  The first line was originally added (without the #) by Synaptic when I  included the Live CD for Gutsy, but someone told me to un-check the box for the CD on the first sources tab so Synaptic wouldn't search the CD for things it should get from the repositories.  When I did un-check it, I guess Synaptic commented it out. Do  the first and third lines contain redundant info, or is the first item after the last  / in each line a modifier of the other items (main, multiverse, etc.)?

On my laptop there are many, many comment lines, but still only three uncommented ones.  Why this requirement for more than 3 lines?  Shouldn't Synaptic take care of this, or at least warn you?!?!  Any suggestions? :confused:

Thanks.

---

### Post by emarkd on 2008-02-05
Not sure what mikewhatever's referring to.  There's no limit on the number of lines you should have.  You've got all the official Gutsy repositories there.

---

### Post by bw44 on 2008-02-05
> **emarkd said:**
> Not sure what mikewhatever's referring to.  There's no limit on the number of lines you should have.  You've got all the official Gutsy repositories there.

Whew! That's all right then!  Thanks very much for letting me know.

bw44

PS.  I found several pages in the Ubuntu Community documentation just now that helped answer my other questions about the repositories (though some of the screen shots don't match what you see in Gutsy).  Here are a couple of URLs in case anyone following this thread hasn't seen them:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)

---

