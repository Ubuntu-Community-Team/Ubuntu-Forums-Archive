---
title: "Updates wont work!"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-09-18
When I click the update button I get this:

Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'synaptic' first.

Im positive that there is nothing open that I know about, and I have tried restarting and updating before I do anything else, still got the same thing.

When I try to do a "sudo apt-get update" it goes through the update process and then gives me this:


Fetched 31B in 6s (5B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Sef on 2006-09-18
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Had the same problem and ran dpkg --configure -a.  After that it worked.

To run dkpg manually:

Applications > Accessories > Terminal

sudo dpkg --configure -a 

If there is a problem with that command, then do

sudo apt-get dpkg --configure -a

Think I ran the first one, but just can't remember right now.

---

### Post by voodoonirvana on 2006-09-18
> **Sef said:**
> Had the same problem and ran dpkg --configure -a.  After that it worked.

To run dkpg manually:

Applications > Accessories > Terminal

sudo dpkg --configure -a 

If there is a problem with that command, then do

sudo apt-get dpkg --configure -a

Think I ran the first one, but just can't remember right now.

Ok I tried that and I got this, something to do with Java???

Setting up j2sdk1.4-doc (1.4.2.02-1ubuntu3) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    j2sdk-1_4_2-doc.zip j2sdk-1_4_0-doc-ja.zip j2sdk-1_4_2-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.



How do I install this?

---

### Post by voodoonirvana on 2006-09-18
I could really use some help here.

---

### Post by catlett on 2006-09-18
Did you try to install a java application before this? That is not a needed application. It is for someone who wants to develop java applications.
Can you open 'synaptic package manager'? If so search for that application, right click it and select 'mark for removal' Hopefully that will keep apt from trying to install.That is if you didn't want the development package. Regular java for the ineternet is enabled from a different app.
If you can do that, use aptitude to update and upgrade, it does a better job of sorting things out.
```
sudo aptitude update
```
```
sudo aptitude upgrade
```

---

### Post by voodoonirvana on 2006-09-18
> **catlett said:**
> Did you try to install a java application before this? That is not a needed application. It is for someone who wants to develop java applications.
Can you open 'synaptic package manager'? If so search for that application, right click it and select 'mark for removal' Hopefully that will keep apt from trying to install.That is if you didn't want the development package. Regular java for the ineternet is enabled from a different app.
If you can do that, use aptitude to update and upgrade, it does a better job of sorting things out.
```
sudo aptitude update
```
```
sudo aptitude upgrade
```

Okay, I tried uninstalling all that in the Add/Remove programs thing, and now its giving this:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

---

### Post by catlett on 2006-09-18
It keeps acting as if another appication is using apt. That error (could not open) usually means something else is accessingh it and it can't get to it. Or you aren't root. What happened when you ran audo aptitude upgrade? The same error?

---

### Post by bodhi.zazen on 2006-09-20
```
sudo rm /var/lib/dpkg/lock
```

---

### Post by voodoonirvana on 2006-09-20
Oh, I already got this fixed. I had to uninstall all this junk from java, but thanks anyway.

---

### Post by harshad on 2006-09-23
I am getting the same error and synaptic package manager won't open. I get the error "Only one software management tool is allowed to run at the same time"

When I tried running sudo dpkg --configure -a

I get this 
[I]Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading... dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 flashplugin-nonfree
[/I]

So I guess the root cause is the flash plugin for firefox that I tried to install. 

Fortunately after I got this error on the terminal, Synaptic and my auto update seems to have started working again. I have no idea why

It's currently downloading files. I hope the entire install goes through.

---

### Post by chrisfay on 2006-09-23
> When I tried running sudo dpkg --configure -a

I get this 
Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading... dpkg: error processing flashplugin-nonfree (--configure):
subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
flashplugin-nonfree

This is a known problem with the recent flashplugin-nonfree update in backports. See [this]("http://www.ubuntuforums.org/showthread.php?t=261179&highlight=flashplugin-nonfree") thread.

To get back to the stable flash plugin:
```
sudo apt-get install flashplugin-nonfree/dapper
```

---

