---
title: "Kubuntu"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by tech9 on 2007-09-18
I have played around with Kubuntu a bit and do like some aspects of the OS. One thing that I do not like is that it will not install libs that are dependecies to VLC Player or FireStarter...

Also, I do not see where you can configure the root password to login as root in Kub...

I heard it a millions times that no firewall is needed and actually firestarter is just a front-GUI to some built in IP Tables. I realize this - But, I like to see inbound/outbound connections just for kicks. 

Other than kmyfirewall for Kubuntu, does anyone know of something that is out there similar to firestarter?

Between Ubuntu and Kubuntu, It was almost a toss-up at first; but now that I am messing with Kubuntu more, and finding out certain things do not work, I am thinking that Ubuntu is better.

---

### Post by yabbadabbadont on 2007-09-18
What happens when you try to install firestarter?  Have you tried using "apt-get" in a terminal window instead of using Adept?

---

### Post by tech9 on 2007-09-18
> **yabbadabbadont said:**
> What happens when you try to install firestarter?  Have you tried using "apt-get" in a terminal window instead of using Adept?


Hi,

And yes... I used "sudo apt-get install firestarter"

I receive the following message...

Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  firestarter: Depends: libbonobo2-0 (>= 2.15.0) but it is not installable
               Depends: libbonoboui2-0 (>= 2.15.1) but it is not installable
               Depends: libgnome-keyring0 (>= 0.7.1) but it is not installable
               Depends: libgnome2-0 (>= 2.14.1) but it is not installable
               Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not installable
               Depends: libgnomeui-0 (>= 2.17.1) but it is not installable
               Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
               Depends: gconf2 (>= 2.12.1-4ubuntu1) but it is not installable
               Depends: gksu (>= 0.8.5) but it is not installable
E: Broken packages

Any ideas?

---

### Post by yabbadabbadont on 2007-09-18
Please post the contents of /etc/apt/sources.list

---

### Post by tech9 on 2007-09-18
> **yabbadabbadont said:**
> Please post the contents of /etc/apt/sources.list

Here you go...

 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

Thanks!

---

### Post by yabbadabbadont on 2007-09-18
That looks correct.  Try running, "sudo apt-get update", followed by "sudo aptitude install firestarter".  Please post the output if either command fails.

---

### Post by Nythain on 2007-09-18
also, your backports are disabled, not sure if any of those lib packages are in those repos... the deal is, firestarter does and has installed fine on my kubuntu box...

as for how to enable teh root account (wich is highly not suggested) you could search these forums for "enable root account" or google ubuntu enable root login and see what comes up... i dont know teh command off hand but thats because i've never used it :)

---

### Post by tech9 on 2007-09-19
> **Nythain said:**
> also, your backports are disabled, not sure if any of those lib packages are in those repos... the deal is, firestarter does and has installed fine on my kubuntu box...

as for how to enable teh root account (wich is highly not suggested) you could search these forums for "enable root account" or google ubuntu enable root login and see what comes up... i dont know teh command off hand but thats because i've never used it :)

That's good to know that you got it working on your kubuntu box... being somewhat new to linux, I have a hard time with editing files through the vi prompt under the command prompt. I usually go in as root to make any major edits, then exit and switch back to my profile. The ^ commands do not show as function keys in vi editor... so it's hard to know if I am adding to the file or editing it or what.

Thanks

---

### Post by Steveway on 2007-09-19
If vi is to hard then use nano.
Or any Graphical editor you like, but keep in mind if you use  a graphical program and need root-access then use gksu (kdesu on KDE) and not sudo!

---

### Post by tech9 on 2007-09-19
> **yabbadabbadont said:**
> That looks correct.  Try running, "sudo apt-get update", followed by "sudo aptitude install firestarter".  Please post the output if either command fails.

When running, "sudo apt-get update", I get the following message...
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Not sure what is in use though?

---

### Post by yabbadabbadont on 2007-09-19
Make sure that you don't have Adept, Synaptic, or Aptitude running anywhere.  You can only have one package manager process running at a time.

---

### Post by tech9 on 2007-09-24
> **yabbadabbadont said:**
> Make sure that you don't have Adept, Synaptic, or Aptitude running anywhere.  You can only have one package manager process running at a time.

Thanks, but I am sticking with Ubuntu for now.

---

