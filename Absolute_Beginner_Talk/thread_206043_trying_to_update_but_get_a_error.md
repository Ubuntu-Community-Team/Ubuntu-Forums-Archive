---
title: "trying to update but get a error"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by tidy_boy on 2006-06-29
Hi guys I am trying to install automatix but I am getting this error please help

matt@matt-laptop:~$ sudo apt-get update
E: Type &#8216;[ftp://cipherfunk.org/pub/packages/ubuntu/&#8217;](ftp://cipherfunk.org/pub/packages/ubuntu/&#8217;) is not known on line 32 in source list /etc/apt/sources.list


Thanks

---

### Post by harishg on 2006-06-29
Looks like that ftp site might be down.Open the source list file of apt 

sudo gedit /etc/apt/sources.list 

comment the line 32.

---

### Post by tonyr on 2006-06-29
Does that line appear with the **ftp** in your **/etc/apt/sources.list file**, or is 
does the line look in general like all the other repo source lines?

Did you try **ftp**-ing directly, from the command line (or other **ftp** tool)?
Maybe the site really doesn't exist.

---

### Post by Ferri on 2006-06-29
It looks like you have not entered the repository correctly. It should be something like this:

deb [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

---

### Post by tidy_boy on 2006-06-29
Ok that problem is now sorted thanks guys

but when I do sudo apt-get install automatix

I get 

matt@matt-laptop:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package automatix

This is the contents of my /etc/apt/sources.list



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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main



any ideas

---

### Post by arnieboy on 2006-06-29
there are some clear instructions here:
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by tidy_boy on 2006-06-29
I am using that thrad and did everything it said upto the installation part2 and when i run 

matt@matt-laptop:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package automatix


It does not work

---

### Post by arnieboy on 2006-06-29
[QUOTE=tidy_boy]I am using that thrad and did everything it said upto the installation part2 and when i run 

matt@matt-laptop:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package automatix


It does not work[/QUOTE]
it does not work because u cant read (just kidding.. )

add the following line to the end of sources.list
> deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main
save and exit and then do:
```
sudo apt-get update
sudo apt-get install automatix
```

---

### Post by tonyr on 2006-06-29
Add one of these to your repo list:


[B]If you use Dapper, add this: 

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

If you use Breezy, add this:

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) breezy main

Kubuntu users, add this:

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) kubuntu main [/B]

---

### Post by tidy_boy on 2006-06-29
yeah i added that a minute ago and it still does not work same error

---

### Post by arnieboy on 2006-06-29
[QUOTE=tidy_boy]yeah i added that a minute ago and it still does not work same error[/QUOTE]
post the results of 
```
cat /etc/apt/sources.list
```

---

### Post by tidy_boy on 2006-06-29
Sorted Thanks guys

---

