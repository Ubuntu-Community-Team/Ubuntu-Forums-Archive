---
title: "[SOLVED] Problem Installing Wine"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Adronicus on 2008-02-23
Hi, I recently installed Ubuntu 7.10 on my computer, and realized I needed wine in order to run windows based operations/programs.
-I do have an internet connection.

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

That is where I received directions to downloading/installing wine.

I do the first step: "Adding the WineHQ APT Repository:"
> wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
-entered in my password, and got an "OK"

Second step: "For Ubuntu Gutsy (7.10):"
> sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

get this::

> 
gregory@Tha-Rig:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
--22:58:48--  [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184, 88.159.206.7, 2001:4de0:aaac:0:2456::2
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

100%[====================================>] 181           --.--K/s             

22:58:48 (18.97 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [181/181]

gregory@Tha-Rig:~$ 


Then after that I did:

> Then, you can install Wine from WineHQ like it were any other package, such as by using the Synaptic Package Manager under System->Administration. Alternatively, you can install from the terminal by running 'sudo apt-get update' to update APT's package information and then 'sudo apt-get install wine'.

I used the terminal again, and when I entered in:>  sudo apt-get update
I got this: 

> gregory@Tha-Rig:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
gregory@Tha-Rig:~$ 

So I thought up to there it was good.
Final step for this:: > sudo apt-get install wine
got this::

> 
gregory@Tha-Rig:~$ sudo apt-get install wine
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
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages
gregory@Tha-Rig:~$ 


PROBLEM, I NEED HELP!!!!

If I do it the other way "using the Synaptic Package Manager under System->Administration"

I mark for installation get this box::

> 
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences
> wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: libaudio2  but it is not installable

So same thing as with using the terminal, i need help, and any that I am provided will be greatly appreciated.

---

### Post by jcwmoore on 2008-02-23
make sure you have all the repsoitories enabled, i.e. the universe and multiverse.  That package could be in a repository that you do not have enabled.  In gutsy go to System > Admin > Software Sources and make sure everything is checked

wine is avaliable in the ubuntu repositroies, you shouldn't need to go through all that "wget" stuff to get it

---

### Post by gyf on 2008-02-23
I had the same problem and as jcwmoore said it was fixed by enabling the repositories.

System -> Administration -> Software Sources 
then ticking the multiverse and universe check boxes.

---

### Post by Adronicus on 2008-02-23
As I previously stated, I got my instructions from
[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")
As well as having little background information on Ubuntu.

BTW, That worked, thanks a bunch!

---

### Post by Adronicus on 2008-02-23
Nevermind

---

