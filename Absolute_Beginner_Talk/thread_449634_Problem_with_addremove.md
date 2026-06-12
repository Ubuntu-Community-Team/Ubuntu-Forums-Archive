---
title: "Problem with add/remove"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by HieroPosche on 2007-05-20
Complete noob at linux here :)

Was trying to install wine following the howto and after entering:

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

I can't run the add/remove applications program anymore. I get an error message saying.

Failed to check for installed and available applications.

It says to check for broken pakages with synaptic, but when I try to open that I get:

E: Type '--13:30:37--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I think maybe I need to just delete the winehq.list and run the command again? But I don't want to botch anything more than I may already have.

Any ideas on what I ought to do would be mighty helpful.

---

### Post by finer recliner on 2007-05-20
make a backup of your sources.list file before editing it:

```

$sudo cp sources.list sources.list.bck

```

now delete that one line.

if you need to refer back to backuped copy for whatever reason:
```

$sudo cp sources.list.bck sources.list
//^ this will overwrite the sources.list file with the backed up copy.

```


i recommend backing up any system files before editing them (i.e. fstab, xorg.conf, etc)

---

### Post by abhishek456 on 2007-05-20
i don't know why that extra /winehq.list is linked to sourcess.list

Ok you can create a fresh sources.list file and put it in your /etc/apt directory

You can generate new sourcelist here [http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/")

You can also see the backed sourcelist in same directory > sources.list.save

---

### Post by HieroPosche on 2007-05-20
Awesome thanks guys.

---

### Post by YokoZar on 2007-05-20
> **finer recliner said:**
> make a backup of your sources.list file before editing it:

```

$sudo cp sources.list sources.list.bck

```

now delete that one line.

if you need to refer back to backuped copy for whatever reason:
```

$sudo cp sources.list.bck sources.list
//^ this will overwrite the sources.list file with the backed up copy.

```


i recommend backing up any system files before editing them (i.e. fstab, xorg.conf, etc)There was nothing wrong with the sources.list file in the first place - the command places a secondary list file alongside it, which in this case was malformed.

You should just be able to run the command again to overwrite the (malformed) winehq.list.

---

### Post by HieroPosche on 2007-05-20
Ran the command again, it did overwrite, but still having the same problem.

---

### Post by bapoumba on 2007-05-20
Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by HieroPosche on 2007-05-20
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by bapoumba on 2007-05-20
Looks fine.
What is the output to:
```
sudo aptitude update
```

---

### Post by HieroPosche on 2007-05-20
E: Type '--14:43:37--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: Couldn't read list of package sources

---

### Post by bapoumba on 2007-05-20
```
ls /etc/apt/sources.list.d/
```
Should be empty.

if a file winehq.list is there:
```
sudo rm /etc/apt/sources.list.d/winehq.list
```

Before you remove, you can copy the file to your /home if you wish
```
cp /etc/apt/sources.list.d/winehq.list winehq.list 
```

---

### Post by HieroPosche on 2007-05-20
Fantastic it works again thank you very much.

---

### Post by bapoumba on 2007-05-20
Glad to see you back on tracks :)

---

