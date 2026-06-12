---
title: "unrar issues"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by niteblind on 2007-10-06
Hi All,

I am trying to use hellanzb which requires me to install unrar. Not an issue thinks I as I was using this before I reinstalled the OS fine no issues. However. now I cannot find it!

I am using Dapper and on the repositories I am only finding unrar-free which I tried to install but hellanxb bombs out when trying to unrar the files at the end.

Does anyone know what happened to unrar? Is it on another repositoy that is not in the standard list as I hvae akready uncommented on the ones in the sources.list file and it still isnt there.

niteblind

---

### Post by taurus on 2007-10-06
Make sure you uncomment by removing the # in /etc/apt/sources.list for both universe and multiverse repos.  Then, update it and see if you can install the unrar version now.

---

### Post by ryanVickers on 2007-10-06
My RAR maker script comes with a feature to check if unrar is installed, and if not lets you add it... (signature)

---

### Post by Frak on 2007-10-06
Goto
System->Administration->Software Sources
And check backports, Universe, and Multiverse

Then try again

---

### Post by niteblind on 2007-10-07
this is my sources.list file, I know that I am blind so I might be missing something but as far as I can see universe and multiverse are uncommented. Can someone just confirm that unrar is still in the repos? I need to reinstall anyways as I just screwed the OS (:p). So maybe this will sort itself out after I try again.


deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


niteblind

---

### Post by williamwade on 2007-10-07
just open terminal and type
```
sudo apt-get install unrar
```
and
```
sudo apt-get install rar
```

that worked for me

---

### Post by DoruHush on 2007-10-07
The unrar application belong to the mulitiverse repositoties.
You don't have this repositories enabled.
Do that and it will work.
Note: It is not the same with the backport multiverse. 
You should enable the dapper multiverse repositories.

Edit: It should look something like that:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper multiverse

Edit: No need to install the rar application because it is shareware, and after some time you 
will not be able to use the feature of rar archives creation. After the trial period expire
you only can to use the unrar function, but you still have the whole rar application
installed on tour computer (but unable to use the rar function). 
The unrar application it is available for free from the rar team. This application
perform the unrar task because it is the same feature that is included în rar program.

If you choose to install both rar and unrar applications you will have in the end 
two unrar applications installed on your PC (for no reason).

---

