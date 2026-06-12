---
title: "Application install issues"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by KeithO on 2005-10-09
I just installed Ubuntu last week after reading all the rave reviews about it.  I got things running pretty easily however I'm now trying to get the similar programs I had on Windows running here. However when installing programs, I keep getting this error message:
> W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
This is greek to me so could someone help me figure this out.  

Thanks.

---

### Post by Wolki on 2005-10-09
[QUOTE=KeithO]I just installed Ubuntu last week after reading all the rave reviews about it.  I got things running pretty easily however I'm now trying to get the similar programs I had on Windows running here. However when installing programs, I keep getting this error message:
[/QUOTE]

The hoary-backports on mirrormax do not exist anymore. (long story). You can fix this error by opening your sources.list (sudo gedit /etc/apt/sources.list) and removing each line that contains "hoary-backports" *and* "mirrormax". You don't need to remove the lines that contan mirrormax and hoary-extras as those are still up.

---

### Post by darkmatter on 2005-10-09
[QUOTE=KeithO]I just installed Ubuntu last week after reading all the rave reviews about it.  I got things running pretty easily however I'm now trying to get the similar programs I had on Windows running here. However when installing programs, I keep getting this error message:

This is greek to me so could someone help me figure this out.  

Thanks.[/QUOTE]

Keitho, Backports have become an official project, and are being hosted on the official servers. All you need to do is change the reference to Backports in /etc/apt/sources.list to the following
```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
```

You may leave the reference to hoary-extras untouched, as they are still hosted on mirrormax.

---

### Post by KeithO on 2005-10-09
great.  that almost did the trick.  now when i do "sudo apt-get install sun-j2re1.5" (without the quotes of course, I'm shown, "E: Couldn't find package sun-j2re1.5".  I get the same for Azureus.  

Also could you double check my souces.list file to make sure the problem isn't there. 

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse


Thanks again.  You guys rock.

---

### Post by darkmatter on 2005-10-09
Your sources.list looks fine, but you should add
```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
```
and

```
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

I believe that is why you cannot find Azureus. As for sun-j2re1.5. It has been removed from the repos. (I can't remember theexact reason, but I believe it had to do with Sun having a fit)

To get Java 1.5 working, try [http://www.ubuntuforums.org/showthread.php?t=70428&highlight=Java](http://www.ubuntuforums.org/showthread.php?t=70428&highlight=Java)

---

### Post by KeithO on 2005-10-09
Great thanks alot.  I appreciate it.  I'm having issues with the java install which I'll post about in that thread.

---

### Post by Perfect Storm on 2005-10-10
Here's how you install java: [http://www.ubuntuforums.org/showthread.php?t=70428](http://www.ubuntuforums.org/showthread.php?t=70428)

---

