---
title: "Repositorys"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2006-09-10
[FONT="Arial"][SIZE="2"][COLOR="Black"]Is there anything wrong with the repositories , I cant acees anything ??

tried to remove and re install synaptic , but I cant access that even with the comand line 

Stephen[/COLOR][/SIZE][/FONT]

---

### Post by davmac on 2006-09-10
Repositories working fine for me.

Is your connection working OK? Open up a terminal window and type "ping www.google.com". If that looks ok, what do you get if you type "sudo apt-get update"?

If that works OK, what output do you get if you type "sudo apt-get check" or "sudo apt-get update"?

If none of these are working could you type "cat /etc/apt/sources.list" and post the result back here?

Dave Mac

---

### Post by basilwatson on 2006-09-10
s@stephen-laptop:~$ sudo apt-get check
Password:
Reading package lists... Done
Building dependency tree... Done
s@stephen-laptop:~$

cat /etc/apt/sources.list
s@stephen-laptop:~$ sudo su
root@stephen-laptop:/home/s# cat /etc/apt/sources.list
cat: /etc/apt/sources.list: No such file or directory
root@stephen-laptop:/home/s# cat /etc/apt/sources.list
cat: /etc/apt/sources.list: No such file or directory
root@stephen-laptop:/home/s# cat home/s/etc/apt/sources.list
cat: home/s/etc/apt/sources.list: No such file or directory
root@stephen-laptop:/home/s#

Stephen

---

### Post by Anonii on 2006-09-10
> **basilwatson said:**
> s@stephen-laptop:~$ sudo apt-get check
Password:
Reading package lists... Done
Building dependency tree... Done
s@stephen-laptop:~$

cat /etc/apt/sources.list
s@stephen-laptop:~$ sudo su
root@stephen-laptop:/home/s# cat /etc/apt/sources.list
cat: /etc/apt/sources.list: No such file or directory
root@stephen-laptop:/home/s# cat /etc/apt/sources.list
cat: /etc/apt/sources.list: No such file or directory
root@stephen-laptop:/home/s# cat home/s/etc/apt/sources.list
cat: home/s/etc/apt/sources.list: No such file or directory
root@stephen-laptop:/home/s#

Stephen

Interesting, you dont have a sources.list file :P

Now, go to the terminal and do:
_sudo gedit /etc/apt/sources.list _

and paste these lines inside:

```
# Specialized Basic Ubuntu Multimedia Preparation Script sources.
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Major Bugfixes
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Universe
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

## Security Updates
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

## Multiverse
deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

## Debian Multimedia Repository
deb http://www.debian-multimedia.org sarge main

## Original BUMPS repository.
## deb http://www.politicalcrossfire.com/ubuntu/dapper dapper main non-free

```

then save the file, and run the:
_sudo apt-get update_
again.

Finally, you must have somehow ****** up your whole /etc/apt/sources.list file, the file which holds the repositories. Careful not to do the same again <:

---

### Post by basilwatson on 2006-09-10
sorry tried that * cant cut and paste as it wasnt connecting to this site so have gone to office ! on another computer .. 

it said command not found, i tried in rood and sudo and etc ..I  am not skilled enough to figure that one out Sooooooo..... 

I am going to reburn a new cd , install afresh , and if that dont work 

who knows 

* the good thing about xubuntu it takes a few min to load ..everythings backed up ..so its actually quicker in the end !! 

:p 
try that with windows!!! 

Stephen

---

