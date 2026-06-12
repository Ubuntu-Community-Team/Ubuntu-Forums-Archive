---
title: "Problem with screenlets"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by ndogg1982 on 2007-07-10
Hi, this is my first post here. After about 3 days of Ubuntu on my pc (I somehow corrupted the windows bootloader when installing a second hard drive??) I'm absolutely loving it. I've already installed kubuntu desktop and worked out a bug or two, installed a bunch of games and apps, and even got Beryl working beautifully with an integrated ATI card. My only problem now is, I'm trying to install those cool screenlets everyone talks about, specifically for Cairo clock. Here is what I've done so far:

I've gedited the sources.list file to include that repository, did some kind of apt-get key add thing that a tutorial advised, and then the sudo apt-get install screenlets. 

Now, this is what I get when I do that final step. 

[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  screenlets: Depends: screenlets-core but it is not going to be installed
              Depends: screenlets-extra but it is not going to be installed
              Depends: screenlets-utils but it is not going to be installed
E: Broken packages
[/HTML]

Anyone have any ideas or came across this problem? Thanks for the help in advance.

---

### Post by k33bz on 2007-07-10
> **ndogg1982 said:**
> Hi, this is my first post here. After about 3 days of Ubuntu on my pc (I somehow corrupted the windows bootloader when installing a second hard drive??) I'm absolutely loving it. I've already installed kubuntu desktop and worked out a bug or two, installed a bunch of games and apps, and even got Beryl working beautifully with an integrated ATI card. My only problem now is, I'm trying to install those cool screenlets everyone talks about, specifically for Cairo clock. Here is what I've done so far:

I've gedited the sources.list file to include that repository, did some kind of apt-get key add thing that a tutorial advised, and then the sudo apt-get install screenlets. 

Now, this is what I get when I do that final step. 

[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  screenlets: Depends: screenlets-core but it is not going to be installed
              Depends: screenlets-extra but it is not going to be installed
              Depends: screenlets-utils but it is not going to be installed
E: Broken packages
[/HTML]

Anyone have any ideas or came across this problem? Thanks for the help in advance.

have you installed its dependicies?

---

### Post by ndogg1982 on 2007-07-10
Nope, don't think so. I would love to know how to do that though. Now that you mention it, do I just apt-get screenlets-core, screenlets-extra,and screenlets-utils one at a time in terminal? I'll try that now, if that's not it please explain. And thanks for the lightning quick reply btw!

---

### Post by k33bz on 2007-07-10
NP. but ya do apt-install on each one,

---

### Post by ndogg1982 on 2007-07-10
> **k33bz said:**
> NP. but ya do apt-install on each one,

Thanks for the advice, but that's still not working. I'm getting this now when I do that:

[HTML]:~$ sudo apt-get install screenlets-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  screenlets-core: Depends: python-feedparser but it is not installable
E: Broken packages

[/HTML]

Is this a problem with the repository, or am I doing something wrong? I've also tried installing the python-feedparser but it's saying it's not available. I also just tried downloading the package from the website [http://hendrik.kaju.pri.ee/screenlets/?q=node/5](http://hendrik.kaju.pri.ee/screenlets/?q=node/5)
but I can't figure out how to install from that package.

---

### Post by k33bz on 2007-07-10
have you done this part?


wget [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg) -O- | sudo apt-key add - && sudo apt-get update

Then you can install screenlets with 'sudo apt-get install screenlets'. The package also includes updated third-party screenlets and utilities (Control panel, tray-icon)

---

### Post by ndogg1982 on 2007-07-10
Yeah, I've done that, just did it again and I still get the same thing. And on that apt-key add command it says Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Packages. I've done everything on that tutorial, my guess is that there is a problem with that repo. I'm gonna keep digging around for the answer, but if anyone else could try that tutorial and see if the same thing happens maybe that would help.

---

### Post by k33bz on 2007-07-10
please post results

```
sudo gedit /etc/apt/sources.list
```

---

### Post by ndogg1982 on 2007-07-10
> **k33bz said:**
> please post results

```
sudo gedit /etc/apt/sources.list
```

Here ya go:
[HTML]# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://ubuntu.beryl-project.org/ feisty main
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets[/HTML]

---

### Post by k33bz on 2007-07-10
ummmm,
then idk, kuz i just installed it just fine using those instuctions. are you using fiesty?

---

### Post by ndogg1982 on 2007-07-10
Definitely using feisty, 7.04. Now that I know it's something on my end, I'm sure I can dig around and fix it tomorrow. Little bugs like this are kind of annoying, but I get to learn alot about the os when trying to fix them. Thanks again for your help.

---

### Post by k33bz on 2007-07-10
NP, wish i could of gotten it to work for ya

---

### Post by amphoterous on 2007-07-25
I have the same problem and I am interested to see if you have found a solution.

---

### Post by twizler on 2008-04-09
Go to the screenlets deb download site and install the new one -- open up in package manager -- its all gui -- and easy 

[http://www.getdeb.net/release.php?id=2394](http://www.getdeb.net/release.php?id=2394)

---

