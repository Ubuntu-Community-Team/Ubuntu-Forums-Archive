---
title: "Bad Package?"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by think13 on 2006-09-27
Well, I got a package off the internet.  It is the updated armagetron from sourceforge.  Well, it came as a rpm, so I had to convert it into a debian package with alien.  I then installed the package.

Now whenever I install other packages, an error message comes up that says "Error while processing armagetronad"
I will get a screenshot of this error the next time I get it.

When I try to remove it with synaptic, I get this error:
E: armagetronad: subprocess pre-removal script returned error exit status 127

help?

---

### Post by deadgobby on 2006-09-27
> **think13 said:**
> Well, I got a package off the internet.  It is the updated armagetron from sourceforge.  Well, it came as a rpm, so I had to convert it into a debian package with alien.  I then installed the package.

Now whenever I install other packages, an error message comes up that says "Error while processing armagetronad"
I will get a screenshot of this error the next time I get it.

When I try to remove it with synaptic, I get this error:
E: armagetronad: subprocess pre-removal script returned error exit status 127

help?
 You may need to change owner ship of the pack. The padck armagetron is or may be in Synaptic.
[http://ubuntuguide.org/wiki/Dapper#limewire](http://ubuntuguide.org/wiki/Dapper#limewire)
 Need to get some sleep.
Gobby

---

### Post by think13 on 2006-09-27
The package armagetron is in synaptic, but it is an old version.  Your link just brought me to the homepage for ubuntu guide, which doesn't help me.  I look for changing ownership of it, but does anyone else have any ideas as to my problem?

---

### Post by Perfect Storm on 2006-09-27
If you want to compile the latest version, I wrote a howto (today actually): [http://gaming.gwos.org/index.php?option=com_content&task=view&id=138&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=138&Itemid=63)

---

### Post by think13 on 2006-09-27
When following through that walkthrough, I got to the ./configure, and I get this error:

configure: error: no acceptable C compiler found in $PATH

Any idea what is happening there? I already installed package g++, which should have installed gcc, right?

---

### Post by Metacarpal on 2006-09-27
install build-essential
That'll give you everything you need for compiling.

---

### Post by Perfect Storm on 2006-09-27
> **think13 said:**
> When following through that walkthrough, I got to the ./configure, and I get this error:

configure: error: no acceptable C compiler found in $PATH

Any idea what is happening there? I already installed package g++, which should have installed gcc, right?

Follow the step where it says 
> Before Installation: 

Make sure that you have set up your sourcelist correctly. Also that the graphic card have the proper driver set up with 3D Acceleration enable.

Next thing that is needed is the right libs to make Armagetron Advanced to compile and run properly. Open the terminal and type;

Code:

sudo aptitude update && sudo aptitude upgrade 
sudo aptitude install build-essential checkinstall 
sudo aptitude install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libxml2-dev



---

### Post by think13 on 2006-09-27
Ok, I got it installed.  Now, did it overwrite the other 'bad' one I had installed?  

I want to remove the other version that I converted with alien and installed.  When I go to synaptic and try to mark package armagetronad for removal and apply, it gives me E: armagetronad: subprocess pre-removal script returned error exit status 127.

In /usr/local/bin, there exists the 'bad' armagetron, armagetronad, which is an executable, and armagetronad-uninstall, which is an executable text file with the contents:

#! /bin/sh
rpm -e armagetronad

When I run this file, nothing happens.

How can I remove this?

---

### Post by dmizer on 2006-09-27
that's because you used alien to install it.  so of course the removal script for the old version is written for systems that use the redhat package manager to install software, not aptitude.

so to uninstall the package you installed using alien:
```
sudo dpkg -r <name of .deb file for armagetronad>
```

---

### Post by think13 on 2006-09-28
When I tried that, I got this:

david@david-laptop:~$ sudo dpkg -r armagetronad
dpkg: error processing armagetronad (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 armagetronad
david@david-laptop:~$

I tried to reinstall it, but got E: armagetronad: subprocess pre-removal script returned error exit status 127.  I reinstalled it using Artificial Intelligence's tutorial.  Now, I get the same message when I get that, but worse, when I try to open Synaptic, I get this:

E: The package armagetronad needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Is there any way I can restore the OS to a time before this all happened? Is there any way to set 'restore points' like in Windows? Will I have to reinstall Ubuntu to get rid of this crap?

---

### Post by dmizer on 2006-09-28
sounds like you've done a pretty good job of putting the wax on. lol. it's part of the price you can (not always) pay when dealing with software that's not part of the official repository.  furthermore, it's something that's even more apt to happen if you're working with alien packages.

you might (might) be able to correct this by booting to the live cd and performing fsck to the local disk.  it fixed some broken packages for me before.

otherwise, you'll be at the mercy of artificial intelegence or a fresh install.

if you've made a seperate home partition, you shouldn't have to worry about loosing any settings.  if not, you might consider making a seperate home partition this time around.

---

### Post by think13 on 2006-09-28
Yeah, I figured that I really messed it up this time.  If I have to, it will be second reinstall this week :(

Well, I am learning a TON about Ubuntu and Linux/Unix in general from this experience, at least.

To run fsck, do I just open a terminal, and type
sudo fsck /dev/sda2
which is where I believe my Ubuntu install will be?

And what exactly does fsck do?
My question about a system restore point still stands.

---

### Post by think13 on 2006-09-28
I found a tutorial that worked like a charm for my problem

[http://www.ubuntuforums.org/showthread.php?p=1555304#post1555304]("http://www.ubuntuforums.org/showthread.php?p=1555304#post1555304")

---

