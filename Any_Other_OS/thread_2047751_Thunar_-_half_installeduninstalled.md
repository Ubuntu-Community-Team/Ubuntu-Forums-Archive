---
title: "Thunar - half installed/uninstalled"
date: 2012-08-25
forum: Any Other OS
---

### Post by joey00 on 2012-08-25
xfce desktop. Mint 13

On a new install I decided to replace Thunar with PCManfm.

The latter is working fine, but does not pick up volume instructions, such as empty trash or delete, or even some file open commands.

Some of these are met with an error: Failed to execute program /usr/bin/Thunar: Success.

Thunar is mostly uninstalled - I realised too late that its function is more integrated than a file browser.

I tried to re-install Thunar. But that doesn't work. Synaptic just rejects the install, and apt-get claims version and dependancy issues.

Is there any way to transfer the functionality to PCManFM, or to get it to revert to Thunar?

---

### Post by Toz on 2012-08-25
Can you post back the results of trying to re-install thunar via the command line:
```
sudo apt-get install thunar
```

And yes, thunar is a little more integrated into Xfce than maybe it should be. Search the forums here for a number of other threads about trying to replace thunar with another file manager.

---

### Post by Perfect Storm on 2012-08-25
Moved to Other OS/Distro Talk.

---

### Post by joey00 on 2012-08-26
> **Toz said:**
> Can you post back the results of trying to re-install thunar via the command line:
```
sudo apt-get install thunar
```And yes, thunar is a little more integrated into Xfce than maybe it should be. Search the forums here for a number of other threads about trying to replace thunar with another file manager.

I did this already. The general drift seems to be; "Don't - just add the prefered one and partly disable Thunar".

The output: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 thunar : Depends: thunar-data (= 1.2.3-3ubuntu2) but 1.4.0-0ubuntu1~ppa1 is to be installed
          Recommends: thunar-volman but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by Toz on 2012-08-26
Did you add the Xfce 4.10 PPA to your system? 

What does the following return?
```
apt-cache policy thunar
```

---

### Post by joey00 on 2012-08-26
I did not add a repository for Thunar. I just assumed, since it shows in synaptic, it doesnt need a specific addition.. 

apt-cache policy thunar returns:

 thunar:

  Installed: (none)
  Candidate: 1.2.3-3ubuntu2
  Version table:
     1.2.3-3ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe i386 Packages

---

### Post by Toz on 2012-08-26
Hmmm. I wonder then, why its trying to install thunar-data version 1.4 from a PPA?

Lets see where thunar-data is coming from. Can you post back the results of:
```
apt-cache policy thunar-data
```
...and
```
ls /etc/apt/sources.list.d
```
...as well as post back the contents of your /etc/apt/sources.list file.

---

### Post by joey00 on 2012-08-28
apt-cache policy thunar-data 
gives:

thunar-data:
  Installed: 1.4.0-0ubuntu1~ppa1
  Candidate: 1.4.0-0ubuntu1~ppa1
  Version table:
 *** 1.4.0-0ubuntu1~ppa1 0
        100 /var/lib/dpkg/status
     1.2.3-3ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe i386 Packages

--------
ls /etc/apt/sources.list.d
gives:

local-repository.list        xubuntu-dev-xfce-4_10-precise.list
local-repository.list.save  xubuntu-dev-xfce-4_10-precise.list.save

----------------
sources list:

deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) maya main upstream import backport
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free

# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb games

-------------

> **Toz said:**
> Hmmm. I wonder then, why its trying to install thunar-data version 1.4 from a PPA?

Lets see where thunar-data is coming from. Can you post back the results of:
```
apt-cache policy thunar-data
```...and
```
ls /etc/apt/sources.list.d
```...as well as post back the contents of your /etc/apt/sources.list file.

---

### Post by Toz on 2012-08-28
> **joey00 said:**
> 
thunar-data:
  Installed: 1.4.0-0ubuntu1~ppa1
  Candidate: 1.4.0-0ubuntu1~ppa1
  Version table:
[COLOR="Red"] *** 1.4.0-0ubuntu1~ppa1 0[/COLOR]
        100 /var/lib/dpkg/status
     1.2.3-3ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
Some sort of PPA has been added that provides the newer thunar package.

> --------
ls /etc/apt/sources.list.d
gives:

local-repository.list        [COLOR="Red"]xubuntu-dev-xfce-4_10-precise.list[/COLOR]
local-repository.list.save  xubuntu-dev-xfce-4_10-precise.list.save
And here it is. This explains why you're having a problem - you've got some sort of Xfce 4.10 repository referenced.

1. Can you post back the contents of /etc/apt/sources.list.d/local-repository.list xubuntu-dev-xfce-4_10-precise.list

2. And can you post back the results of:
```
sudo apt-get update
```

---

### Post by joey00 on 2012-08-30
> **Toz said:**
> Some sort of PPA has been added that provides the newer thunar package.

And here it is. This explains why you're having a problem - you've got some sort of Xfce 4.10 repository referenced.

1. Can you post back the contents of /etc/apt/sources.list.d/local-repository.list xubuntu-dev-xfce-4_10-precise.list

2. And can you post back the results of:
```
sudo apt-get update
```
---------------
/etc/apt/sources.list.d/local-repository.list   contains:

# deb file:///usr/share/local-repository binary/

xubuntu-dev-xfce-4_10-precise.list   I am not finding. Where please?

?

sudo apt-get update output - see attachment.

---

### Post by Toz on 2012-08-30
How about:
```

ls -l /etc/apt/sources.list.d
```
Is it there?

Also, can you post back the results of:
```
dpkg -l  |grep -i ppa
```

It looks as if Xfce 4.10 was at one point in time installed on this computer but not properly uninstalled. This is what is causing your problem.

---

### Post by joey00 on 2012-08-31
> **Toz said:**
> How about:
```

ls -l /etc/apt/sources.list.d
```Is it there?

Also, can you post back the results of:
```
dpkg -l  |grep -i ppa
```It looks as if Xfce 4.10 was at one point in time installed on this computer but not properly uninstalled. This is what is causing your problem.

Yes it is!  :

[FONT=arial][SIZE=2]xubuntu-dev-xfce-4_10-precise.list[/SIZE][/FONT]
# deb [http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu](http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu) precise main
# deb-src [http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu](http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu) precise main

AFAIK no updated xfce was installed. But many of the Mint 13 distributions were buggy when it came to install. Maybe it found its way in while struggling to get an acceptable desktop. Grey on grey is pretty, but useless!

ppa list attached

---

### Post by Toz on 2012-08-31
Try uncommenting the lines in xubuntu-dev-xfce-4_10-precise.list (remove the leading #s), running:
```
sudo apt-get update
```
...and if you get no errors, try reinstalling thunar.

---

### Post by joey00 on 2012-09-01
Toz,

Thank you!

The latest change seems to do the trick. I havent fully checked it, but everything seems to work now.

Again, my grateful thanks for your efforts.  :)

May I throw in a question: The two commented-out lines. Have you any idea why they would be so?

Since it wasn't done directly by me, I conjecture that either the file arrived that way, or some other process took them out.

joey

---

### Post by Toz on 2012-09-02
> **joey00 said:**
> Toz,

Thank you!

The latest change seems to do the trick. I havent fully checked it, but everything seems to work now.

Again, my grateful thanks for your efforts.  :)
No worries - glad I could help. If you don't mind, can you mark this thread solved so that others with a similar problem may find it easier?

> May I throw in a question: The two commented-out lines. Have you any idea why they would be so?

Since it wasn't done directly by me, I conjecture that either the file arrived that way, or some other process took them out.

joey
Unfortunately, I don't and have never used Mint. Looking on the Mint web page, it states that Maya 13 is Ubuntu 12.04 and Xfce 4.10. There are 2 ways to get Xfce 4,10 working with Ubuntu 12.04 - compile from source or use the PPA. The easier option would be to use the PPA and if Mint is using the PPA, I have no idea why those particular references would have been commented out. It wouldn't make sense to do so. I'd be more inclined to believe that some process would have done that - but the only process that I know of that would comment out PPAs, is the upgrade to a new ubuntu version process.

---

