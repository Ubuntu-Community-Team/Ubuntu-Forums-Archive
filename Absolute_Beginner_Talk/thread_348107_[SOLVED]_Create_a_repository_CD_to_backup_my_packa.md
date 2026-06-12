---
title: "[SOLVED] Create a repository CD to backup my packages"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Canis familiaris on 2007-01-28
Hi there
How can I create a repository CD for Ubuntu?
I have a lot of packages installed on my dapper like Kubuntu-desktop, Xubuntu Desktop, etc. which I do not want to download again, since I've a ltd. broadband connection.
I want to create a repository CD such that, i can install all the packages in a fresh Ubuntu installation or in another computer  which was installed in my current installation of Ubuntu.
So that without connecting to internet I can insert te CD and:
```

sudo apt-cdrom add
sudo aptitude install kubuntu-desktop
```
and expect it to be installed covering all dependencies, and not caring for package upgrades. (which i want to do at another time),
I want to repository CD or perhaps many CDs to cover all my downloaded packages.
Personally I've tried APTonCD but to say it is not suitable for my purpose.

Thanks in advance

---

### Post by MkfIbK7a on 2007-01-28
this directory has all the things you installed through apt-get...

/var/cache/apt/archives

---

### Post by Pobega on 2007-01-28
I'm not sure how long it's kept in cache, but you can try using > aptitude download <package> for the packages you want to backup. If you're going to want to backup your packages for future use you might actually want to use download from now on, that creates a .deb file for the package in your current working directory (In the terminal).

**Edit:**Nevermind, Wert's answer was better than mine.

---

### Post by Canis familiaris on 2007-01-28
> **wert613 said:**
> this directory has all the things you installed through apt-get...

/var/cache/apt/archives
OK, If I copy these files, how can I configure the CD such that such that it behaves like a repository CD?

---

### Post by MkfIbK7a on 2007-01-28
i dont know but you really dont need to,
 just burn these onto a cd and when you want to install them insert it into the drive and open it and copy the debs that you want to the hardrive and double click to install them

---

### Post by Canis familiaris on 2007-01-28
> **wert613 said:**
> i dont know but you really dont need to,
 just burn these onto a cd and when you want to install them insert it into the drive and open it and copy the debs that you want to the hardrive and double click to install them
Installing .deb by double clicking? But that is painful!  It pushes on to a dependency hell.  :mad:  I would much prefer to create a repository CD so that I could install the backup packages by apt-get or aptitude.

---

### Post by MkfIbK7a on 2007-01-28
im not sure how to do that but im sure someone wrote instructions on how...

maybe try the code you posted in the first post

```
sudo apt-cdrom add
sudo aptitude install kubuntu-desktop
```

---

### Post by Canis familiaris on 2007-01-29
> **wert613 said:**
> im not sure how to do that but im sure someone wrote instructions on how...

maybe try the code you posted in the first post

```
sudo apt-cdrom add
sudo aptitude install kubuntu-desktop
```

Isn't that the CD requires an index to act as a repository CD?

---

### Post by Canis familiaris on 2007-01-29
Is there a script or method to create a repository CD of my packages?

---

### Post by Canis familiaris on 2007-01-29
And Is there any way that I install kubuntu-desktop package edgy on my dapper installation and my edubuntu-desktop package dapper as well.

---

### Post by CongoJim on 2007-01-29
> **Anurag_panda said:**
> Is there a script or method to create a repository CD of my packages?

There is aptcd but if you copy your archives to whatever then you can use synaptic to install them by using in Synaptic -File- install downloaded packages- chose your copied archives and sit back and  watch all of them install. It's a good idea to be conected when you do this just in case but the last time I did it it was 500mb of old and less than 1 mb new.

---

### Post by Canis familiaris on 2007-01-29
> **CongoJim said:**
> There is aptcd but if you copy your archives to whatever then you can use synaptic to install them by using in Synaptic -File- install downloaded packages- chose your copied archives and sit back and  watch all of them install. It's a good idea to be conected when you do this just in case but the last time I did it it was 500mb of old and less than 1 mb new.
Perhaps it's a good way to backup my packages, but my question was that how could I prepare a repository CD from my apt archives?

---

### Post by CongoJim on 2007-01-29
> **Anurag_panda said:**
> Perhaps it's a good way to backup my packages, but my question was that how could I prepare a repository CD from my apt archives?

Are you wanting to selectively re-install? If not, just do what I suggested.It works across computers transfering one to another. I used it to install identical pkgs on 6 computers and it needn't be a cd, you could network transfer, put in on a flash, it doesn't really matter. just get the archive someplace where you can read it except you probably don't want to overwrite the existing archives. ie put the new on your desktop or leave it on the flash or cd and read it from there.

---

### Post by casaschi on 2007-01-29
This might be what you are looking for:

[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)
"This page will describe how to make a cd which contains packages you have downloaded on one machine using apt or synaptic. The cd will be a repository that you can easily use on another machine using synaptic or apt-cdrom."

---

### Post by MkfIbK7a on 2007-01-29
good resource it is really what i said but it has a program that automates it!

---

### Post by Canis familiaris on 2007-01-30
> **casaschi said:**
> This might be what you are looking for:

[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)
"This page will describe how to make a cd which contains packages you have downloaded on one machine using apt or synaptic. The cd will be a repository that you can easily use on another machine using synaptic or apt-cdrom."
Great Link! Thanks :KS

---

### Post by ultima on 2007-01-30
all I do is copy all the files in /var/cache/apt/archives into a tar.gz archive. 

When you re-install or install on another machine just put them back in /var/cache/apt/archives and run sudo apt-get update. That way you can use apt-get to install your packages.

---

### Post by klein de usa on 2007-02-19
Hi
i found this the other day but haven't tried it yet :
[http://www.ubuntugeek.com/?PHPSESSID=271596d7944be10a54345b300b696d71&s=aptoncd]("http://www.ubuntugeek.com/?PHPSESSID=271596d7944be10a54345b300b696d71&s=aptoncd")

---

### Post by dvarsam on 2007-02-19
[QUOTE=Anurag_panda]Perhaps it's a good way to backup my packages, but my question was that how could I prepare a repository CD from my apt archives?[/QUOTE]

You could also do a **workaround** on this...

I remember back in [color=red]Ubuntu v6.06[/color] **or** [color=red]v5.10[/color], that Synaptic used _also_ the Ubuntu CD as an Update Repository...

_Steps Required_:

1. You must add the Ubuntu CD into Synaptic's available Repos...
HowTo: From inside the Synaptic window, from the Menu you select "[color=blue]Settings\Repositories[/color]".
I am NOT sure where you have to go next to do the rest, but hopefully someone could guide your through...

_Note_:
Searching back, I found this line in my [color=red]Ubuntu v5.10[/color] "[color=blue]/etc/apt/sources.list[/color]" file:
```
deb [color=blue]cdrom:[/color][Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```
With some little editing you could make this like work with your Ubuntu v6.10 CD Repos.



2. Burn a New Ubuntu v6.10 CD/DVD, after you have copied/added your downloaded Updates into the original Ubuntu v6.1O CD repositories...
(as someone said before, all downloaded Update packages are available in the folder "[color=blue]/var/cache/apt/archives[/color]" - so all these downloaded packages must be added in some way to your Ubuntu v6.10 CD's Repos...)

Hope this helps...
Good luck!

P.S.> You could also wait for an Ubuntu v6.10 Service Pack to be made available.
This happened in the past with Ubuntu v6.06 (when 130-40 updates were created... :))

---

