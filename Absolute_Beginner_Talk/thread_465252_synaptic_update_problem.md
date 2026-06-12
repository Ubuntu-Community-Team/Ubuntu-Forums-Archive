---
title: "synaptic update problem"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by matt_tee on 2007-06-05
when i try to access synaptic package manager i receive this error:

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type ‘“deb’ is not known on line 39 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

any ideas how to resolve?

thanks in advance

---

### Post by taurus on 2007-06-05
There is something wrong with line 39 in your /etc/apt/sources.list.  You need to either edit it

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
or post it here.

```
cat /etc/apt/sources.list
```

---

### Post by phr0ze on 2007-06-05
I would open /etc/apt/sources.list and look at line 39 to see if anything looks a little strange. Either way make a copy of the file and fix or remove line 39.

---

### Post by sread on 2007-06-05
Hi, It looks like you might have an error in your sources list? This might not be very helpful, but try opening /etc/apt/sources.list and look to see if anything looks out of place on line 39. I'm not at an Ubuntu computer right now, but if you post your line 39 I (or someone else maybe) can check against a working copy.

---

### Post by matt_tee on 2007-06-05
thanks for quick reply, here it is:


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates multiverse universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-security multiverse
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”

---

### Post by taurus on 2007-06-05
You ought to remove the last two lines in your /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
Save the change and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Seisen on 2007-06-05
Delete these lines 

```
“deb http://www.getautomatix.com/apt edgy main”
“deb http://www.getautomatix.com/apt feisty main”

```

---

### Post by matt_tee on 2007-06-05
thanks, that worked

---

### Post by taurus on 2007-06-05
> **matt_tee said:**
> thanks, that worked

If you need to install codecs for multimedia, here's a link for you.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by sread on 2007-06-05
Also, if you're the curious type, the reason those lines weren't working was due to the quotation marks. Thus the syntax error.

---

### Post by taurus on 2007-06-05
> **sread said:**
> Also, if you're the curious type, the reason those lines weren't working was due to the quotation marks. Thus the syntax error.

And a bigger problem was the wrong release version.

---

