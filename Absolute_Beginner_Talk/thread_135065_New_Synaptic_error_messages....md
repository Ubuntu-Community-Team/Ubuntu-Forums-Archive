---
title: "New Synaptic error messages..."
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-02-23
The last two accesses of Synaptic produced the following:

   	 	 	 	 	 	 	 	  
> W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
 W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
 W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
 W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
 W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
 W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
 W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
 W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
 

I do not recall making any changes to anything that would produce this.  Does anyone know how I might fix this?

-thx

---

### Post by Zimmer on 2006-02-23
Usually this means your computer cannot connect to the sources over the net.
Either your connection to the net is down, or the sources are offline. This happens periodically, I have noticed. 
Check you have the modem/router switched on (I have looked a fool in the past for trying to get a package and then realising the router was unplugged !) and it can connect to a web address. If you still cannot stat the packages it is the sources that are offline...

Regards

ps, they seem to be online now...

---

### Post by Cousindaddy on 2006-02-23
Thanks for the reply.

However, I just now checked Synaptic and received the same message.  My modem is on (after all, I'm typing this).  Could I have deleted something or added a line to a config file that might have produced this?  Where should I start looking? 

-thx

---

### Post by Jucato on 2006-02-23
then probably the sources/locations are down at the moment. if you're absolutely sure that you haven't change anything in the sources.list, then that's the only other possible explanation.

---

### Post by Cousindaddy on 2006-02-23
I don't think I've changed anything in my sources.list...but with all of the tweaking I've done I can't be sure.  Zimmer says the sources are online now, yet I still receive the same message.  How do I access my sources.list? Perhaps I may have changed something there.

-thx

---

### Post by Jucato on 2006-02-23
maybe you could post the contents of /etc/apt/sources.list just to be sure that you have things right. :D

---

### Post by Cousindaddy on 2006-02-23
In /etc/apt/ there are 5 folders that are red with a white "x" in the middle: they are: (1) *sources.list*; (2) *secring.gpg*; (3) *sources.list.save*; (4) *sources.list.save.1*; & (5) *trustdb.gpg*.  I do have 2 *sources.list_backup* files from 2 weeks ago that are not red with the white "x."

I assume that this must be the root of the problem.  What would have caused this?

---

### Post by Jucato on 2006-02-23
um... I meant if you could post the contents of the file sources.list that is found in /etc/apt directory. those "x" marked files/folders mean that those are right-protected. that's normal

---

### Post by Cousindaddy on 2006-02-23
I don't know how to open the file to read it.

---

### Post by Perfect Storm on 2006-02-23
To read and write to it:
```
 sudo gedit /etc/apt/sources.list 
```

Read it:
```
gedit /etc/apt/sources.list 
```

---

### Post by Cousindaddy on 2006-02-23
Thanks for the help.  Here's the contents of my /etc/apt/sources.list:

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/


---

### Post by Perfect Storm on 2006-02-23
Where's the rest of your sourcelist?

Mine looks like this:

> deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

## Backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

## Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## PLF testing package
deb [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free

## BMP Plus
deb [http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/](http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/) breezy/


---

### Post by Cousindaddy on 2006-02-23
That's everything in the file.  I copied it verbatim.

---

### Post by Perfect Storm on 2006-02-23
Do you have a backup for your old sourcelist?

If not you should add:

> deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security univers

Where it says dk change it with your country code or something close.

Then
```
sudo apt-get update
```

---

### Post by Cousindaddy on 2006-02-23
That did the trick!

Thanks for everyone's help.  
And thanks for not making me feel like a complete Ubuntu idiot.

---

### Post by Cousindaddy on 2006-02-24
I just received the same error message again today.

> W: Couldn't stat source package list [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

What is going on with this?
Anyone have any ideas what would continue to cause errors like this and how I may fix them?

-thx

---

### Post by Cousindaddy on 2006-02-24
Could the root of this problem lie with Firestarter, inasmuch as I might be blocking something from accessing necessary updates?  

When I performed a: *sudo apt-get update* (as instructed when this problem happened before) everything seemed to function properly.  I then restarted Synaptic and everything was fine.

I'm sure I must have sone something to cause this error but I don't know what it would be.

-thx

---

### Post by darf681 on 2006-02-24
try this:

sudo apt-get update

this will reload all of your repository information fresh, and then synaptic should be able to see again...i got similar errors after messing around with Automatix....much to my woE

---

