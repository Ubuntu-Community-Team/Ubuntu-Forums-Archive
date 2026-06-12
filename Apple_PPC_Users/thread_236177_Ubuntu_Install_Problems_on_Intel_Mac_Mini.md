---
title: "Ubuntu Install Problems on Intel Mac Mini"
date: 2006-08-14
forum: Apple PPC Users
---

### Post by msabers on 2006-08-14
I tried to install Ubuntu on my Intel Mac Mini, but it fails to install GRUB. I found instructions at false-bin.org that give Terminal commands to install Lilo, but it says only an administrator can do that. Trying to boot into Ubuntu fails every time. 

Is there a guide for installing Ubuntu on an Intel Mac Mini, or can somebody tell me how to get it to boot?

---

### Post by tactus on 2006-08-14
You probably need to type "sudo su" or something before the given commando fails. I used the instructions from false-bin.org to install Dapper on my Mac Mini Intel in the weekend and it worked for me. At least everything worked until today, but that's for another topic..

---

### Post by msabers on 2006-08-14
I followed the instructions from this thread:
[http://www.ubuntuforums.org/showthread.php?t=196912&highlight=intel+mac](http://www.ubuntuforums.org/showthread.php?t=196912&highlight=intel+mac)
but got this error:

[I]root@ubuntu:/# apt-get install lilo lilo doc
Reading package lists... Done
Building dependency tree... Done
Package lilo is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lilo has no installation candidate
[/I]

How do I circumvent this?

---

### Post by pdub on 2006-08-14
it should read:

apt-get install lilo lilo-doc

There is a typo in the instructions you are following

---

### Post by msabers on 2006-08-14
Same result:

root@ubuntu:/# apt-get install lilo lilo-doc
Reading package lists... Done
Building dependency tree... Done
Package lilo is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lilo has no installation candidate
root@ubuntu:/#

---

### Post by pdub on 2006-08-14
Can you access the internet from this computer so that apt can get to the repositories?

If you type **aptitude search lilo** what do you get?

Can you post your sources file?

gedit /etc/apt/sources.list

---

### Post by msabers on 2006-08-14
"aptitude search lilo" does nothing, it just moves to the next line. I cannot open the sources file, this is what happens:

[I]root@ubuntu:/# gedit /etc/apt/sources.list
cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.
root@ubuntu:/#[/I]

This is running under a chrooted terminal window, I don't know if I should be using a normal terminal.

EDIT: Running under a non-chrooted terminal window gives this:
[I]ubuntu@ubuntu:~$ aptitude search lilo
p   elilo                           - Bootloader for systems using EFI-based firp   lilo                            - LInux LOader - The Classic OS loader can lp   lilo-doc                        - Documentation for LILO (LInux LOader)
ubuntu@ubuntu:~$
[/I]

Should I be entering your commands in a chrooted or non-chrooted window?

---

### Post by pdub on 2006-08-14
Sorry about that, forgot you were in a shell only.

You can just type **cat /etc/apt/sources.list**

Did you follow the instructions to the letter? I have not installed Ubuntu on my Mac-Mini yet so I am not familiar with the process.

It appears as though you should have a full GUI running during the install so gedit should have worked for you. 

Do you have access to the Internet from the mini?

Can you ping something like [www.ubuntu.org?](www.ubuntu.org?)

ping [www.ubuntu.org](www.ubuntu.org)

---

### Post by msabers on 2006-08-14
Here is my sources file:

[I]root@ubuntu:/# cat /etc/apt/sources.list

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ erse multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
[/I]

And to answer your question, I do have internet access on the mini (via ethernet). 

I think the next thing I have to do is uncomment the Universal lines, which should allow me to install Lilo, correct? However, I don't know how to do that from the command line (or without using gedit).

---

### Post by pdub on 2006-08-14
When I do an **aptitude search lilo** I get 

[I]p   elilo        - Bootloader for systems using EFI-based firmware
p   lilo         - LInux LOader - The Classic OS loader can load Lin
p   lilo-config  - KDE frontend for lilo configuration
p   lilo-doc     - Documentation for LILO (LInux LOader)[/I]

Here is my sources.list

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free 

## Repository for wine
deb http://wine.sourceforge.net/apt binary/
deb-src http://wine.sourceforge.net/apt source/

deb http://kubuntu.org/packages/amarok-141 dapper main

# The Opera web browser repopsitory
deb http://deb.opera.com/opera etch non-free

```

---

### Post by msabers on 2006-08-14
How can I change my sources list to yours, using a chroot terminal?

---

### Post by hajk on 2006-08-15
> **msabers said:**
> Same result:

root@ubuntu:/# apt-get install lilo lilo-doc
Reading package lists... Done
Building dependency tree... Done
Package lilo is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lilo has no installation candidate
root@ubuntu:/#

Did you change your /etc/apt/sources.list? Then you must first do 
# apt-get update
before installing lilo etc...

---

### Post by pdub on 2006-08-15
You can use **vi**
[B]
vi /etc/apt/sources.list[/B]

OR

**sudo vi /etc/apt/sources.list** if you are not root already

The commands are **"i"** to insert text
**esc** to leave insert mode

When you are done type **:wq** which will write then quit

Then the following command:

**apt-get update**

Then continue your setup

---

### Post by msabers on 2006-08-15
Ok, got universal repos uncommented in the sources file. I tried to run **apt-get update**, but now it appears as if it does not have an active internet connection.

The Live CD has an active internet connection, but the chrooted terminal does not. How do I install Lilo now?

Would Lilo be on the Ubuntu DVD (I have one)?

---

### Post by pdub on 2006-08-15
You can add the DVD or CD as a repository. 

Insert the CD or DVD

sudo apt-cdrom add
And give a name like 'ubuntu-dvd' or anything you want.

---

### Post by keirnna on 2006-09-14
I am having the same issue. I followed these directions to a T from [http://bin-false.org/?p=17](http://bin-false.org/?p=17). I recieved this error from my chroot'ed terminal:

root@ubuntu:/# apt-get install lilo
Reading package lists... Done
Building dependency tree... Done
Package lilo is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lilo has no installation candidate
root@ubuntu:/#

Now I can apt-get no problem from the non-chroot'ed terminal or the live cd; however, I seem to have no internet access from my chroot'ed shell. How can I get around this without downloading the packages and installing that way? TIA.

---

### Post by keirnna on 2006-09-14
Turns out this is the solution to this problem: (Remark :Some users report problem to find lilo because no network is not
available in the chroot terminal. It is strange it works for most for us.

If you have that problem, the solution is to reactivate the network in the chroot terminal.
Either manually (ifup eth0), with dhclient
or using the graphical config (gksu network-admin).)

---

