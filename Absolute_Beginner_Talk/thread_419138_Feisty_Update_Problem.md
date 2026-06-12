---
title: "Feisty Update Problem"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-04-22
Hi:
I;ve been trying to update with the update manager and have got about 1000 files so far.  The download has timed out a few times saying connection refused.  So I just try again and have been able to continue up to this point.

Now update manager won't run, and there is a message in the update notifier of: an error occured.  Error: Opening the cache (E:Malformed line 2 in source list /etc/apt/sources.list (URI parse), (E:Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (URI parse)

This is what the beginning of those files look like.  I don't see anything wrong, but am not very familiar with linux:

/etc/apt/sources.list

deb None edgy main restricted
deb-src None edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
## deb None edgy-updates main restricted
deb-src None edgy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe


/etc/apt/sources.list.d/edgy-universe.list 

# automatically added by gnome-app-install on 2007-02-15 21:24:58.991773
deb None edgy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb None edgy-updates universe

What do I do?

Thanks,
Ziffnabb

---

### Post by mabelrxu on 2007-04-22
hm .... this'll probably break it further, but try this:

first, use cp to make a backup
cp /etc/apt/sources.list.d/edgy-universe.list /etc/apt/sources.list.d/edgy-universe.list.backup

next, open up /etc/apt/sources.list.d/edgy-universe.list in a text-editor and change that address to None to match the others ... see what happens ... if it breaks, then just copy it back using that cp command, except backwards

---

### Post by ziffnabb on 2007-04-22
Hi mabelrxu:

Tried that.  It did not make any difference.  

Thanks,
Ziffnabb

---

### Post by Seisen on 2007-04-22
You need to comment these lines out or fix them

```

deb None edgy main restricted
deb-src None edgy restricted main multiverse universe #Added by software-properties
```

```
deb-src None edgy-updates restricted main multiverse universe #Added by software-properties
```

```
/etc/apt/sources.list.d/edgy-universe.list 
```

```
deb None edgy universe
deb None edgy-updates universe
```

This will help you create a better source list.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by ziffnabb on 2007-04-22
Thanks Seisen

That seemed to do it.  I got similar errors for different line numbers, they were 43, 45 & 47.  I commented them out as well and did an apt-get update.  Now if I can just finish my Feisty upgrade!

Ziffnabb

---

