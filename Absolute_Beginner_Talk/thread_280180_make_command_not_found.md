---
title: "make: command not found"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by timvets on 2006-10-19
I'm on a new ubuntu dapper installation
I need t compile a program
I go to the locaton where the source files are extracted

I do:
sudo make

I get:
sudo: make: command not found

can't find make in synaptic

sudo apt-get install make
gives:

Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

'make' being such a common word makes it hard to find specific info on 'make' as in 'sudo make'...

thanks

---

### Post by Tamil on 2006-10-19
Try after running this

```
sudo aptitude install build-essential
```

---

### Post by StormNet on 2006-10-19
You are going to need the build-essential
> sudo apt-get install build-essential
That should add make for you.

---

### Post by Arby on 2006-10-19
I think that means you don't have make installed. In Synaptic it's bundled as a metapackage with some other compiling type stuff. I think the package is called buildutils or similar but I'm not in front of my ubuntu system at the moment so I can't check

Edit: too slow

---

### Post by Sef on 2006-10-19
To compile, you need to download build-essential.  

Applications > Accessories > Terminal

sudo aptitude update

sudo aptitude install build-essential

---

### Post by timvets on 2006-10-19
sudo aptitude install build-essential

returns:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

thanks

---

### Post by timvets on 2006-10-19
sudo apt-get build essential
returns :

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by timvets on 2006-10-19
now when I tried

sudo apt-get build-essential

again, it just says :

E: Invalid operation build-essential

---

### Post by hajk on 2006-10-19
Read carefully those instructions... in a terminal type

sudo apt-get install build-essential

(also make sure that you don't use this command while synaptic is still running).

---

### Post by Sef on 2006-10-19
```
sudo apt-get install build-essential
```

```
sudo aptitude install build-essential
```

Aptitude is a more updated version of apt-get.  The difference is that if you uninstall, aptitude will uninstall the dependencies as well which apt-get won't.

---

### Post by devnulljp on 2006-10-19
> **timvets said:**
> now when I tried

sudo apt-get build-essential

again, it just says :

E: Invalid operation build-essential

1. The lock problem above is because you have synaptic (or adept or sthg) running and you're trying to run apt from the command line. So, quit synaptic first. Then go to the terminal.
2. the problem above is because you missed the actual instruction for apt
type 

```
sudo apt-get **install** build-essential

```

---

### Post by timvets on 2006-10-19
ok synaptic was running in the background,
closed and tried:

sudo apt-get install build-essential

Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

thanks
Tim

---

### Post by devnulljp on 2006-10-19
Sounds like you haven't got the right repositories.
You need to add universe & multiverse (see [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories))
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list
```

Can you see lines something like these?
```
#deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
```

Delete those # marks then:
```
sudo apt-get update
sudo apt-get install build-essential
```

---

