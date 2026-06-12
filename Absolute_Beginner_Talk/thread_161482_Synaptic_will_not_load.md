---
title: "Synaptic will not load"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-17
I get this error message (after a failed program install)

[COLOR="Blue"]E: Internal error opening cache (1). Please report.
E: Unable to lock the list directory[/COLOR]

I hope there is something I can do to fix this?

---

### Post by ubernoob on 2006-04-17
E: Unable to lock the list directory

you usually get this if you don't run it as root, or if you are already running synaptic or update manager

---

### Post by cliff0108 on 2006-04-17
I also get this :
[COLOR="Blue"]E: Internal error opening cache (1). Please report.[/COLOR]

I went to the help page in Synatic and it stated :

 [COLOR="Blue"]Synaptic Package Manager requires a clear environment with no half installed packages to perform additional changes. But at the moment there is no way to continue canceled installations within Synaptic Package Manager.

To fix this situation type the following command in a terminal, then press Return:
apt-get install -f [/COLOR]

I just attempted run Synaptic the way I usually do System/Administration/Synaptic Package Manager

I gather the system can stall sometimes with a partially loaded program install.

Not sure what I should try next
Cliff

---

### Post by Titus A Duxass on 2006-04-17
Try running apt-get install -f in a terminal as it suggests.

---

### Post by cliff0108 on 2006-04-17
When I run what is suggested I get this :

c[COLOR="Blue"]liff@ubuntu:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package avidemux needs to be reinstalled, but I can't find an archive for it.
[/COLOR]

I deleted the only instance of the program in the usr/local/automatix/conf directory 
(the binary - which works - by the way- remained where I installed from - my downloads directory. Should I delete every instance of avidemux and I wonder will this get my Synaptic to reload?

---

### Post by Titus A Duxass on 2006-04-17
Try apt-get remove avidemux to get rid of the package.

---

### Post by cliff0108 on 2006-04-17
No - I get this :

c[COLOR="Blue"]liff@ubuntu:~$ sudo apt-get remove avidemux
Reading package lists... Done
Building dependency tree... Done
E: The package avidemux needs to be reinstalled, but I can't find an archive for it.
[/COLOR]

---

### Post by Titus A Duxass on 2006-04-17
Do:
apt-cache search avidemux

That will show you the available packages, then you can apt-get install the packages.

If it returns no packages then you need to modify your sources.list so that the repositories are available.

---

### Post by cliff0108 on 2006-04-17
Thanks for your continuing help - this is what I got  - so do I try to modify my sources .list and if so - how would I doo that - AND should I try amnually uninstalling ? Very new at all this :o(

[COLOR="Blue"]cliff@ubuntu:~$ sudo apt-cache search avidemux
Password:
avidemux-2.1.0 - Avidemux 2.1 Final build. x86 package.
avidemux -
cliff@ubuntu:~$ sudo apt-get install Avidemux 2.1.0
Reading package lists... Done
Building dependency tree... Done
E: The package avidemux needs to be reinstalled, but I can't find an archive for it.
[/COLOR]

---

### Post by Titus A Duxass on 2006-04-17
You have the packages available.

Try:
apt-get install -f avidemux-2.1.0

This should force the install if I remember correctly.

---

### Post by Titus A Duxass on 2006-04-17
I have just checked, you can install avidemux using the Automatix package that is available in this forum.

No problem giving help, it's Easter Monday and I am not at work.

---

### Post by cliff0108 on 2006-04-17
Rats! 
Still did't work :

[COLOR="Blue"]Cliff@ubuntu:~$ sudo apt-get install -f avidemux-2.1.0
Reading package lists... Done
Building dependency tree... Done
E: The package avidemux needs to be reinstalled, but I can't find an archive for it.
cliff@ubuntu:~$[/COLOR]

---

### Post by Titus A Duxass on 2006-04-17
Give the Automatix thing a twirl, this usually does everything without a hitch.

---

### Post by cliff0108 on 2006-04-17
It didn't work eitther - gives the same response the get-apt thing did. I had tried earlier.
I think if I'd installed from Automatix to begin with rather than a rmp to deb convert all would have been well.

---

### Post by cliff0108 on 2006-04-17
If I search for and manually delete every avidemux file I wonder if that would help. I know with Windows there is a registry to worry about - but I don't think Linux has that?

My concern is not so much getting this program to wotk as it is getting Synaptic to.

I do appreciate the time you are taking with this  ! :o)

---

### Post by Titus A Duxass on 2006-04-17
There is an apt command for purging the system but I can't remember it.

This commands are available:

   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

I would try:

check followed by clean or autoclean.

I think you are correct about the converting thing.  But the apt system is pretty smart and we should be able to fix this.  I can't help you with Synaptic, I do everything through apt at the CLI.

Have you done:
apt-get update - this gets your sources.list upto date,
apt-get upgrade - installs the latest versions that are available,
apt-get dist-upgrade - upgrades the distribution.

Usually doing the three steps above sorts out most problems.

---

