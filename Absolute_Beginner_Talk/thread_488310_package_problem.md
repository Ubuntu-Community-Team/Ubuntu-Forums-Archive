---
title: "package problem"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-06-30
whent i type these commands:

```
apt-get install
apt-gt update
```

i get:

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

any help is good

ta,
Nolander

---

### Post by reverend_HH on 2007-06-30
im pretty new to this too but i think u gotta run it as root, so just type in "sudo" before the "apt-get" part then enter password

---

### Post by avik on 2007-06-30
I looks to me more than a permissions issue.  Can you post your /etc/apt/sources.list file?

---

### Post by Nolander on 2007-06-30
```
 ## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

##All iinet local mirrors

deb http://ftp.iinet.net.au/pub/ubuntu/ edgy main restricted universe multiverse
deb-src http://ftp.iinet.net.au/pub/ubuntu/ edgy main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://ftp.iinet.net.au/pub/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://ftp.iinet.net.au/pub/ubuntu/ edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://ftp.iinet.net.au/pub/ubuntu/ edgy-security main restricted universe multiverse
deb-src http://ftp.iinet.net.au/pub/ubuntu/ edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://ftp.iinet.net.au/pub/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ftp.iinet.net.au/pub/ubuntu/ edgy-backports main restricted universe multiverse

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free non-free
```

and i use the sudo command at the begining

---

### Post by hyper_ch on 2007-06-30
```

sudo apt-get update

```

```

sudo apt-get install XXXX

```

---

### Post by Nolander on 2007-06-30
ive tryd the above post it stillgives methe same result

---

### Post by glimpsed on 2007-06-30
Same problem here:

glimpsed@glimpsed:~$ sudo apt-get -f install liferea
Reading package lists... Error!
E: Problem parsing dependency Conflicts
E: Error occurred while processing libpng12-0 (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

Does anyone know what can be done?

---

### Post by Ayuthia on 2007-06-30
**Edit:  Upon further review, the issue I listed below was a fix where they had problems with /var/lib/apt/lists.  The problem here is with /var/lib/dkpg/status.  Please disregard this suggestion.**

You might try the following:
[http://www.linuxforums.org/forum/debian-linux-help/51937-aptitude-problem-problem-mergelist.html](http://www.linuxforums.org/forum/debian-linux-help/51937-aptitude-problem-problem-mergelist.html)

The fix for them is in the 4th post, but like he says, make sure that you back them up in case it does not work.  So if you have the space, copy those files into another directory before attempting.

---

### Post by alienexplorers on 2007-06-30
Try running:
> dpkg --configure -a

---

### Post by glimpsed on 2007-06-30
After doing what Ayuthia said nothing seemed to have changed because I got the exact same output on the terminal as the one I pasted in my previous post.

On alienexplorers' suggestion this is what I got:

> glimpsed@glimpsed:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 23075 package `libpng12-0':
 `Conflicts' field, reference to `libpng12-dev': version contains ` '


So, I guess I'm stuck with it for now. Thanks for the help anyway  ;)

---

### Post by glimpsed on 2007-06-30
I suppose gdebi also uses /var/lib/dpkg/status to install .deb packages because I've got the same error while trying to install liferea via gdebi:

> 
glimpsed@glimpsed:~$ gdebi /home/glimpsed/Desktop/liferea_1.3.8-debian1_i386.deb
Reading package lists: Done
Error opening the cache:
E:Problem parsing dependency Conflicts, E:Error occurred while processing libpng12-0 (NewVersion1), E:Problem with MergeList //var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.


---

### Post by Ayuthia on 2007-06-30
glimpsed-sorry about that.  I just realized that I pointed you in the wrong direction.

alienexplorers suggestion points out that the issue is on line 23075.  It is saying that it does not like a character in that line.  What you could do is open up the file and go to line 23075 and see what is says.  If it does not make any sense, you can copy the section and paste it here and maybe someone who has that package might be able to help.  If you don't know how to look at the file, open a terminal and type:

gedit /var/lib/dpkg/status

That will allow you to look at the file.  You will not be able to make the modifications to it by using what I typed because you need root access.

---

### Post by Nolander on 2007-07-01
Thanks 4 all yourhelp but the problem still remains, ohh well, looks like a re install.

ta,
Nolander

---

### Post by glimpsed on 2007-07-01
I think Nolander solution is the best for now so a reinstall is what I'll also do next.

@Ayuthia: I can open that file for viewing with root permissions if i use this:
> gksudo gedit /var/lib/dpkg/status

Either way though I couldn't open the file because this is what gedit "told" me:

> 
Could not open the file /var/lib/dpkg/status.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Thanks for your help.

---

