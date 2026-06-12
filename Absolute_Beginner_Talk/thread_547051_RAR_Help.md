---
title: "RAR Help"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Tootles on 2007-09-09
ok whenever i open a rar file in ubuntu its always empty....
any thoughts?

---

### Post by shae on 2007-09-09
```
sudo apt-get install rar unrar
```

---

### Post by Tootles on 2007-09-09
sergey@sergey-desktop:~$ sudo apt-get install rar unrar
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
sergey@sergey-desktop:~$

---

### Post by shae on 2007-09-09
Then try just:
```
sudo apt-get install unrar
```

If this does not work, post the output of
```
cat /etc/apt/sources.list
```

---

### Post by Tootles on 2007-09-09
sergey@sergey-desktop:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate
sergey@sergey-desktop:~$

---

### Post by shae on 2007-09-09
> **shae said:**
> 
```
cat /etc/apt/sources.list
```
Please post the results of this.

---

### Post by Tootles on 2007-09-09
sergey@sergey-desktop:~$ cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
sergey@sergey-desktop:~$

---

### Post by [Alsharifi] on 2007-09-09
worked for me.


```
sudo apt-get install rar
```

---

### Post by Tootles on 2007-09-09
or maybe i already have rar cause i have rar file on desktop, and it shows the box and blue text that sais rar, but theres nothing in it, it does this for every file

---

### Post by shae on 2007-09-09
There is your problem.  You need to uncomment Universe from your sources.list. 
```
sudo gedit /etc/apt/sources.list
```

Remove the #s from the following four lines:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Add the following lines

 deb  [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse

Then save and exit.

Then
```
sudo apt-get update
sudo apt-get install rar unrar
```

If you have any problems, continue to post.

---

### Post by [Alsharifi] on 2007-09-09
did u try that code?

---

### Post by Tootles on 2007-09-09
sergey@sergey-desktop:~$ sudo gedit /etc/apt/sources.list
sergey@sergey-desktop:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate
sergey@sergey-desktop:~$ sudo gedit /etc/apt/sources.list
sergey@sergey-desktop:~$ sudo gedit /etc/apt/sources.list
sergey@sergey-desktop:~$ sudo apt-get update
E: Type 'deb-rc' is not known on line 8 in source list /etc/apt/sources.list
sergey@sergey-desktop:~$ sudo apt-get install rar unrar
E: Type 'deb-rc' is not known on line 8 in source list /etc/apt/sources.list
E: The list of sources could not be read.
sergey@sergey-desktop:~$

---

### Post by shae on 2007-09-09
Please check to ensure the lines are exactly as I specified.  It seems that you accedently changed one of the deb-src to deb-rc.

---

### Post by Tootles on 2007-09-09
now when i type cat /etc/apt/sources.list
it wont open in a new windows so i cant edit

---

### Post by shae on 2007-09-09
To edit your source file, you need to use:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by Tootles on 2007-09-09
there is no #s

---

### Post by [Alsharifi] on 2007-09-09
yea line 8 of the source list is wrong. deb-rc should be deb-src? 

what u mean no #'s?

---

### Post by niceguy123 on 2007-09-11
> **shae said:**
> ```
sudo apt-get install rar unrar
```

Thanks,

This forum is great ; )

---

### Post by stchman on 2007-09-11
unrar is in the multiverse repository.

---

### Post by Sef on 2007-09-29
> unrar is in the multiverse repository.

Here is how to add [multiverse]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

