---
title: "What does &quot;Package *** has no installation candidate&quot; mean? And how do I fix it?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by CheeseEatingBulldog on 2006-09-22
I am trying to install xgl / compiz and have tried to follow all of the howto's but keep on running into bits I can't get.

I have added god knows how many repos to my sources list but keep on getting

"Package csm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package csm has no installation candidate" 

This goes the same for cgwd and the theme packages to go with it. 

I can see the cgwd theme in my synaptic but it refuses to install it

cgwd-themes:
 Depends: cgwd (>=0.54) but it is not installable

I am completely lost as to where I am supposed to look, can anyone help?

Sources list:
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
# deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
# deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# Penguin Liberation Front (sources)
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# Bleeding edge wine packages (packages)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Bleeding edge wine packages (sources)
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


##############################
### Automatix Repositories ###
##############################

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

## created by automatixrepo2
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## Compiz / Xgl /Aiglx
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main universe restricted multiverse
    
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) dapper main
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main aiglx
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx

deb [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy
deb-src [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy

---

### Post by joshyf on 2006-09-22
I'm having the same problem. This 'csm' is a new package, because a couple of weeks ago, on a previous ubuntu install, i had xgl/compiz/cgwd working perfectly... =/ very frustrating!!

---

### Post by CheeseEatingBulldog on 2006-09-22
So, these packages have just been removed from the repos or something? I have tried to find a download site for a direct download, but it seems like that when I finally want to have a go at eyecandy, it has been deleted from the web :(

I get this when I run compiz btw:

compiz
XGL Present
compiz: No XKB extension
compiz: Couldn't load plugin 'dbus'
compiz: Couldn't load plugin 'csm'

---

### Post by dannyboy79 on 2006-09-22
i would strongly suggest going to straight to the source. [www.compiz.net](www.compiz.net) and you'll get a better answer there. Plus, they have great tutorials. That's the tut I used to get my compiz and xgl running on my dapper box. Good luck. also, you have way to many repositories, you are probably getting conflictions since you have so many, you only need 2 of them. It's all stated at [www.compiz.net](www.compiz.net), in fact i found a great link for ya'll. [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

---

### Post by CheeseEatingBulldog on 2006-09-22
Thanks for that, but I have been to both of those links, and still no joy. I can't get the cgwd or any of themes.

The compiz forums are one big maze of text, will have better look, but am fed up.

---

### Post by sYs^ on 2006-09-22
Same problem, this problem appeared only for 64Bit users(they had to add another line to their sources.list :P), but now ...

Any ideas?

---

### Post by sYs^ on 2006-09-22
I just found this on [http://www.compiz.net/topic-4562-1.html](http://www.compiz.net/topic-4562-1.html)

> 
...
CSM has become Beryl Settings Manager (beryl-settings)
CGWD has become Emerald, with its companion emerald-theme-manager.
...
Perhaps this is the source of our problem :p
But:

```
 dani@paks:~$sudo apt-cache search emerald
xemeraldia - not just another tetris clone
dani@paks:~$
```or

```
dani@paks:~$ sudo apt-cache search beryl
dani@paks:~$

```

What do you think? :p

---

### Post by CheeseEatingBulldog on 2006-09-22
I read that they had changed the names ...so basically they switched to a new name and package....but have failed to put these up for grabs, and they have removed the original packages. Great.

---

### Post by kikos on 2006-09-22
I spent about 3 hrs trying to get csm installed to no avail because of the same problem.    These linux dependency issues are the reason I hate changing/updating the default distro packages.  Is there a ubuntu distro that already has compiz and xgl installed from a livecd by default?

---

### Post by kikos on 2006-09-22
Alternatively, is there another package I can use to get compiz/xgl working on Ubuntu (Dapper Drake) without need of the csm package?

---

### Post by Skardal on 2006-09-22
Yes, this is frustrating...I installed CSM etc yesterday,
but I removed them again today. When I tried to reinstall them I get the same problems that you guys are.

Hopefully this will be solved soon :?

---

### Post by sYs^ on 2006-09-23
Check out this topic:
[http://www.compiz.net/topic-4690-2.html](http://www.compiz.net/topic-4690-2.html)

---

### Post by Skardal on 2006-09-23
Try this!


```
sudo apt-get install compiz-plugins
```

:D \\:D/

This solved my problem!

Edit: 
I was wrong. Sorry guys. It installed csm etc, but it didn't work.

---

### Post by CheeseEatingBulldog on 2006-09-23
I get:

sudo apt-get install compiz-plugins
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-plugins: Depends: csm (>= 0.5) but it is not installable
E: Broken packages

:(

Guess we will have to wait for the new compiz release.

---

