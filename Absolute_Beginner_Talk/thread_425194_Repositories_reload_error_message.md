---
title: "Repositories reload error message"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by rufousfelix on 2007-04-27
I get the following error message when I try to reload the repositories in Synaptic Package Manager (also when running sudo aptitude update):

"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

and this in the specific error message box:

"http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)"

I've been getting this message for about a week after I reinstalled ubuntu.  Before, I didn't get this message.  I've looked at the sources.list & that seems okay, but would like suggestions on what else to check out or whether just to ignore the message.  Someone else asked this question, but I think the issue is unresolved.  Thanks.

---

### Post by taurus on 2007-04-27
Open a terminal and edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from your repos.  Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by rufousfelix on 2007-04-28
Thanks, taurus.  Those terminal commands worked like a charm!

---

