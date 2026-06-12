---
title: "list of source could not be read"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by edison118 on 2007-06-07
I'm getting the following error message

A error occurred please run package Manager from the right click menu or apt-get pm a terminal to see what is wrong. The error message was: 'Error: Opening the cache (E: Type --06:06:44--" is not known on line 1 in source list /etc/apt/sources.list.d/mediduntu.list, E:The list of sources could not be read.)'

When I run the package manager I got the following error message.

E: Type '--06:06:44--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Pls help me. I'm new to Linux.

thanks

---

### Post by wpshooter on 2007-06-07
My suggestion would be that you go to **software sources ** under SYSTEM/ADMINISTRATION and then make sure every repository (including universe & multi-universe) that you want are checked and then reload when you exit the diagonal, then reboot the computer and then try your operation again.

Good luck.

---

### Post by taurus on 2007-06-07
There is something wrong with the first line of /etc/apt/sources.list.d/medibuntu.list.  So, you need to either fix it or post it here.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by edison118 on 2007-06-07
when I typed this command " gksudo gedit /etc/apt/sources.list.d/medibuntu.list" I got the following message

--06:06:44--  [http://medibuntu.sos-sts.com/sources.lists.d/feisty.list](http://medibuntu.sos-sts.com/sources.lists.d/feisty.list)
           => `feisty.list'
Resolving medibuntu.sos-sts.com... 81.169.138.125, 88.191.13.100, 88.191.26.58, ...
Connecting to medibuntu.sos-sts.com|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
06:06:44 ERROR 404: Not Found.

---

### Post by taurus on 2007-06-07
> **edison118 said:**
> when I typed this command " gksudo gedit /etc/apt/sources.list.d/medibuntu.list" I got the following message

--06:06:44--  [http://medibuntu.sos-sts.com/sources.lists.d/feisty.list](http://medibuntu.sos-sts.com/sources.lists.d/feisty.list)
           => `feisty.list'
Resolving medibuntu.sos-sts.com... 81.169.138.125, 88.191.13.100, 88.191.26.58, ...
Connecting to medibuntu.sos-sts.com|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
06:06:44 ERROR 404: Not Found.

:confused:

Can you post this then?

```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by edison118 on 2007-06-07
--06:06:44--  [http://medibuntu.sos-sts.com/sources.lists.d/feisty.list](http://medibuntu.sos-sts.com/sources.lists.d/feisty.list)
           => `feisty.list'
Resolving medibuntu.sos-sts.com... 81.169.138.125, 88.191.13.100, 88.191.26.58, ...
Connecting to medibuntu.sos-sts.com|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
06:06:44 ERROR 404: Not Found.

---

### Post by taurus on 2007-06-07
You need to edit /etc/apt/sources.list.d/medibuntu.list and remove all the lines in there.

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```
Otherwise, you should remove it completely.

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by edison118 on 2007-06-07
I did so 

when I typed "sudo aptitude update" I got This message 
E: Type 'multiverse' is not known on line 6 in source list /etc/apt/sources.list
E: Couldn't read list of package sources

when I typed "sudo aptitude upgrade" I got this message

E: Type 'multiverse' is not known on line 6 in source list /etc/apt/sources.list
E: Type 'multiverse' is not known on line 6 in source list /etc/apt/sources.list
E: The list of sources could not be read.

when I typed "gksudo gedit /etc/apt/sources.list" I got the following message

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main 
multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu

when I type "cat /etc/apt/sources.list" I got the following message

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main 
multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security multiverse

---

### Post by taurus on 2007-06-07
> **edison118 said:**
> I did so 

when I typed "sudo aptitude update" I got This message 
E: Type 'multiverse' is not known on line 6 in source list /etc/apt/sources.list
E: Couldn't read list of package sources

when I typed "sudo aptitude upgrade" I got this message

E: Type 'multiverse' is not known on line 6 in source list /etc/apt/sources.list
E: Type 'multiverse' is not known on line 6 in source list /etc/apt/sources.list
E: The list of sources could not be read.

when I typed "gksudo gedit /etc/apt/sources.list" I got the following message

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
[COLOR="Blue"][B]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main 
multiverse universe #Added by software-properties
[/B][/COLOR]
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu



Those two lines should be one line.

```
gksudo gedit /etc/apt/sources.list
```

```
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties
```

---

### Post by edison118 on 2007-06-07
thank you very much. it worked.

you r realy genius

Can I get ur email ID. My ID is [EDIT]not a good idea to include your e-mail here.[/EDIT]

---

