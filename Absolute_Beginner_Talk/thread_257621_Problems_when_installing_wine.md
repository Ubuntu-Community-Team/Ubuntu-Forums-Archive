---
title: "Problems when installing wine"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by khorlick on 2006-09-14
I get the error...

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

libwine:
  Depends: wine but it is not installable

I am trying to install through Synaptic using the method at [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

Anyone know what i am doing wrong?

---

### Post by x64Jimbo on 2006-09-14
Please post your sources file
/etc/apt/sources.list

---

### Post by khorlick on 2006-09-14
> Please post your sources file
/etc/apt/sources.list

How do i do that. I cant find my sources file?

---

### Post by mitch.c on 2006-09-14
> **khorlick said:**
> How do i do that. I cant find my sources file?
Umm. That was your sources list... /etc/apt/sources.list ;)

---

### Post by mcmillanje on 2006-09-14
go applications >> accessories >> terminal.

then, in the terminal type:
```
sudo gedit /etc/apt/sources.list
```

copy and paste into this thread,

exit gedit w/o saving

(assuming you have regular ubuntu DD.)

---

### Post by khorlick on 2006-09-14
thank you mcmillanje, and yes i have regular ubuntu with DD's :D 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by mcmillanje on 2006-09-14
add this to the end (same process/commands, just save afterward)

```
deb http://wine.budgetdedicated.com/apt dapper main
```

the deb-src one is the development stuff, not the actual files...

---

### Post by khorlick on 2006-09-15
Now i get this when trying to reload synaptic

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:) 404 Not Found

any thoughts?

---

### Post by Najand on 2006-09-15
Wine is available at Ubunutu's official Repositories (Universe). There is no need to add  a new one.
Click on System -> Administration -> Software Properties and check all unchecked options. (Uncheck [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)... though)
Then Click System -> Administration -> Synaptic Package Manager
And click on "Reload"
Now you can see "Wine" is available there.

Right Click on it and select "Mark for installation" Then Click "Apply"

---

### Post by mikemunro1 on 2006-10-15
Quote: Re: Problems when installing wine
Wine is available at Ubunutu's official Repositories (Universe). There is no need to add a new one.
Click on System -> Administration -> Software Properties and check all unchecked options. (Uncheck [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)... though)
Then Click System -> Administration -> Synaptic Package Manager
And click on "Reload"
Now you can see "Wine" is available there.

Right Click on it and select "Mark for installation" Then Click "Apply"
 
](*,) Hi , I am having some problems with Wine as well; have carried out all the instructions as quoted above and have d/loaded the Wine files..........BUT what do I do next??? I have some learning difficulty and this has escaped from me completely! Please point me in the right direction....Thanks
Mike

---

