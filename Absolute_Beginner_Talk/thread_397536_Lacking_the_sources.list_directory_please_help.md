---
title: "Lacking the sources.list directory please help"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-03-30
Someone please help me with this problem:

I'm following a tutorial to "enable extra repositories"
This is what it says..
> sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

I inputed that but got this..
> 
mv: cannot stat `/etc/apt/sources.list': No such file or directory

This is everything I **do** have in the /etc/apt directory..
> 
[LIST=1]
[*]apt.conf  [*]  secring.gpg    [*]      sources.list.d   [*]  trustdb.gpg [*] trusted.gpg~
[*]apt.conf.d  [*]sources.list_backup [*] sources.list.save [*] trusted.gpg
[/LIST]

What do I do?
Do I create a sources_list directory?

---

### Post by .oops on 2007-03-30
You could try making a copy of **sources.list_backup** and rename it to **sources.list**. If the **sources.list_backup** file is empty, and if you really need your own **sources.list**, create one and place the following in it:

```
    deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
    deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

    ## Major bug fix updates produced after the final release of the
    ## distribution.
    deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
    deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

    ## Uncomment the following two lines to add software from the &#8216;universe&#8217;
    ## repository.
    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    ## team, and may not be under a free licence. Please satisfy yourself as to
    ## your rights to use the software. Also, please note that software in
    ## universe WILL NOT receive any review or updates from the Ubuntu security
    ## team.
    deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
    deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

    ## Uncomment the following two lines to add software from the &#8216;backports&#8217;
    ## repository.
    ## N.B. software from this repository may not have been tested as
    ## extensively as that contained in the main release, although it includes
    ## newer versions of some applications which may provide useful features.
    ## Also, please note that software in backports WILL NOT receive any review
    ## or updates from the Ubuntu security team.
    deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
    deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

    deb http://security.ubuntu.com/ubuntu dapper-security main restricted
    deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
    deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
    deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

    ## dapper-commercial by canonical
    ## currently has realplay (realplayer 10) and opera (opera 9)
    deb http://archive.canonical.com/ubuntu dapper-commercial main

    ## Bleeding edge wine repository for Dapper
    ## only uncomment it if you need it
    ## deb http://wine.budgetdedicated.com/apt dapper main
    ## deb-src http://wine.budgetdedicated.com/apt dapper main

    ## skype
    ## only uncomment it if you need it
    ## deb http://download.skype.com/linux/repos/debian/ stable non-free
```

You can also add new repositories by simply going to **System -> Administration -> Synaptic -> Configuration -> Repositories**.

---

### Post by x1a4 on 2007-03-30
*mv* is used to move/rename files.  By following those directions you renamed your _sources.list_ to _sources.list_backup_. Just copy it like so: 

*sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list*

BTW _sources.list_ is a regular file and not a directory

---

