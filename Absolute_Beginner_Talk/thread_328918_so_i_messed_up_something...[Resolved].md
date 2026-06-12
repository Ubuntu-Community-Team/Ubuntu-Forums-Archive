---
title: "so i messed up something...[Resolved]"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by andrewpb on 2006-12-31
earlier today i tried installing wine but to no avail, i found a post [http://www.ubuntuforums.org/showthread.php?t=328192&highlight=wine](http://www.ubuntuforums.org/showthread.php?t=328192&highlight=wine) that seemed to describe the same problem, so i went through and unchecked the boxes on the repositories in synaptic, and now i can't access add/remove, automatix, or synaptic package manager.  needless to say it seems as though it didn't work.

in synaptic this is the error message that pops up
E: Type 'http://wine.budgetdedicated.com/apt' is not known on line 50 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Type 'http://wine.budgetdedicated.com/apt' is not known on line 49 in source list /etc/apt/sources.list
E: Unable to lock the list directory

if someone could help me i would appreciate it, also i am very grateful for those who help, however could you explain what happened and why the way to fix it works, i think that will help me in the future.

thanks

---

### Post by meng on 2006-12-31
Please:
cat /etc/apt/sources.list

---

### Post by taurus on 2006-12-31
After you uncommented those lines out ([http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)) in /etc/apt/sources.list, did you remember to click the update list or ran it from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
```
Otherwise, post you /etc/apt/sources.list here then.

```
cat /etc/apt/sources.list
```

---

### Post by andrewpb on 2006-12-31
so i tried this

sudo aptitude update

and it came up with this

E: Type 'http://wine.budgetdedicated.com/apt' is not known on line 49 in source list /etc/apt/sources.list
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Type 'http://wine.budgetdedicated.com/apt' is not known on line 49 in source list /etc/apt/sources.list
E: The list of sources could not be read.

when i unchecked the stuff i did do the reload thing, and if i remember correctly that's when it started acting all funny...now what should i do?  danka

---

### Post by meng on 2006-12-31
cat /etc/apt/sources.list
(sheesh! :) )

---

### Post by andrewpb on 2006-12-31
i did the cat /etc/apt/sources.list command and now should i follow those directions?

---

### Post by taurus on 2006-12-31
Post your /etc/apt/sources.list here!!!

---

### Post by andrewpb on 2006-12-31
cat /etc/apt/sources.list

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START


deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted#AUTOMATIX REPOS END
[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)


is this what you need

thanks again

---

### Post by taurus on 2006-12-31
You have two extra lines for automatix!!!

```

deb http://www.getautomatix.com/apt dapper main
deb http://www.getautomatix.com/apt dapper main

```
Then, the last line is not even right; and that's why you got the error message in your original post...

```

http://wine.budgetdedicated.com/apt

```
So, you need to edit your /etc/apt/sources.list and fix those two problems...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Remove those three things that I showed above and save it.  Then, run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by andrewpb on 2006-12-31
so i removed those two lines and saved, i then tried 

sudo aptitude update

it then gave me this

E: Type 'http://wine.budgetdedicated.com/apt' is not known on line 47 in source list /etc/apt/sources.list
E: Type 'http://wine.budgetdedicated.com/apt' is not known on line 47 in source list /etc/apt/sources.list
E: The list of sources could not be read.


thanks again

---

### Post by taurus on 2006-12-31
You need to delete the last line in your /etc/apt/sources.list as well, [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)!  Or you HAVE to put "deb" in front of it...

```
deb http://wine.budgetdedicated.com/apt
```
Then, run

```
sudo aptitude update
sudo aptitude upgrade
```

p.s.   My previous post did mention to remove that last line from your /etc/apt/sources.list as well, [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)!!!

---

### Post by meng on 2006-12-31
> **taurus said:**
> You need to delete the last line in your /etc/apt/sources.list as well, [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)!  Or you HAVE to put "deb" in front of it...
I think you mean
```
deb http://wine.budgetdedicated.com/apt **dapper main**
```

---

### Post by andrewpb on 2006-12-31
thank you very much, everything seems to back to normal

i got to say even though i've messed up several times with ubuntu, i like it better all ready!

---

