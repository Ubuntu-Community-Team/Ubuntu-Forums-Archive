---
title: "[SOLVED] tring to install VMplayer"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-14
i get this error when i try to install it

$ sudo ./vmware-install.pl
sudo: ./vmware-install.pl: command not found

the file is placed on my desktop and i do know what to do to get around it

---

### Post by Linux_Man on 2008-02-14
Are you downloading it off of VMware's site or Via the Ubuntu repositories? I'm rather sure its in the repositories under the "third party software" tab.

EDIT: Also, are you sure that file is marked executable? Because if not its not going to do anything if you try to run it.

---

### Post by PeterJS on 2008-02-14
Did you cd to your Desktop before trying to install it? By default new terminals open up in your home directory.

And as stated above it'd be easier just to install vmware from the partner repository,

---

### Post by articwolf939 on 2008-02-14
i cant find the third party resportites  apt line so i couldnt find it  and yes i did cd to the desktop but i cant figgure out how to cd to the file but yea any more ideas

---

### Post by PeterJS on 2008-02-14
Here's the sources line for the Canonical comercial repo
```

#Canonical
deb http://archive.canonical.com/ubuntu gutsy partner

```

---

### Post by articwolf939 on 2008-02-14
if they work u are now my hero :) thx ALOT

---

