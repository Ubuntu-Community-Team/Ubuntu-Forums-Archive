---
title: "Package Manager Problem"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by maiden30403 on 2006-07-12
Hi I'm having problems with my package manager I get this error

```
E: Type 'http://packages.ubuntu.com/dapper/' is not known on line 25 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Type 'http://packages.ubuntu.com/dapper/' is not known on line 25 in source list /etc/apt/sources.list
E: Unable to lock the list directory
```

Can anyone help with this?

---

### Post by aysiu on 2006-07-12
Can you post the output of this command? ```
cat /etc/apt/sources.list
``` so we can see what's on line 25?

---

### Post by maiden30403 on 2006-07-12
```
## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb http://www.beerorkid.com/automatix/apt dapper main

http://packages.ubuntu.com/dapper/
deb http://ie.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricteddeb http://ie.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

---

### Post by maiden30403 on 2006-07-12
Anyone any ideas. I tried to edit the file but I don't have permissions :-?

---

### Post by aysiu on 2006-07-12
Edit the file with these commands: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources
```

Or to edit with the graphical user interface, read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Every line should start with *deb* or *deb-src* and have something that looks like a web address followed by a word or two.

Delete this line: ```
http://packages.ubuntu.com/dapper/
```
 and make this line into two separate lines: ```

deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricteddeb http://ie.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
```

---

