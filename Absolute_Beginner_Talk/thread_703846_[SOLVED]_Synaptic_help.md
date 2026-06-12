---
title: "[SOLVED] Synaptic help"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by GreTTin on 2008-02-21
Hi all,

I'm pretty new to ubuntu and have come across a problem I can't fix myself. After updating last (although I'm not sure if it was due to that or other things i've installed) i get the error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

then when i run 

```
sudo dpkg --configure -a
``` 

in terminal i get:

```
paul@main:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up tex-common (1.9) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing tex-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 1.4); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-omega:
 texlive-omega depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-omega (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-doc-base:
 texlive-doc-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base-bin:
 texlive-base-bin depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1
paul@main:~$ 
```


now i tried getopt in terminal and it told me to install util-linux however i can't because apt-get doesn't work.

I was just wondering if there's a way to cancel the initramfs update? i think that's what is causing the problem.

i may not be making any sense but hope someone can help. 

thanks all.

---

### Post by spiderbatdad on 2008-02-21
maybe this: ```
sudo apt-get install -f
sudo apt-get update
```

---

### Post by GreTTin on 2008-02-21
I get the same request to run dpkg --configure -a

```
paul@main:~$ sudo apt-get install -f
[sudo] password for paul:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
paul@main:~$ 
```

sudo apt-get update starts but then quits out with 

```
Failed to fetch [http://ma.ath.cx/debian-emu-rep/binary/Packages.gz](http://ma.ath.cx/debian-emu-rep/binary/Packages.gz)  404 Not Found
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
``` 

hmmmmm is that a repository? I'll have a go at removing that, thanks for help. I'll let you know what happens

---

### Post by PeterJS on 2008-02-21
That's quite a problem, I thought util-linux, was required to get a system to boot, shows what I know. But I digress, running which on my system shows me that getopt should be in /usr/bin, you might try popping in a live CD and copying getopt from the live environment to your install, if that works you can force the update to complete and then install util-linux.

---

### Post by r4ik on 2008-02-21
Or get the .deb for you're architecture,

[http://altruistic.lbl.gov/mirrors/ubuntu/pool/main/u/util-linux/](http://altruistic.lbl.gov/mirrors/ubuntu/pool/main/u/util-linux/)

Good Luck !

---

### Post by GreTTin on 2008-02-21
hey, thanks for replies 

I just loaded up live cd but couldn't find util-linux in that folder (usr/bin).

r4ik, I followed that link and am not sure which .deb I need
I have the 64 bit version of ubuntu 7.10 according to conky my kernel is 2.6.22-14-generic

thanks again for the help.

---

### Post by GreTTin on 2008-02-21
sorry for the double post but just clicked on util-linux_2.13-10ubuntu1_amd64.deb and it opened up a package installer.

it says in status:  error: conflicts with the installed package 'linux32'

now i've got the 64 bit version installed so any ideas?

---

### Post by seventhc on 2008-02-21
Maybe you should be using the 32 bit version???
Do you definitely have a 64 bit processor?

---

### Post by GreTTin on 2008-02-21
yeah i got an amd athlon 64 x2 3800+
got 64bit xp on another partition
has worked fine untill this update :(

---

### Post by seventhc on 2008-02-21
OK, just making sure
have you run this yet?
```
[FONT=monospace]dpkg --configure -a[/FONT]
```
Edit: never mind the above, I see you ran it.

I'd also post the output of

```
cat /etc/apt/sources.list
```

---

### Post by GreTTin on 2008-02-21
yeah I posted it in my first post :)

just ran it again and here is what i've got:

```
paul@main:~$ sudo dpkg --configure -a
[sudo] password for paul:
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up tex-common (1.9) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing tex-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 1.4); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-omega:
 texlive-omega depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-omega (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-doc-base:
 texlive-doc-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base-bin:
 texlive-base-bin depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1
paul@main:~$ 
```

thanks for help

---

### Post by GreTTin on 2008-02-21
ok and here is that

```
paul@main:~$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse #Added by software-properties
deb http://packages.medibuntu.org/ gutsy free non-free
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted
deb http://packages.medibuntu.org/ gutsy free non-free
```

hope you can help :)

---

### Post by seventhc on 2008-02-21
Thats a small list....did you delete all the commented parts??
here is mine, maybe make a back up of yours and try mine
```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

What do you have checked in you sources list??
*System>Administration>Software Sources*

---

### Post by GreTTin on 2008-02-21
I've replaced my list with yours and then opened software sources to update but got the same error :(

---

### Post by seventhc on 2008-02-21
oh You have to do this too..sorry, forgot..after you save that list
```
sudo apt-get update
```
without that, it's still reading the old list.

---

### Post by GreTTin on 2008-02-21
yeah just ran that(sudo apt-get update) and ended with 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

again :(

---

### Post by seventhc on 2008-02-21
well, run that one more time with the new list...can't hurt.
sudo dpkg --configure -a

---

### Post by GreTTin on 2008-02-21
yeah sorry it's late here :) didn't even think of that but no good am afraid.

```
paul@main:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up tex-common (1.9) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing tex-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 1.4); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-omega:
 texlive-omega depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-omega (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-doc-base:
 texlive-doc-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base-bin:
 texlive-base-bin depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1
paul@main:~$ 
```

---

### Post by seventhc on 2008-02-21
before this started happeneing did you install this?

[FONT=monospace]*sudo apt-get install texlive-full*

b/c it seems texlive is whats causing these errors somehow.
[/FONT]

---

### Post by GreTTin on 2008-02-21
I installed a few games from synaptic but never noticed a fault until the update.

Is there any way to cancel what dpkg is trying to do?

Not sure if i'm getting this right but from what i've read dpkg --configure -a is to let dpkg finish off something that it never got a chance to due to a crash or w/e. I think mine is trying to finish off a broken install.

---

### Post by seventhc on 2008-02-21
The only thing I can think of now is to go to [I]System>Administration>Synaptic Package Manager
[/I]I think there is a place to fix broken packages in there. It will also show you the number of broken packages on the bottom of the screen.
Also check twhich repositories are enabled, just to double check.
*Settings>Repositories*

---

### Post by GreTTin on 2008-02-21
unfortunately thats the problem :( when i open synaptic package manager it errors (E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.) and closes straight away :(

---

### Post by seventhc on 2008-02-21
yikes....it's like a catch 22
...you need to do *this* to fix it,
but you can't do *this* b/c it's broken...:confused:

I don't know what would work...maybe see if someone else here has any more ideas...I don;t know what else to try.
I'll try to find info on it though.

---

### Post by seventhc on 2008-02-21
edit

---

### Post by GreTTin on 2008-02-21
I know! haha yeah it's a little frustrating.

Thank you for the help anyway :)

The only thing I can think of is to cancel what it is dpkg is trying to do i'm not sure if it's possible i've been searching but i'm not even sure if i'm using the right terminology.

---

### Post by seventhc on 2008-02-21
theres a post here, but I think it's things you tried.
[http://ubuntuforums.org/showthread.php?t=653495](http://ubuntuforums.org/showthread.php?t=653495)

but they basically do the same thing.
```

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```you haven't tried the upgrade command yet.

---

### Post by GreTTin on 2008-02-21
I cant open synaptic :( i can get into addd/remove programs but if i remove or add anything then apply it, it fails and errors out :(

---

### Post by seventhc on 2008-02-21
i mean run that last command...it's the only one you havent tried.
```
sudo apt-get upgrade
```

also..hmm I have to reread this thread lol

---

### Post by GreTTin on 2008-02-21
sorry think i was on the other page whilst you were editing :)

```
paul@main:~$ sudo apt-get upgrade
[sudo] password for paul:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
paul@main:~$ 
```

D'oh still no good :(

Thanks for your help man I'm gonna have to get some sleep it's 3 in the morning here if you think of anything (or any one else does) then please please post it and i'll follow it up tomorrow.

Thanks again.

---

### Post by seventhc on 2008-02-21
Ok, I'm gonna sleep soon too, but hopefully someone can think of something. I'm not sure what to do at this point.](*,)

---

### Post by spiderbatdad on 2008-02-21
```
sudo dpkg-reconfigure -a --force
```
This will take some time, and you will need to answers questions regarding how you want to configure your system.

---

### Post by crjackson on 2008-02-21
I'm actually having problems with my synaptic as well.  It works until I go into the setting menu and try to change ANYTHING.  As soon as I click on Apply or OK it locks up my desktop.

I'm wondering if it's possible to REMOVE synaptic completly and then reinstall (hopefull fixing some problems)  What do you guys think about trying that?

EDIT:  I forgot to mention this.  I was having some errors similar to yours and actually got it working correctly again (except for the preferences thing) by deleting the offending cached files, and then when running again, I had to do a force-install to make it all install.  After that, synaptic appeared to work correctly.  I didn't realize there was a problem until I decided to change my synaptic preferences to delete cached packages after installing.  Don't know if any of this will help you or not, but at least it's something else to try.

---

### Post by seventhc on 2008-02-21
I've been trying to find info about synaptic, but it seems everyhting I find is all the stuff already attempted in this thread.
Although the post above by **spiderbatdad** is different.

can you remove and reinstall synaptic??
I was trying to find info on that too, but it's hard to search b/c it always brings results installing, removing using synaptic but not how to actually remove synaptic itself.

---

### Post by soulfly7x on 2008-02-21
> **seventhc said:**
> I've been trying to find info about synaptic, but it seems everyhting I find is all the stuff already attempted in this thread.
Although the post above by **spiderbatdad** is different.

can you remove and reinstall synaptic??
I was trying to find info on that too, but it's hard to search b/c it always brings results installing, removing using synaptic but not how to actually remove synaptic itself.

First, I would try booting into a console session. In other words, at the login screen, hit the menu and choose console session, or command line session, or however it's phrased.

You should be able to remove synaptic with ```
sudo apt-get remove synaptic
``` or ```
sudo apt-get remove --purge synaptic
```

This will remove the configuration files as well, which is what I assume you *really* want. then ```
sudo apt-get install synaptic
```.

I would also try using the console login the next time there is any kind of extended dpkg error. It might help prevent any kind of conflict with a GUI updater or whatever trying to run at the same time.

---

### Post by seventhc on 2008-02-21
Thanks for the info. :)
That might be something to try.
I don't need to do it, I was trying to find something for the OP and then **crjackson** mentioned removing synaptic b/c he was having a problem too..

---

### Post by trig on 2008-02-21
well this is what mine said... sun java-6 missing... it goes to the terms and conditions then freezes

---

### Post by crjackson on 2008-02-21
> **soulfly7x said:**
> First, I would try booting into a console session. In other words, at the login screen, hit the menu and choose console session, or command line session, or however it's phrased.

You should be able to remove synaptic with ```
sudo apt-get remove synaptic
``` or ```
sudo apt-get remove --purge synaptic
```

This will remove the configuration files as well, which is what I assume you *really* want. then ```
sudo apt-get install synaptic
```.

I would also try using the console login the next time there is any kind of extended dpkg error. It might help prevent any kind of conflict with a GUI updater or whatever trying to run at the same time.

Thanks... I'm at work right now and can't try this, but mark my words if I don't find another fix in the next day, I will do this and post back with results.

---

### Post by trig on 2008-02-22
trig@trig-desktop:~$ sudo dpkg-reconfigure -a --force
 * Disabling power management...                                         [ OK ] 
 * Checking battery state...                                             [ OK ] 
 * Stopping anac(h)ronistic cron anacron                                 [ OK ] 
 * Starting anac(h)ronistic cron anacron                                 [ OK ] 
 * Stopping Advanced Power Management daemon...                          [ OK ] 
 * Starting Advanced Power Management daemon...                          [ OK ] 
Caching application data...
Skipped k3dsurf.desktop: does not include a menu name
Generating mime/codec maps...
Caching application data...
Skipped k3dsurf.desktop: does not include a menu name
Generating mime/codec maps...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Loading AppArmor profiles - AppArmor already loaded with profiles.: Skipped.
Reloading AppArmor profiles : done.
 * Stopping automatic crash report generation: apport                    [ OK ] 
 * Starting automatic crash report generation: apport                    [ OK ] 







&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring atlas3-base &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; layout used by atlas is as follows:                                       &#8593;  
 &#9474;                                                                           &#9618;  
 &#9474; /usr/lib -- reference blas and lapack libraries if installed; atlas       &#9618;  
 &#9474; libraries using only generic code for this general architecture.          &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; /usr/lib/atlas  --  atlas-provided blas and lapack libs using only        &#9618;  
 &#9474; generic code for this general architecture.                               &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; /usr/lib/<flag> --  atlas libraries using cpu extension instructions      &#9618;  
 &#9474; which require the running cpu to have capability <flag>, as reported in   &#9618;  
 &#9474; /proc/cpuinfo.  E.g. 'sse' for SSE1, '3dnow' for 3dnow, etc.              &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; /usr/lib/atlas/<flag> -- atlas-provided blas and lapack libraries using   &#9646;  
 &#9474;  cpu extensions as described above.                                       &#8595;  





trig@trig-desktop:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
trig@trig-desktop:~$ 
trig@trig-desktop:~$ 


trig@trig-desktop:~$ sudo apt-get remove --purge synaptic
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
trig@trig-desktop:~$ 
trig@trig-desktop:~$ 




 &#9474;

---

### Post by r4ik on 2008-02-22
Redo you're sources.list and see what happens,

 Manual Method for Adding Repositories

sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup



sudo gedit /etc/apt/sources.list

    * Replace everything with the following lines 

    To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code) 
    e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) gutsy main restricted universe multiverse 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

    * Save the edited file 

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
sudo apt-get update

[edit]

---

### Post by GreTTin on 2008-02-22
ok glad there has been a few replies :) thanks everyone 

first of all i just tried 
```
sudo dpkg-reconfigure -a --force
```
and got
```
paul@main:~$ sudo dpkg-reconfigure -a --force
 * Disabling power management...                                                   [ OK ] 
 * Checking battery state...                                                       [ OK ] 
 * Stopping ACPI services...                                                       [ OK ] 
 * Loading ACPI modules...                                                         [ OK ] 
 * Starting ACPI services...                                                       [ OK ] 
 * Stopping anac(h)ronistic cron anacron                                           [ OK ] 
 * Starting anac(h)ronistic cron anacron                                           [ OK ] 
Caching application data...
Skipped k3dsurf.desktop: does not include a menu name
Generating mime/codec maps...
Caching application data...
Skipped k3dsurf.desktop: does not include a menu name
Generating mime/codec maps...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
paul@main:~$
```

seems the same but i'll try a couple of things then i'm just going to try the terminal stuff.

thanks again

---

### Post by GreTTin on 2008-02-22
ok bit of new news :)

I can get the apt-get /dpkg working again by doing
```
sudo dpkg --purge -a
```
that stops it wanting to continue the install of texlive.

now as soon as i try to add/remove anything else the problem re occurs.

I just tried
```
sudo apt-get remove texlive-full
```
and got
```
paul@main:~$ sudo apt-get remove texlive-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcompris-data python-pysqlite2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  texlive-full
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
97 not fully installed or removed.
Need to get 0B of archives.
After unpacking 86.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 213810 files and directories currently installed.)
Removing texlive-full ...
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up tex-common (1.9) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing tex-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 1.4); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-doc-base:
 texlive-doc-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base-bin:
 texlive-base-bin depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-doc-base (>= 2007); however:
  Package texlive-doc-base is not configured yet.
 texlive-base depends on texlive-base-bin (>= 2007-8); however:
  Package texlive-base-bin is not configured yet.
 texlive-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-latex-recommended depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-danish:
 texlive-lang-danish depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-danish depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-danish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-vietnamese:
 texlive-lang-vietnamese depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-vietnamese depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-vietnamese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-polish:
 texlive-lang-polish depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-polish depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-lang-polish depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-lang-polish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-mongolian:
 texlive-lang-mongolian depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-mongolian depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-mongolian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-french:
 texlive-lang-french depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-french depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-french (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-swedish:
 texlive-lang-swedish depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-swedish depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-swedish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-pictures depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-greek:
 texlive-lang-greek depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-greek depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-greek (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-croatian:
 texlive-lang-croatian depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-croatian depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-croatian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-extra:
 texlive-fonts-extra depends on texlive-base; however:
  Package texlive-base is not configured yet.
 texlive-fonts-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-fonts-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-fonts-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-fonts-recommended (>= 2007-7); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2007-7); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tetex-bin:
 tetex-bin depends on texlive (>= 2007-7); however:
  Package texlive is not configured yet.
dpkg: error processing tetex-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-spanish:
 texlive-lang-spanish depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-spanish depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-spanish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of preview-latex-style:
 preview-latex-style depends on tex-common; however:
  Package tex-common is not configured yet.
 preview-latex-style depends on texlive-base-bin; however:
  Package texlive-base-bin is not configured yet.
dpkg: error processing preview-latex-style (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on preview-latex-style; however:
  Package preview-latex-style is not configured yet.
 texlive-latex-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-latex-extra depends on texlive-pictures; however:
  Package texlive-pictures is not configured yet.
 texlive-latex-extra depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-norwegian:
 texlive-lang-norwegian depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-norwegian depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-norwegian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-german:
 texlive-lang-german depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-german depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-german (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-cyrillic:
 texlive-lang-cyrillic depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-cyrillic depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-cyrillic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-font-utils depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-finnish:
 texlive-lang-finnish depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-finnish depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-finnish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-generic-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended; however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on texlive-base; however:
  Package texlive-base is not configured yet.
 texlive-pstricks depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-portuguese:
 texlive-lang-portuguese depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-portuguese depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-portuguese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-other:
 texlive-lang-other depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-other depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-other (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-bibtex-extra:
 texlive-bibtex-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-bibtex-extra depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-bibtex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-czechslovak:
 texlive-lang-czechslovak depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-czechslovak depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-lang-czechslovak depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-lang-czechslovak (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-math-extra:
 texlive-math-extra depends on texlive-fonts-recommended; however:
  Package texlive-fonts-recommended is not configured yet.
 texlive-math-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-math-extra depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-math-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-italian:
 texlive-lang-italian depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-italian depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-italian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-publishers:
 texlive-publishers depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-publishers depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-publishers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-dutch:
 texlive-lang-dutch depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-dutch depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-dutch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-hungarian:
 texlive-lang-hungarian depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-hungarian depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-hungarian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-latin:
 texlive-lang-latin depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-latin depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-latin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tetex-extra:
 tetex-extra depends on texlive-lang-danish (>= 2007); however:
  Package texlive-lang-danish is not configured yet.
 tetex-extra depends on texlive-lang-vietnamese; however:
  Package texlive-lang-vietnamese is not configured yet.
 tetex-extra depends on texlive-lang-polish (>= 2007); however:
  Package texlive-lang-polish is not configured yet.
 tetex-extra depends on texlive-lang-mongolian (>= 2007); however:
  Package texlive-lang-mongolian is not configured yet.
 tetex-extra depends on texlive-lang-french (>= 2007); however:
  Package texlive-lang-french is not configured yet.
 tetex-extra depends on texlive-lang-swedish (>= 2007); however:
  Package texlive-lang-swedish is not configured yet.
 tetex-extra depends on texlive-pictures (>= 2007-7); however:
  Package texlive-pictures is not configured yet.
 tetex-extra depends on texlive-lang-greek (>= 2007); however:
  Package texlive-lang-greek is not configured yet.
 tetex-extra depends on texlive-lang-croatian (>= 2007); however:
  Package texlive-lang-croatian is not configured yet.
 tetex-extra depends on texlive-fonts-extra (>= 2007); however:
  Package texlive-fonts-extra is not configured yet.
 tetex-extra depends on tetex-bin; however:
  Package tetex-bin is not configured yet.
 tetex-extra depends on texlive-lang-spanish (>= 2007); however:
  Package texlive-lang-spanish is not configured yet.
 tetex-extra depends on texlive-latex-extra (>= 2007); however:
  Package texlive-latex-extra is not configured yet.
 tetex-extra depends on texlive-lang-norwegian (>= 2007); however:
  Package texlive-lang-norwegian is not configured yet.
 tetex-extra depends on texlive-lang-german (>= 2007); however:
  Package texlive-lang-german is not configured yet.
 tetex-extra depends on texlive-lang-cyrillic (>= 2007); however:
  Package texlive-lang-cyrillic is not configured yet.
 tetex-extra depends on texlive-font-utils (>= 2007-8); however:
  Package texlive-font-utils is not configured yet.
 tetex-extra depends on texlive-lang-finnish (>= 2007); however:
  Package texlive-lang-finnish is not configured yet.
 tetex-extra depends on texlive-pstricks (>= 2007); however:
  Package texlive-pstricks is not configured yet.
 tetex-extra depends on texlive-lang-portuguese; however:
  Package texlive-lang-portuguese is not configured yet.
 tetex-extra depends on texlive-lang-other (>= 2007); however:
  Package texlive-lang-other is not configured yet.
 tetex-extra depends on texlive-bibtex-extra (>= 2007); however:
  Package texlive-bibtex-extra is not configured yet.
 tetex-extra depends on texlive-lang-czechslovak (>= 2007); however:
  Package texlive-lang-czechslovak is not configured yet.
 tetex-extra depends on texlive-math-extra (>= 2007); however:
  Package texlive-math-extra is not configured yet.
 tetex-extra depends on texlive-lang-italian (>= 2007); however:
  Package texlive-lang-italian is not configured yet.
 tetex-extra depends on texlive-publishers (>= 2007); however:
  Package texlive-publishers is not configured yet.
 tetex-extra depends on texlive-lang-dutch (>= 2007); however:
  Package texlive-lang-dutch is not configured yet.
 tetex-extra depends on texlive-lang-hungarian (>= 2007); however:
  Package texlive-lang-hungarian is not configured yet.
 tetex-extra depends on texlive-lang-latin (>= 2007); however:
  Package texlive-lang-latin is not configured yet.
dpkg: error processing tetex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cm-super:
 cm-super depends on tex-common (>= 0.11); however:
  Package tex-common is not configured yet.
 cm-super depends on tetex-base (>= 3) | texlive-latex-recommended; however:
  Package tetex-base is not installed.
  Package texlive-latex-recommended is not configured yet.
 cm-super depends on tetex-extra (>= 3) | texlive-latex-recommended; however:
  Package tetex-extra is not configured yet.
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing cm-super (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-metapost:
 texlive-metapost depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-metapost depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-metapost (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lmodern:
 lmodern depends on tex-common (>= 0.7); however:
  Package tex-common is not configured yet.
dpkg: error processing lmodern (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of context:
 context depends on tex-common (>= 1.4); however:
  Package tex-common is not configured yet.
 context depends on texlive-base-bin (>= 2007); however:
  Package texlive-base-bin is not configured yet.
 context depends on texlive-base (>= 2007); however:
  Package texlive-base is not configured yet.
 context depends on texlive-metapost (>= 2007); however:
  Package texlive-metapost is not configured yet.
 context depends on lmodern (>= 1.01); however:
  Package lmodern is not configured yet.
dpkg: error processing context (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-extra-utils depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of feynmf:
 feynmf depends on tex-common (>= 0.7); however:
  Package tex-common is not configured yet.
 feynmf depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 feynmf depends on texlive-font-utils; however:
  Package texlive-font-utils is not configured yet.
 feynmf depends on texlive-extra-utils; however:
  Package texlive-extra-utils is not configured yet.
dpkg: error processing feynmf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on tetex-extra | texlive-latex-recommended; however:
  Package tetex-extra is not configured yet.
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 pgf depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on pgf (>= 1.00-1); however:
  Package pgf is not configured yet.
 latex-beamer depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 latex-beamer depends on tetex-extra | texlive-latex-base; however:
  Package tetex-extra is not configured yet.
  Package texlive-latex-base is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of musixlyr:
 musixlyr depends on tetex-bin (>= 1.0.5-1) | texlive-base-bin; however:
  Package tetex-bin is not configured yet.
  Package texlive-base-bin is not configured yet.
dpkg: error processing musixlyr (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
paul@main:~$ 

``` sorry for the huge post is there another way to get rid of the part that is already installed?

EDIT: I also tried ```
sudo apt-get purge texlive-full
```

to get this```
paul@main:~$ sudo apt-get purge texlive-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package texlive-full is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
96 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up tex-common (1.9) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing tex-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 1.4); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-doc-base:
 texlive-doc-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base-bin:
 texlive-base-bin depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-doc-base (>= 2007); however:
  Package texlive-doc-base is not configured yet.
 texlive-base depends on texlive-base-bin (>= 2007-8); however:
  Package texlive-base-bin is not configured yet.
 texlive-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-latex-recommended depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-danish:
 texlive-lang-danish depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-danish depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-danish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-vietnamese:
 texlive-lang-vietnamese depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-vietnamese depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-vietnamese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-polish:
 texlive-lang-polish depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-polish depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-lang-polish depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-lang-polish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-mongolian:
 texlive-lang-mongolian depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-mongolian depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-mongolian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-french:
 texlive-lang-french depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-french depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-french (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-swedish:
 texlive-lang-swedish depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-swedish depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-swedish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-pictures depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-greek:
 texlive-lang-greek depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-greek depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-greek (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-croatian:
 texlive-lang-croatian depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-croatian depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-croatian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-extra:
 texlive-fonts-extra depends on texlive-base; however:
  Package texlive-base is not configured yet.
 texlive-fonts-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-fonts-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-fonts-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-fonts-recommended (>= 2007-7); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2007-7); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tetex-bin:
 tetex-bin depends on texlive (>= 2007-7); however:
  Package texlive is not configured yet.
dpkg: error processing tetex-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-spanish:
 texlive-lang-spanish depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-spanish depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-spanish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of preview-latex-style:
 preview-latex-style depends on tex-common; however:
  Package tex-common is not configured yet.
 preview-latex-style depends on texlive-base-bin; however:
  Package texlive-base-bin is not configured yet.
dpkg: error processing preview-latex-style (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on preview-latex-style; however:
  Package preview-latex-style is not configured yet.
 texlive-latex-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-latex-extra depends on texlive-pictures; however:
  Package texlive-pictures is not configured yet.
 texlive-latex-extra depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-norwegian:
 texlive-lang-norwegian depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-norwegian depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-norwegian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-german:
 texlive-lang-german depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-german depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-german (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-cyrillic:
 texlive-lang-cyrillic depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-cyrillic depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-cyrillic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-font-utils depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-finnish:
 texlive-lang-finnish depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-finnish depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-finnish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-generic-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended; however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on texlive-base; however:
  Package texlive-base is not configured yet.
 texlive-pstricks depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-portuguese:
 texlive-lang-portuguese depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-portuguese depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-portuguese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-other:
 texlive-lang-other depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-other depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-other (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-bibtex-extra:
 texlive-bibtex-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-bibtex-extra depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-bibtex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-czechslovak:
 texlive-lang-czechslovak depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-czechslovak depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-lang-czechslovak depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-lang-czechslovak (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-math-extra:
 texlive-math-extra depends on texlive-fonts-recommended; however:
  Package texlive-fonts-recommended is not configured yet.
 texlive-math-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-math-extra depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-math-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-italian:
 texlive-lang-italian depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-italian depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-italian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-publishers:
 texlive-publishers depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-publishers depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-publishers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-dutch:
 texlive-lang-dutch depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-dutch depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-dutch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-hungarian:
 texlive-lang-hungarian depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-hungarian depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-hungarian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-latin:
 texlive-lang-latin depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-lang-latin depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-lang-latin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tetex-extra:
 tetex-extra depends on texlive-lang-danish (>= 2007); however:
  Package texlive-lang-danish is not configured yet.
 tetex-extra depends on texlive-lang-vietnamese; however:
  Package texlive-lang-vietnamese is not configured yet.
 tetex-extra depends on texlive-lang-polish (>= 2007); however:
  Package texlive-lang-polish is not configured yet.
 tetex-extra depends on texlive-lang-mongolian (>= 2007); however:
  Package texlive-lang-mongolian is not configured yet.
 tetex-extra depends on texlive-lang-french (>= 2007); however:
  Package texlive-lang-french is not configured yet.
 tetex-extra depends on texlive-lang-swedish (>= 2007); however:
  Package texlive-lang-swedish is not configured yet.
 tetex-extra depends on texlive-pictures (>= 2007-7); however:
  Package texlive-pictures is not configured yet.
 tetex-extra depends on texlive-lang-greek (>= 2007); however:
  Package texlive-lang-greek is not configured yet.
 tetex-extra depends on texlive-lang-croatian (>= 2007); however:
  Package texlive-lang-croatian is not configured yet.
 tetex-extra depends on texlive-fonts-extra (>= 2007); however:
  Package texlive-fonts-extra is not configured yet.
 tetex-extra depends on tetex-bin; however:
  Package tetex-bin is not configured yet.
 tetex-extra depends on texlive-lang-spanish (>= 2007); however:
  Package texlive-lang-spanish is not configured yet.
 tetex-extra depends on texlive-latex-extra (>= 2007); however:
  Package texlive-latex-extra is not configured yet.
 tetex-extra depends on texlive-lang-norwegian (>= 2007); however:
  Package texlive-lang-norwegian is not configured yet.
 tetex-extra depends on texlive-lang-german (>= 2007); however:
  Package texlive-lang-german is not configured yet.
 tetex-extra depends on texlive-lang-cyrillic (>= 2007); however:
  Package texlive-lang-cyrillic is not configured yet.
 tetex-extra depends on texlive-font-utils (>= 2007-8); however:
  Package texlive-font-utils is not configured yet.
 tetex-extra depends on texlive-lang-finnish (>= 2007); however:
  Package texlive-lang-finnish is not configured yet.
 tetex-extra depends on texlive-pstricks (>= 2007); however:
  Package texlive-pstricks is not configured yet.
 tetex-extra depends on texlive-lang-portuguese; however:
  Package texlive-lang-portuguese is not configured yet.
 tetex-extra depends on texlive-lang-other (>= 2007); however:
  Package texlive-lang-other is not configured yet.
 tetex-extra depends on texlive-bibtex-extra (>= 2007); however:
  Package texlive-bibtex-extra is not configured yet.
 tetex-extra depends on texlive-lang-czechslovak (>= 2007); however:
  Package texlive-lang-czechslovak is not configured yet.
 tetex-extra depends on texlive-math-extra (>= 2007); however:
  Package texlive-math-extra is not configured yet.
 tetex-extra depends on texlive-lang-italian (>= 2007); however:
  Package texlive-lang-italian is not configured yet.
 tetex-extra depends on texlive-publishers (>= 2007); however:
  Package texlive-publishers is not configured yet.
 tetex-extra depends on texlive-lang-dutch (>= 2007); however:
  Package texlive-lang-dutch is not configured yet.
 tetex-extra depends on texlive-lang-hungarian (>= 2007); however:
  Package texlive-lang-hungarian is not configured yet.
 tetex-extra depends on texlive-lang-latin (>= 2007); however:
  Package texlive-lang-latin is not configured yet.
dpkg: error processing tetex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cm-super:
 cm-super depends on tex-common (>= 0.11); however:
  Package tex-common is not configured yet.
 cm-super depends on tetex-base (>= 3) | texlive-latex-recommended; however:
  Package tetex-base is not installed.
  Package texlive-latex-recommended is not configured yet.
 cm-super depends on tetex-extra (>= 3) | texlive-latex-recommended; however:
  Package tetex-extra is not configured yet.
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing cm-super (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-metapost:
 texlive-metapost depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-metapost depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-metapost (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lmodern:
 lmodern depends on tex-common (>= 0.7); however:
  Package tex-common is not configured yet.
dpkg: error processing lmodern (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of context:
 context depends on tex-common (>= 1.4); however:
  Package tex-common is not configured yet.
 context depends on texlive-base-bin (>= 2007); however:
  Package texlive-base-bin is not configured yet.
 context depends on texlive-base (>= 2007); however:
  Package texlive-base is not configured yet.
 context depends on texlive-metapost (>= 2007); however:
  Package texlive-metapost is not configured yet.
 context depends on lmodern (>= 1.01); however:
  Package lmodern is not configured yet.
dpkg: error processing context (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-extra-utils depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of feynmf:
 feynmf depends on tex-common (>= 0.7); however:
  Package tex-common is not configured yet.
 feynmf depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 feynmf depends on texlive-font-utils; however:
  Package texlive-font-utils is not configured yet.
 feynmf depends on texlive-extra-utils; however:
  Package texlive-extra-utils is not configured yet.
dpkg: error processing feynmf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on tetex-extra | texlive-latex-recommended; however:
  Package tetex-extra is not configured yet.
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 pgf depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on pgf (>= 1.00-1); however:
  Package pgf is not configured yet.
 latex-beamer depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 latex-beamer depends on tetex-extra | texlive-latex-base; however:
  Package tetex-extra is not configured yet.
  Package texlive-latex-base is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of musixlyr:
 musixlyr depends on tetex-bin (>= 1.0.5-1) | texlive-base-bin; however:
  Package tetex-bin is not configured yet.
  Package texlive-base-bin is not configured yet.
dpkg: error processing musixlyr (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

```same thing :(

---

### Post by GreTTin on 2008-02-22
I really have no idea how to fix this apart from a fresh install. 

Anyone have any idea's at all? I don't even know what texlive was being installed for it must have been a dependancy for something as I definately wouldn't have looked for it.

if anyone knows how to remove it please help.
Thanks in advance.

---

### Post by GreTTin on 2008-02-22
sorry for replies to replies but it's fixed :D 

I found this thread [http://ubuntuforums.org/showthread.php?t=554229](http://ubuntuforums.org/showthread.php?t=554229)

and used ```
sudo apt-get update && sudo apt-get dist-upgrade
```
and it fixed it somehow not quite sure how but if any one else get's stuck in that loop hope this helps.

also use```
 sudo dpkg --purge -a
``` to let you use dpkg again after it errors.

thanks for help everyone.

---

### Post by gwoodruff on 2008-02-26
I searched high and low for the correct answer to this catch 22. The above post fixed it for me however in the reverse order of posting. 

I ran

```
  sudo dpkg --purge -a
```

and then

```
 sudo apt-get update && sudo apt-get dist-upgrade
```

Thanks to all

---

### Post by clarezoe on 2008-03-25
I got exactly the same wired errors.
I didn't know what did I do, keeping >  sudo dpkg --purge -aand > sudo apt-get update
But it's fine now. Thank goodness.

Is it a bug?!

---

