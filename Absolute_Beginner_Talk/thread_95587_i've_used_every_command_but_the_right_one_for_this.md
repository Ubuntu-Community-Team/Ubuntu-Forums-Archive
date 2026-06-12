---
title: "i've used every command but the right one for this install"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-11-26
hi, i'm trying to install rkhunter, it's on my desktop. i've run commands like:
cd rkhunter
installer.sh

cd Home/Desktop/rkhunter
/installer.sh

and lots of others. can you show me the correct one, please? the folder is called rkhunter and inside there's a script called installer.sh

---

### Post by Xian on 2005-11-26
Try this:

cd Home/Desktop/rkhunter
./installer.sh

By the way, this package is availible in Synaptic.
Just enable the backport repos.

```
$ apt-cache policy rkhunter rkhunter:
  Installed: (none)
  Candidate: 1.2.7-16~breezy1
  Version table:
     1.2.7-16~breezy1 0
        500 http://archive.ubuntu.com breezy-backports/universe Packages
```

---

### Post by ds[de] on 2005-11-26
(in terminal)
cd rkhunter
sudo chmod 755 installer.sh
./installer.sh

I think this should work.

Regards,
ds[de]

//edit: damn, Xian was a tad faster. But nice to see two replies within the first 60 seconds ;-)

---

### Post by Danielle on 2005-11-26
hi, thanks for helping me :)
i have tried everything and nothing works. i have been going round in circles for about 5 hours now trying to install things.

this is the error i get when i run - 
cd Home/Desktop/rkhunter
./installer.sh:

./installer.sh: No such file or directory

i have updated my repository but when i run -
$ apt-cache policy rkhunter rkhunter:
  Installed: (none)
  Candidate: 1.2.7-16~breezy1
  Version table:
     1.2.7-16~breezy1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages

i get:
Danielle@ubuntu:~$ $ apt-cache policy rkhunter rkhunter:
bash: $: command not found
Danielle@ubuntu:~$   Installed: (none)
bash: syntax error near unexpected token `none'
Danielle@ubuntu:~$   Candidate: 1.2.7-16~breezy1
bash: Candidate:: command not found
Danielle@ubuntu:~$   Version table:
bash: Version: command not found
Danielle@ubuntu:~$      1.2.7-16~breezy1 0
bash: 1.2.7-16~breezy1: command not found
Danielle@ubuntu:~$         500 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages

when i run this:
cd rkhunter
sudo chmod 755 installer.sh
./installer.sh

this happens:
bash: cd: rkhunter: No such file or directory
Danielle@ubuntu:~$ sudo chmod 755 installer.sh
chmod: cannot access `installer.sh': No such file or directory
Danielle@ubuntu:~$ ./installer.sh

:( 
i had another look and i have rkhunter on my desktop with installer.sh inside. can you help? thanks

---

### Post by Xian on 2005-11-26
[QUOTE=Danielle]i have updated my repository but when i run -
$ apt-cache policy rkhunter rkhunter:
  Installed: (none)
  Candidate: 1.2.7-16~breezy1
  Version table:
     1.2.7-16~breezy1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages

i get:
Danielle@ubuntu:~$ $ apt-cache policy rkhunter rkhunter:
bash: $: command not found[/QUOTE]

No, that was just to illustrate the existence of the package.
To install it you need to issue this command:

$ sudo apt-get install rkhunter

The output from my system:

```
$ sudo apt-get install rkhunter
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liblockfile1 mailx postfix
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre
Recommended packages:
  resolvconf libmd5-perl
The following NEW packages will be installed:
  liblockfile1 mailx postfix rkhunter
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 111kB/1185kB of archives.
After unpacking 3056kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

If you want to install the recommended packages as well all in one shot, then use aptitude and issue this command:

```
$ sudo aptitude install rkhunter
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be automatically installed:
  liblockfile1 libmd5-perl mailx postfix resolvconf
The following NEW packages will be installed:
  liblockfile1 libmd5-perl mailx postfix resolvconf rkhunter
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 164kB/1238kB of archives. After unpacking 3375kB will be used.
Do you want to continue? [Y/n/?]
```

---

### Post by Xian on 2005-11-26
[QUOTE=Danielle]this is the error i get when i run - 
cd Home/Desktop/rkhunter
./installer.sh:[/QUOTE]
Just FYI, the problem here is that you are in the wrong location.
You need to:

$ cd /home/username/Desktop/rkhunter
./installer.sh

Replace 'username' with your own.

You can always check to see if you are in the right place by asking the terminal to list the file contents of where you are located.

$ cd /home/username/Desktop/rkhunter
$ ls -a

---

### Post by Danielle on 2005-11-26
Wow, thanks i have rkhunter installed now. if i want to put it in System Tools do i use smeg? thanks

BTW i have alot of tutorials to read, i just want to setup some security stuff first. i'm going to install a hosts file and a real-time antivirus scanner to protect my windows partition :)
then at some point i want to use Privoxy which i think everyone should have. thanks for the help, Xian. i shall understand all of this soon, i hope :D

---

### Post by Xian on 2005-11-26
[QUOTE=Danielle]Wow, thanks i have rkhunter installed now. if i want to put it in System Tools do i use smeg? [/QUOTE]
You can access the Gnome menu editor with a right-click on the panel.

---

### Post by Danielle on 2005-11-26
thanks, i've  added rkhunter to System Tools but i can't find the icon to add to the menu. does anyone know where rkhunter's icon is kept? or how to add it to System Tool's menu? thanks :)

---

