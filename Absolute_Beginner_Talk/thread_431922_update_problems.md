---
title: "update problems"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by aliov_85 on 2007-05-03
Hello every body.

I'm a new friend of you in the community...

When i try to update I get this message:

E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)

can anyone help me please?

---

### Post by jfinkels on 2007-05-03
> **aliov_85 said:**
> Hello every body.

I'm a new friend of you in the community...

When i try to update I get this message:

E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)

can anyone help me please?

Can you please post the output of this command: ```
cat /etc/apt/sources.list
```

---

### Post by starcraft.man on 2007-05-03
Sounds like there is a problem with your sources list. Easy to fix.

Type this into terminal: (Terminal is Applications > Accessories > Terminal)

```
sudo gedit /etc/apt/sources.list
```

Then copy and paste the contents of the text window here.

Probably just a little error in the line.

---

### Post by aliov_85 on 2007-05-03
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy restricted

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-backports restricted multiverse

deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-security restricted multiverse
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-backports restricted multiverse

##man ino add kardam
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy restricted multiverse

deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-proposed multiverse restricted

---

### Post by jfinkels on 2007-05-03
That looks okay...but we both made a mistake. That's not where the error is. The error is in this file /etc/apt/sources.list.d/edgy-multiverse.list .

Could you post the contents of that file?

I don't know why you have that file at all, it's unnecessary, but let's just see what it is :D

---

### Post by starcraft.man on 2007-05-03
> **jfinkels said:**
> That looks okay...but we both made a mistake. That's not where the error is. The error is in this file /etc/apt/sources.list.d/edgy-multiverse.list .

Could you post the contents of that file?

I don't know why you have that file at all, it's unnecessary, but let's just see what it is :D

ROFL!!! Silly little d... HAX! and we both missed it, arrrg, I must need new glasses....

---

### Post by aliov_85 on 2007-05-03
Hello, thanks my friend,

# automatically added by gnome-app-install on 2007-01-28 11:29:50.329841
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates

---

### Post by jfinkels on 2007-05-03
> **aliov_85 said:**
> Hello, thanks my friend,

# automatically added by gnome-app-install on 2007-01-28 11:29:50.329841
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates

Okay, I think you do not need this file at all. Type this command, then run "sudo aptitude update" again and see what happens.

```

sudo mv /etc/apt/sources.list.d/edgy-multiverse.list /etc/apt/sources.list.d/edgy-multiverse.list.backup

```

All we're doing here is renaming the file, so that it won't be used (hopefully). Let me know how this goes.

---

### Post by aliov_85 on 2007-05-03
:popcorn: :guitar: :lolflag: 

Thank you jfinkels , I had success with your help.  so thanks

Can u just tell what was the problem to get experience of that error

See you soon

---

