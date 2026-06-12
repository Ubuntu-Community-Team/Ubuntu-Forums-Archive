---
title: "Updrage Problem"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by WaveMyBlackFlag on 2007-04-13
Okay, so i try to run updates through terminal using apt-get

This is what I've been getting:
----
Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  samba: Depends: samba-common (= 3.0.22-1ubuntu3.1) but 3.0.22-1ubuntu3.2 is installed
E: Unmet dependencies. Try using -f.
----

so I do and get:

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following packages will be REMOVED
  samba
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 142962 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
----

So who has any idea as to what I need to do here?  I'd really like to update/upgrade if I could!!

---

### Post by Seisen on 2007-04-13
Try doing this
```
sudo dpkg --configure -a
sudo apt-get -f install
```

Let us know if that works if not we will try to figure it out.

---

### Post by WaveMyBlackFlag on 2007-04-14
Done and done:  I also changed my repositories -  looks like i had the Fiesty CD-Rom listed in there also for some reason... so i removed that and all the dapper repos, re-added them and I get this now instead


Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  samba
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 52 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 142936 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

It almost seems as if I have a newer version of samba than I should, yea - nay??

some of the same lines, but new "fun" ones i haven't seen before.

For the record, the Idea of a "dangling symlink" is pretty funny, to me...

---

### Post by caffienefree on 2007-04-14
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/48082](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/48082)

Try removing the symlink by **sudo rm -rf /etc/rc2.d/S91samba**

---

### Post by WaveMyBlackFlag on 2007-04-15
Bingo.

Thanks all.

---

### Post by celticmonkey on 2007-05-17
I had the same problem exactly. Removing that symlink seems to have done the trick. The package manager is working again!

---

