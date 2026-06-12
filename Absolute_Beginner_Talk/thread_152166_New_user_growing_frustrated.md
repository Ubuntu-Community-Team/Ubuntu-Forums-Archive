---
title: "New user growing frustrated"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by doorman_54 on 2006-03-29
Been using couple versions of Linux off and on about a year now and have always had the same problem...........Windows made installing so easy!  tried reading some info on faq for installing programs and keep geting same error


here is example


root@ubuntu:/home/adam # sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
root@ubuntu:/home/adam # sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package realplayer
root@ubuntu:/home/adam #

Any help is welcome

---

### Post by Lord Illidan on 2006-03-29
The problem is that you haven't read the good documentation.


1. Enable extra repos: [https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29)

1. Use Synaptic..

```
sudo synaptic
```

---

### Post by WoodyMahan on 2006-03-29
OK

There is graphical interface in Ubuntu that makes installing programs very easy.  It is called Synaptic manager.

Go to System - Administration - Synaptic Package Manager.  It will ask for a password, this is your user password.  When it opens up use the Search Button at the top to search for a program name or program feature (Example: Project Manager) to get a list of available programs for download.

Select the one you want to try, mark it for download and click Apply.

Quick, Easy, Done.

Synaptic is controlled by a file called sources.list, this file contins a list of web addresses that Synaptic currently has availble to search through (repositories).  You can post here for a particular program or feature you want if you don't find it and someone will most likely provide you with an address to add to your sources.list file to make that program available through Synaptic.

The sudo command you listed above is only part of the equation.  You need to know the name of the package you want to install, then type:

sudo apt-get (package name) 
without the parentheses of course.

---

### Post by rmjokers on 2006-03-29
I suggest you read this page:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

It has lots of useful info about installing software to view media that isnt completely free and therefore cant be part of the main Ubuntu distribution.  What you basically need to do is add additional sources for APT so that it can find this software.  Then, installation will be easier than windows.  The apt-cache search / apt-get install method is much faster than going to a site, manually downloading packages, and answering a bunch of install questions.  You just have to know where to point APT to find the packages in the first place.  Don't get discouraged.  A little bit of pain to learn a new way of doing things (the Ubuntu way) will lead to happiness in the long run!

---

### Post by John.Michael.Kane on 2006-03-29
You need to add the plf repos to your soruce list

```
## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secondary repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secondary are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free


```
sudo gedit /etc/apt/sources.list            add the list above , and you should be fine

---

### Post by doorman_54 on 2006-03-29
Thanks guys!!  Synaptic package manager is hard at work.

---

### Post by doorman_54 on 2006-03-29
[QUOTE=SD-Plissken]You need to add the plf repos to your soruce list

```
## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secondary repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secondary are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free


```
sudo gedit /etc/apt/sources.list            add the list above , and you should be fine[/QUOTE]


I added list above as per your post and then recieved an error when starting Package manager.   Add list or replace list?

---

### Post by John.Michael.Kane on 2006-03-29
[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672) look here since this also has the same repos listed. 


On a side not you can always try this [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) it installs everything too make you read it well though.

---

### Post by doorman_54 on 2006-03-29
[QUOTE=SD-Plissken][http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672) look here since this also has the same repos listed. 


On a side not you can always try this [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) it installs everything too make you read it well though.[/QUOTE]


Thx for extra info.   am running 64 bit version so I will follow those steps.



Keeping fingers crossed:)

---

### Post by doorman_54 on 2006-03-29
Downloading and I presume installing updates in terminal as I type.............

---

