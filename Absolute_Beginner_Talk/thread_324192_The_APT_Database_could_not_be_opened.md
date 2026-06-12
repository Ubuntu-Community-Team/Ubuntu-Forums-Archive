---
title: "The APT Database could not be opened"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by naponos on 2006-12-23
Hallo, I was trying to put new repositories on adept,  to install picasa2, but I got the following information: 

The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

I tried to apply a few solutions (found on internet) but they didn't work.
I was only able to write the following note :

deb http ://dl.google.com/linux/deb/ stable non-free 
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted 
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe 
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 


Bear in mind that I'm just a beginner with linux.

Kind regards, Alessandro

---

### Post by jvc26 on 2006-12-23
Hi there - which repos do you have to add to put picasa on?

You can do this from the command line with:
```

gksudo gedit /etc/apt/sources.list

```

Then replace the sources.list with the one from here (it is a trusted list, off psychocats)
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
This above link will also help as it is a walkthough on HOWTO add extra repos.

To add your picasa ones you would just trot down to the bottom of the list and add:
```

##Repos for picasa
**The URL for the picasa repo**

```

Then save and close, go back to terminal and type

```

sudo apt-get update

```

Which will look through the repos that you have in your list and then update the packages list in synaptic. and then you should be able to install picasa.

Have I got the wrong end of the stick or is this what you're after
:)
Il

---

