---
title: "Trying to add repositories!"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-09-11
When i try to add universe and multiverse repositories from synapic manager, it always goes to the point of "downloading file 5 of 5" and it fails for every 1 thereafter.
Can anyone suggest a reason for this? Ive set up the network proxy right! I know that much cos the internet's working so whats the problem??

Thanks,
Meniscus

---

### Post by monktbd on 2006-09-11
maybe the repositories are down right now.
or do you have that problem already for several hours?

---

### Post by Najand on 2006-09-11
What id you close synaptic and type in the command line:
```
$ sudo apt-get update && sudo apt-get upgrade
```
Does it work? If not can you write down the errors here please?

---

### Post by meniscus on 2006-09-11
Yes thanks, I got these 2

[COLOR="Red"]E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
[/COLOR]

---

### Post by meniscus on 2006-09-11
And to answer your question monktbd. I've always got that response from the system.

---

### Post by monktbd on 2006-09-11
looks like either you have still one program running that uses the apt lists (e.g. apt-get, synaptic, add software wizard) or that one of these programs terminated without removing the lock file.

beacuse i guess you have the problem also after a reboot i think it is possibly the latter.

---

### Post by doghi on 2006-09-11
OK,

```
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
```

that could be caused by the fact, that you still got synaptic running? If not, the apt-resources could be locked by a not completely killed apt process.
To get rid of this, try:

```
sudo rm /var/lib/apt/lists/lock
```

And then try to apt-get update, as supposed before

HTH

---

### Post by meniscus on 2006-09-11
Sorry that took so long. Yes i did that and im getting this error? Is it something not configured right?



[COLOR="Red"][/COLOR]meniscus@meniscot:~$ sudo rm /var/lib/apt/lists/lock
Password:
meniscus@meniscot:~$ sudo apt-get update && sudo apt-get upgrade
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy Release.gpg
  Connection failed [IP: 193.1.193.69 80]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy Release
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Packages
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/main Packages
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/restricted Packages
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/multiverse Packages
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Packages
  Connection failed [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/main Packages
  Connection failed [IP: 193.1.193.69 80]
60% [Waiting for headers][COLOR="Red"][/COLOR]

---

### Post by meniscus on 2006-09-11
Here is the total error


[COLOR="Red"]meniscus@meniscot:~$ sudo rm /var/lib/apt/lists/lock
Password:
meniscus@meniscot:~$ sudo apt-get update && sudo apt-get upgrade
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy Release.gpg
  Connection failed [IP: 193.1.193.69 80]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy Release
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Packages
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/main Packages
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/restricted Packages
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/multiverse Packages
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Packages
  Connection failed [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/main Packages
  Connection failed [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/restricted Packages
  Connection failed [IP: 193.1.193.69 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/multiverse Packages
  Connection failed [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Connection failed [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Connection failed [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Connection failed [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  Connection failed [IP: 193.1.193.69 80]
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 193.1.193.69 80]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
meniscus@meniscot:~$[/COLOR]

---

### Post by richbarna on 2006-09-11
The IP that you are trying to connect to is down.
Go to this page where Ubuntu_Demon has a guide to use a better Breezy sources list:-
[http://ubuntuforums.org/showthread.php?t=92672](http://ubuntuforums.org/showthread.php?t=92672)

---

### Post by Najand on 2006-09-11
Maybe there is a problem with Israel repositories... try to edit /etc/apt/sources.list with gedit or vim:
```
$ sudo gedit /etc/apt/sources.list
```
try to remove all "ie."s in 
```
http://[COLOR="Red"]ie.[/COLOR]archive.ubuntu.com 
```
                
To

```
http://archive.ubuntu.com
```

And try:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by meniscus on 2006-09-11
So i just type the following lines of code into the terminal and im done. Should i add them all to be safe? What does deb stand for?








[COLOR="Red"]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted[/COLOR]

## Major bug fix updates produced after the final release of the
## distribution.
[COLOR="Red"]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted[/COLOR]

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

[COLOR="Red"]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse[/COLOR]

## Security Updates
[COLOR="Red"]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted[/COLOR]

d[COLOR="Red"]eb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse[/COLOR]

## official backports
[COLOR="Red"]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse[/COLOR]

# If you get errors about missing keys follow these command's :
# gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
# gpg --export --armor 33BAC1B3 | sudo apt-key add -
#
# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH [http://ovh.com](http://ovh.com)
[COLOR="Red"]deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
[/COLOR]
## plf mirror. use if primary repo is offline
## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
## [COLOR="Red"]deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free[/COLOR]
## [COLOR="Red"]deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free[/COLOR]

##
## Use the following repos ONLY if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## official wine apt repository
##[COLOR="Red"]deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main[/COLOR]
##[COLOR="Red"]deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main[/COLOR]


## opera web browser
## [COLOR="Red"]deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free[/COLOR]

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## [COLOR="Red"]deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./[/COLOR]

## skype
## [COLOR="Red"]deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free[/COLOR]




followed by



[COLOR="DarkOrange"][COLOR="Red"]$sudo gedit /etc/apt/sources.list[/COLOR]


[COLOR="Red"]$sudo apt-get update ; sudo apt-get upgrade[/COLOR]


 [COLOR="Red"]gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -[/COLOR][/COLOR]

---

### Post by richbarna on 2006-09-11
.deb are the packages that Debian and Debian based distros use. The same as an .exe for windows (similar, before someone gets all pedantic on me). Some other distros use rpm packages.

As Ubuntu is a derivative of Debian, it uses deb packages.

Now instructions. Personally I would advise:-

> gksudo gedit /etc/apt/sources.list 
Type your password and the text editor will open, delete everything, and copy the source list above to it, then save and exit.

Then you do the next commands in the terminal.

> sudo apt-get update && sudo apt-get upgrade 
or you can do the commands seperately, hitting enter after each one.

> sudo apt-get update > sudo apt-get upgrade 
You should now see everything going ok in the terminal.

After everything is updated, reboot, and everything should be cool. ;)

*important* If you get given commands to open a graphical program, remember to use gksudo **not **sudo as this can harm your computer. It is ok to use sudo for terminal commands. Also, if you are installing a program using a guide, use aptitude instead of apt-get, aptitude keeps a record of all the files and will make life easier if you want to remove a program in the future.

---

### Post by missmoondog on 2006-09-11
fwiw,
i've always gotten similar errors from the repositories when checking for updates. no matter what sources.list i've used.

---

### Post by meniscus on 2006-09-11
Yes Najand, Did that,

This is what my new updated sources list looks like!




[COLOR="Red"]deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


[/COLOR]

---

### Post by meniscus on 2006-09-11
Should those lines be without the # at the start??

Sorry for delaying the rest of ye, im just tryin what seems to be the easiest fix 1st!

---

### Post by Najand on 2006-09-11
> **meniscus said:**
> Yes Najand, Did that,

This is what my new updated sources list looks like!


deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe




You don't need "#"s before deb. Remove all of "#" signs before lines starting with "deb"

You can copy and paste this if you need:
This is what my new updated sources list looks like!

Copy and paste it if you need.

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


```

---

### Post by Najand on 2006-09-11
> **richbarna said:**
> .deb are the packages that Debian and Debian based distros use. The same as an .exe for windows (similar, before someone gets all pedantic on me). Some other distros use rpm packages.

As Ubuntu is a derivative of Debian, it uses deb packages.

Now instructions. Personally I would advise:-

 
Type your password and the text editor will open, delete everything, and copy the source list above to it, then save and exit.

Then you do the next commands in the terminal.

 
or you can do the commands seperately, hitting enter after each one.




You should now see everything going ok in the terminal.

After everything is updated, reboot, and everything should be cool. ;)

That is nice instruction, but it would be much nicer if you tell him how import/export gpg keys too.

---

### Post by richbarna on 2006-09-11
> **Najand said:**
> That is nice instruction, but it would be much nicer if you tell him how import/export gpg keys too.

To keep the forums clean and tidy, it would be better if a question about gpg keys was in a seperate thread.

Also, the keys are only needed for extra repositories that aren't standard. I will gladly post a guide on how to add the keys, if and when the OP requests it. Uncommenting non-standard repositories is not good advice for a new user.

---

### Post by Najand on 2006-09-11
Sorry, I didn't want to hurt you... 

Unfortunately people don't look at the documentations and the Official Wiki, (also, other guides like Ubuntu guides) If they do, more than 70 % of the problem can be solved...

---

### Post by richbarna on 2006-09-11
> **Najand said:**
> Sorry, I didn't want to hurt you... 

Unfortunately people don't look at the documentations and the Official Wiki, (also, other guides like Ubuntu guides) If they do, more than 70 % of the problem can be solved...

I agree, the Official Wiki is amazing also doing a forum search will usually get answers quickly.

Some posts will always lead to other questions, and yes I could have written instructions for gpg. But, when another person does a forum search for gpg they may have to dig through many unrelated threads.

It is much simpler to find an answer in a seperate well titled thread.

And no, you didn't hurt me ;)

---

### Post by meniscus on 2006-09-11
This is what ive got so far.... Ive tried it twice and there seems to be errors so im gunna try richbarna's method. Hope you dont take offence Najand.. 


[COLOR="Red"]meniscus@meniscot:~$ sudo rm /var/lib/apt/lists/lock
meniscus@meniscot:~$ sudo gedit /etc/apt/sources.list
meniscus@meniscot:~$ sudo apt-get update && sudo apt-get upgrade
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy Release.gpg
  Connection failed [IP: 193.1.193.69 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Sources
  Connection failed [IP: 193.1.193.69 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
33% [Waiting for headers] [Waiting for headers]

[/COLOR]

---

### Post by Najand on 2006-09-11
Connection failed [IP: 193.1.193.69 80] means you cannot connect your proxy server... How did you configure your proxy server?

---

### Post by meniscus on 2006-09-11
from netscape window

edit > preferences > connection settings >

then typed in the proxy server and the port number..



and in terminal typed 

export http_proxy="http://proxyserver:port

  why?

---

### Post by Najand on 2006-09-11
Oh, OK... Try this and see if it will solve your problem or not...
Click on:
1. System -> Preferences -> Network Proxy
It will not ask you for any passwords...
2. select Manual Proxy Configuration.
3. Write down your proxy address/port
4. Click Close.

And then try apt-get again.... I hope this will solve it.
***Gesundheit***

---

### Post by meniscus on 2006-09-11
Brilliant!!It worked!Thank u so much. Well it unpacked and setup a load of stuff so i assume thats it!  Do I need to restart my computer now? 



Just one more question: Whats this [COLOR="Red"]Official Wiki[/COLOR] ye are talking about?

---

### Post by richbarna on 2006-09-11
Good Guide :-
[https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)

---

### Post by meniscus on 2006-09-11
Thank you all so much! Ye are all gems:D

---

### Post by Najand on 2006-09-11
Thanks Lord it is working fine.
Official WIKI is [https://wiki.ubuntu.com/]("https://wiki.ubuntu.com/")
Offical Help is
[https://help.ubuntu.com/](https://help.ubuntu.com/)
And they are a bunch of unofficial ones.

Hope The Ubuntu Philosophy of "Humanity to Others" comes back to the middle east soon.

---

### Post by richbarna on 2006-09-11
They have mentioned that the wiki is now on the Community Docs section ;)
> **Resources**

  [LIST]
[*] [[IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] Documentation]("http://help.ubuntu.com/") - main website for Ubuntu documentation **Note** - the community wiki is now on the [[IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] Community Docs]("https://help.ubuntu.com/community") section on this website - as before, all contributions are welcome! 
[/LIST]
[https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)

---

