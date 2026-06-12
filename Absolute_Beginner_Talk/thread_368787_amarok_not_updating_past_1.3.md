---
title: "amarok not updating past 1.3"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by kaboom on 2007-02-23
Hey all,
This is probably going to be a very easy fix, but i'm fairly inexperienced with linux so i dont know how to go about it.  i'm on dapper have amarok 1.3.  i'm trying to update it to 1.4 but when i use 'sudo apt-get install amarok' it says its allready the newest version.  

side question about amarok:  i had it setup before a reinstall so that it would stream last.fm channels.  i dont remember if that was standard for 1.4 or if i got a plugin somewhere that enabled that.  if its not standard could someone tell me where to find that capability again?

thanks in advance for help on any part of these questions
chris

---

### Post by nickoli_02 on 2007-02-23
The newest version of Amarok may be 1.4, but it may not have been put in the repositories yet. If you really want the latest version of Amarok, you could compile it yourself... but why bother :D there probably isn't that big of a difference between the two versions.

Edit: Also make sure you run sudo apt-get update before trying to upgrade packages. This refreshes the list of what's new in the repositories with regards to what's on your system... something like that, lol

---

### Post by kaboom on 2007-02-23
thanks for the quick reply.  i am looking to upgrade if the last.fm stream option comes with 1.4;  if they dont then i'm happy with 1.3 and i'll try to figure out what i did last time to get them.

---

### Post by r4ik on 2007-02-23
Have a look at,

[http://kubuntu.org/announcements/amarok-1.4.3.php](http://kubuntu.org/announcements/amarok-1.4.3.php)

Good luck !

---

### Post by kaboom on 2007-02-23
> **r4ik said:**
> Have a look at,

[http://kubuntu.org/announcements/amarok-1.4.3.php](http://kubuntu.org/announcements/amarok-1.4.3.php)

Good luck !


ok that at least changed the problem - which i consider progress.  now on sudo apt-get install amarok i get this output:
kaboom@kaboom-laptop:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: libifp4 but it is not installable
          Depends: libvisual-0.4-0 (>= 0.4.0) but it is not installable
E: Broken packages

thanks to all for the suggestions so far

---

### Post by Bachstelze on 2007-02-23
Yes, certainly. Did you add the line to your sources.list and the key ? Did you run *apt-get update* ?

---

### Post by kaboom on 2007-02-23
> **HymnToLife said:**
> Yes, certainly. Did you add the line to your sources.list and the key ? Did you run *apt-get update* ?

i added the line to sources.list and ran the update, but i dont think i added a key anywhere.  how should i do that?

---

### Post by Bachstelze on 2007-02-23
>  wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
 sudo apt-key add kubuntu-packages-jriddell-key.gpg

You will get a message "OK" (you may also get a warning about no ultimately trusted keys found)

You also need to enable the Dapper backports.

---

### Post by kaboom on 2007-02-23
> **HymnToLife said:**
> You also need to enable the Dapper backports.

ok i did use the wget and sudo lines, i didn't know thats what you were referring to.  would those lines enable the backports or would i need to do something else for that?  sorry for the remedial questions.

---

### Post by Bachstelze on 2007-02-23
```
sudo nano /etc/apt/sources.list
```

You should have two lines with a URL and *dapper-backports* in them. Uncomment them - that is, remove the # before them - and run *apt-get update* again.

---

### Post by kaboom on 2007-02-23
ok it seems like i'm getting closer each time.  the only error i'm still getting with 'sudo apt-get install amarok' is:

kaboom@kaboom-laptop:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: libifp4 but it is not installable
E: Broken packages
kaboom@kaboom-laptop:~$



i looked around for somewhere to get libifp4 but couldn't seem to find it. hopefully this is the last kink to iron out.

cheers

---

### Post by r4ik on 2007-02-24
If you enabled the Dapper backports like Hymntolife suggested, reload Synaptic
libifp4 should be there.

libifp4 allows you to communicate with iRiver iFP audio devices. It
provides a high-level interface to upload and download files to and
from the device, as well as other functions like battery status and
firmware updating.

---

### Post by kaboom on 2007-02-24
thanks for everyone's help.  i solved the problem: for anyone else that find themself with it i went into synaptic,  chose settings > repositories>  +add.   then just added all of the channels and amarok updated itself about a minute later.  
hope this helps someone and again i appreciate everyone posting.
chris

---

