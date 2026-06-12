---
title: "unable to undo change in package manager"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by ststelly on 2008-04-15
First time poster. I have been unable to get my server settings correct on this version of kubuntu 7.10, but that is not my immediate problem. I still have internet access through windows. My problem is that I downloaded several packages to help me setup kubuntu, and transfered them through a thumb drive to the Linux desktop. I then tried to get the package manager to find the files on the desktop (didn't work) The next time I tried to open the manager it told me I had an unknown on line 74 in source list /etc/apt/sources.list.  I opened that file after reading a similar post  on this site, and tried to correct it by adding a # in front of line 74 (line 74 just has /desktop...where I had told the manager to look) I then tried to save the file, but it would not allow the file to be saved.  Any ideas? I only loaded kubuntu last week, and have been unable to do very much to date.

---

### Post by Inxsible on 2008-04-15
you need to use root privs to be able to save that file.

---

### Post by bwang on 2008-04-15
You need to be root to edit sources.list

```
sudo kate /etc/apt/sources.list
```

---

### Post by ststelly on 2008-04-15
Worked like a charm. My first lesson in Linux. Thanks much!!:)

---

