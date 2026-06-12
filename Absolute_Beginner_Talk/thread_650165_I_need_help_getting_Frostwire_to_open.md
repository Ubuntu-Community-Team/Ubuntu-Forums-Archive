---
title: "I need help getting Frostwire to open"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Mifune41 on 2007-12-26
I just installed it from their website, but when I click on the launcher nothing happens. 

Any help?

---

### Post by mdpalow on 2007-12-26
Did you install Java 6? Frostwire needs Java to run.

---

### Post by frup on 2007-12-26
type frostwire in terminal and you should see the error message it spews out... as mdpalow said, it is most likely that you need java.

---

### Post by Mifune41 on 2007-12-26
After typing frostwire in to the terminal I got the following: 

[I]Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
[/I]

How do I upgrade Java?

---

### Post by GSF1200S on 2007-12-26
Open up the Add/Remove programs application and do a search for Java.

Install "Ubuntu restricted extras" and Sun Java 6 Runtime- you are on 32bit Ubuntu, right? This is a little trickier on 64bit... Post the error message if this doesnt fix it for you...

---

### Post by barbedsaber on 2007-12-26
And when/if it works, can you please mark the thread as solved.

---

### Post by Mifune41 on 2007-12-26
> **GSF1200S said:**
> Open up the Add/Remove programs application and do a search for Java.

Install "Ubuntu restricted extras" and Sun Java 6 Runtime- you are on 32bit Ubuntu, right? This is a little trickier on 64bit... Post the error message if this doesnt fix it for you...

I already have Ubuntu restricted extras installed, but I don't see Sun Java 6 Runtime; but I do have Sun Java 5 Runtime installed, if that changes anything.   

how do I find out if I'm on a 32bit?

---

### Post by GSF1200S on 2007-12-26
> **Mifune41 said:**
> I already have Ubuntu restricted extras installed, but I don't see Sun Java 6 Runtime; but I do have Sun Java 5 Runtime installed, if that changes anything.   

how do I find out if I'm on a 32bit?

Could you post screenshots of what you have installed, as ive done for an example? That way, I know what you have...

To find out if your 64bit, check the results of:

```
uname -a
```

I am on 64 bit, so my printout is as follows:(notice the bold)

```
Linux hybrid 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 **x86_64 GNU/Linux**

```

---

### Post by Mifune41 on 2007-12-26
I'm guessing this means I'm not on a 64 bit:

```
 Linux main-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux 
```

---

### Post by GSF1200S on 2007-12-26
> **Mifune41 said:**
> I'm guessing this means I'm not on a 64 bit:

```
 Linux main-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux 
```

What if you click on the 'other' section of the add/remove programs?? It should be in there- make sure apt is up to date (you must have add/remove closed to do this) by putting in a terminal:

sudo apt-get update

I see that same Java 5 Runtime but its under the Internet section. You need the Java 6 runtime under the 'other' section. Post a screenshot of other if its not there? Are you using the default sources for your repos? Im not sure if this is necessary, but are all repos enabled??

---

### Post by Mifune41 on 2007-12-26
I did the "sudo apt-get update" as you said, but I'm still not seeing Java 6 runtime anywhere(see attachment).

> **GSF1200S said:**
>  Are you using the default sources for your repos?

I'm not sure, how would I find out?

>  Im not sure if this is necessary, but are all repos enabled??

Again, how do I find out?



(Jeez, if you end up helping me resolve this situation, I don't think a simple 'thanks' would be enough in return)

---

### Post by GSF1200S on 2007-12-26
> **Mifune41 said:**
> I did the "sudo apt-get update" as you said, but I'm still not seeing Java 6 runtime anywhere(see attachment).



I'm not sure, how would I find out?



Again, how do I find out?



(Jeez, if you end up helping me resolve this situation, I don't think a simple 'thanks' would be enough in return)

Its kind of hard to explain the GUI way, as im used to Adept and KDE... The easiest way is for you to post the full contents of the following file:

```
gedit /etc/apt/sources.list
```

If nothing comes up but an empty file, throw 'sudo' in front of that.. then post that here. Sun Java 6 should be there (in add/remove programs).. If its not, then it must be that all your repos are not available..

If nothing else, well get the java 6 RE from the website and compile it from source.. its not too hard.

Hey, thats what the forums are for- Ive asked plenty of questions! Thats the perks of OSS... ;)

---

### Post by Mifune41 on 2007-12-26
Here's everything from sources.list:

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by Sef on 2007-12-26
> I already have Ubuntu restricted extras installed, 

Applications > Add/Remove > Change the top right box to 'All Available Applications' > Search > Sun Java 6 > choose the top option > Apply > Apply > OK

---

### Post by GSF1200S on 2007-12-26
> **Sef said:**
> Applications > Add/Remove > Change the top right box to 'All Available Applications' > Search > Sun Java 6 > choose the top option > Apply > Apply > OK

Hopefully this works, but it appears Sef that it says "All Available Applications?" Maybe im missing what you are saying as im on KDE..

It does appear you are missing some of the multiverse repos in your sources.list- Im going to post mine, and any lines you see missing (namely multiverse) you should put in your own sources.list- You are missing sources and that is why we cant find Java 6 JRE. Youll have to be root (sudo) to modify the sources.list-

Make sure you run:

```
sudo apt-get update
```

after you add the missing lines...
 
> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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

Alternatively, you can paste my sources.list content in place of your sources.list content (save a copy of your own content) and run apt-get update- this should show you all available packages in the add/remove programs...

---

### Post by GSF1200S on 2007-12-26
And if this doesnt work, try this command, and then post what the terminal says:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

It should also be noted you are on 32bit, so the top part of my sources.list is for 64bit.. Youll need to change that to how your sources.list reads... Im sorry if this is sounds so complicated.. thats my fault :(

---

