---
title: "Can't update with update manager"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by kudos1uk on 2008-02-21
I'm having a problem with updates and have done for some time now.

Using xubuntu 7.10 - Gutsy

If I update via update manager, I click update and it just churns forever, it does not ask for a password and I have to end up killing update manager.

To update I have to go to terminal and type:

**sudo update-manager**

It then asks me for my password which I enter, I then get the following warning:

**Warning: could not initiate dbus**

Update manager then launches and does a full update without a problem.

I think the issue is that I don't get asked for a password unless I use terminal. The only other thing I notice is that if I use update manager it only offered one update but when I launch it via terminal I see all the updates.

Any ideas why this is an issue?

---

### Post by kpkeerthi on 2008-02-21
Can you try updating from command line using the below commands in sequence?
```
sudo aptitude update
```
```
sudo aptitude dist-upgrade
```

And then see if the problem goes away when using **update-manager**. 

Also I suggest using [gksudo ]("http://www.psychocats.net/ubuntu/graphicalsudo")while launching graphical applications with super-user privileges, as in 
```
gksudo update-manager
```

---

### Post by kudos1uk on 2008-02-21
Thanks for helping with this,

**sudo aptitude update**

All went ok but the following errors:

> bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/main Packages                   
  Sub-process bzip2 returned an error code (2)


> Fetched 70.0kB in 9s (7467B/s)                                                 
Reading package lists... Done
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_gutsy-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_gutsy-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
tony@tony-laptop:~$ 



I ran apt-get update as it said but made no difference, same result.

Next:
**sudo aptitude dist-upgrade**


again OK with the following errors:

> 32 packages upgraded, 2 newly installed, 10 to remove and 0 not upgraded.
Need to get 62.7MB of archives. After unpacking 6869kB will be freed.
The following packages have unmet dependencies:
  mplayer: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is installed.
  scim-hangul: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is installed.
  libpoppler-glib2: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
mplayer

Keep the following packages at their current version:
libpoppler-glib2 [0.6-0ubuntu2 (gutsy, now)]
scim-hangul [0.2.2-2ubuntu3 (gutsy, now)]

Score is 201

Accept this solution? [Y/n/q/?] y



Its still working away and not yet complete so will just post this update and post again when its complete, thanks again for your help.

---

### Post by macogw on 2008-02-21
Post a copy of your /etc/apt/sources.list  You have some lines repeated is all.

---

### Post by kudos1uk on 2008-02-21
**kpkeerthi**
Thanks, I just did my first update from update-manager without having to go into terminal. Your advice looks like it did the trick, thanks :)

**macogw**
Here is a copy of sources.list:

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports restricted universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free


---

### Post by kpkeerthi on 2008-02-21
Is that all you have in sources.list? Something seems to be not right at your end.

I suggest you use [this]("http://www.psychocats.net/ubuntu/sources#gutsy") and then update and dist-upgrade as state above.

---

### Post by kudos1uk on 2008-02-21
Many thanks, I have updated everything.

I can't test it now as there are no more updates but as it all worked well earlier I think you have helped me fix it all.

Thanks again Tony :)

---

### Post by kudos1uk on 2008-02-22
Hi again,

Having done a lot of testing this is really wierd.

If I update by clicking on the update manager in the menu, it finds the updates but when I click "update" the timer comes up but wont go any further, it never asks for my passwork and I have to kill update manager.

Here is the wied bit, if I start update manager from the task bar (the notification icon) or in terminal everthing goes fine, it asks my password and the update completes.

---

