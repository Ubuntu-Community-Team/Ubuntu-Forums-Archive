---
title: "sources.list problem"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by green_is_mean on 2007-09-28
Hi, 

I'm using Ubuntu 6.06, while trying to upgrade using the Synaptic package manager I mistakenly deleted a sources.list file. Now i can't upgade anything and each time i open de SPM it gives me this warning:

E: Malformed line 33 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I've tried looking for info on how to fix the problem but can'T seem to find a way.

Help is very appreciated 
Thanks in advance 

Green_is_mean

---

### Post by llamakc on 2007-09-28
Post the contents of your /etc/apt/sources.list file. On line 33 there's a typo.

---

### Post by southernman on 2007-09-29
> **llamakc said:**
> Post the contents of your /etc/apt/sources.list file. On line 33 there's a typo.

Apparently green managed to delete their sources.list file all together.

@Green- In a terminal (Applications > Accessories > Teminal) do this:

```
ls /etc/apt
```

you should see a file names "sources.list~" and if you do, now just do this:

```
sudo cp sources.list~ sources.list
```

You should be able to run synaptic without problems now.

---

### Post by llamakc on 2007-09-29
So how is apt reporting an error on a specific line if the file is missing? If that's what happened, I've never seen that before. Interesting.

---

### Post by southernman on 2007-09-29
After I hit submit (post quick reply) that dawned on me too. If green did indeed delete the file, when running synaptic it must of used the backup file (with the ~ in the name). If that's the case, then it must of been a borked file, hence the error, hence you would be absolutely, positively, without a doubt correct... it's just a matter of an error on line 33! Whew... pardon the total lack of grammer on that! :p

PS. how is things in the big easy these days?

---

### Post by llamakc on 2007-09-29
Still a mess. Still a cluster#$C% of a mess. You can still get hand grenades on Bourbon though. I guess that's a positive. ;)

---

### Post by zvacet on 2007-09-29
```
cat -n /etc/apt/sources.list | grep 33
```

Post it here.If that doesn´t help you can allways use this 

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")

---

### Post by llamakc on 2007-09-29
> **zvacet said:**
> ```
cat -n /etc/apt/sources.list | grep 33
```Post it here.If that doesn´t help you can allways use this 

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

Learn something everyday. I didn't realize 'cat' could number lines like that. Awesome. Thanks.

---

### Post by green_is_mean on 2007-09-29
Hey guys,

i've tried: [HTML]sudo cp sources.list~ sources.list[/HTML] and the terminal gives mi this [HTML]cp: cannot stat `sources.list~': No such file or directory[/HTML]. but file exist. 

I've tried [HTML]cat -n /etc/apt/sources.list | grep 33 [/HTML] and it gives me [HTML]33  deb http://archive.ubuntu.com/ubuntu[/HTML]

but when i try [HTML]gedit /etc/apt sources.list[/HTML] i get a warning message saying 
[HTML]Could not open the file /etc/apt.[/HTML]

I've looked at my sources.list file and I can't find the error so here is my entire sources.list file. I've cheked the line there are no blank space or typos as far as i know.
I don't really understand what's going on,

[HTML]

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu/ dapper-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe


deb http://archive.ubuntu.com/ubuntu
deb-src http://archive.ubuntu.com/ubuntu
deb http://packages.freecontrib.org/ubuntu/plf
deb-src http://packages.freecontrib.org/ubuntu/plf

/etc/apt/sources.list
/etc/apt/sources.list
/etc/apt/sources.list
/etc/apt/sources.list[/HTML]

---

### Post by green_is_mean on 2007-09-29
For Llamack

i've already checked 
[http://easylinux.info/wiki/Ubuntu_da...a_repositories](http://easylinux.info/wiki/Ubuntu_da...a_repositories) and it doesn't help with my problem since that's what i was doing when i created the problem

---

### Post by Perfect Storm on 2007-09-29
You can set up a new source list from here;
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by southernman on 2007-09-29
Sorry - stupid human pet tricks on my part!

The correct code to copy the backup file from any directory other than the apt directory would be:

```
sudo cp /etc/apt/sources.list~ /etc/apt/sources.list
```

but let's hold off a minute on that and tell me what these lines below come from:

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)

/etc/apt/sources.list
/etc/apt/sources.list
/etc/apt/sources.list
/etc/apt/sources.list

Are those lines you added manually? Notice the difference primarily in the "first" offending line at 33 differs the working line by specifing the "release" you are using:

> deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) [COLOR="Red"]dapper-security main restricted[/COLOR]

2- As for why this code "gedit /etc/apt sources.list" doesn't work. First off, your not linking to the file properly which is "gedit /etc/apt/sources.list"

2.a- Secondly, you aren't opening the file as a root user so any edits you made wouldn't stick when closing the file. Why running gui applications you should append sudo, with gksudo. Therefore the proper code to open that file would look like:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by green_is_mean on 2007-10-01
all these lines were added using the Synaptic package manager so i don't see how they could be wrong

---

### Post by southernman on 2007-10-01
> **green_is_mean said:**
> all these lines were added using the Synaptic package manager so i don't see how they could be wrong
Clearly they are though. 

It's just software.

---

