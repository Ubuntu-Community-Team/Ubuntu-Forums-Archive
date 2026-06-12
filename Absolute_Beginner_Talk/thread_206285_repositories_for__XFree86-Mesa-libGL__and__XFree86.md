---
title: "repositories for  XFree86-Mesa-libGL  and  XFree86-libs ???"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-06-29
Hi,

I need to get 2 packages before I can install the ATI proprietary drivers:

> XFree86-Mesa-libGL

XFree86-libs

Can anyone provide full repositories entries to be put in ***soureces.list*** for these packages?

Thanks

---

### Post by ovimunt on 2006-06-30
*bump*

---

### Post by ovimunt on 2006-06-30
little bump :-D

---

### Post by richbarna on 2006-06-30
Ubuntu ati driver install guide :-
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

If you are looking to install an ATI driver, have a look here :-
[http://www2.ati.com/drivers/linux/linux_8.16.20.html]("http://www2.ati.com/drivers/linux/linux_8.16.20.html")

Or if not, what you are looking for is here:-

[http://distro.ibiblio.org/pub/linux/distributions/startcom/ML-3.0.3/updates/repodata/repoview/XFree86-Mesa-libGL-0-4.3.0-78.SEL.html]("http://distro.ibiblio.org/pub/linux/distributions/startcom/ML-3.0.3/updates/repodata/repoview/XFree86-Mesa-libGL-0-4.3.0-78.SEL.html")

---

### Post by ovimunt on 2006-06-30
Hi,

Thanks for the two links but I've been there already. What happens is that I get some errors of missing commands/files during the installation. Then, on ATI's website they say that you ***must*** have those packages otherwise the install will not run properly. So I've checked Synaptics and couldn't find them either as installed or at least as available to install. I also did an ***apt-get*** and ***aptitude*** to try and install them from the command line but they're not available from my current list of repositories.

I then did a Google and managed to find the two libraries on their home website. However if you want to install them manualy you need to run some script which is supposed to tell you which distribution you need to install for your particular system. Problem is that none of the distributions available seem to be apropriate for my system. 

Now, the fact that I'm running the AMD64 distribution of Ubuntu may be the reason for not finding a suitable distribution of the two libraries that I need. With this in mind I thought that if I manage to find a repository I might be able to use Synaptics to find the right distribution of the libraries.

I then did a Google on this and did actually managed to find some repositories  containing those libraries. This is where I got stuck - I don't know how to add that URL to my list of repositories... :-| I do know how to edit the ***sources.list*** and all that but I don't know which is the exact URL that I need to enter i.e. main folder, etc, nor do I know what are the arguments that I need.

Any other suggestions? 

Thanks anyway

---

### Post by ovimunt on 2006-06-30
*bump*

---

### Post by richbarna on 2006-06-30
[QUOTE=ovimunt]*bump*[/QUOTE]

Okay, Open your terminal and type :-

> gksudo gedit /etc/apt/sources.list

It'll ask for your password and then show you the list. You may have to comment out some other repos as well (remove the #'s)

Just scroll to the bottom and copy and paste your repo url, save and exit.

Then terminal again :-

> sudo aptitude update && sudo upgrade

That should get you sorted :)

PS: If you paste the url's here I can prepare you a complete sources.list and you can copy and paste the whole thing.

---

### Post by ovimunt on 2006-06-30
Hi,

These are the full URLs as found by Google. Both repositories contain the two libraries. Looking at the first URL it does seem to be a 32bit version but maybe there is a 64bit one somewhere on the server or maybe the 32bit one will work.


[http://linuxsoft.cern.ch/cern/slc30X/i386/yum/os/repodata/repoview/XFree86-Mesa-libGL-0-4.3.0-97.EL.html](http://linuxsoft.cern.ch/cern/slc30X/i386/yum/os/repodata/repoview/XFree86-Mesa-libGL-0-4.3.0-97.EL.html)

[http://dries.ulyssis.org/rpm/packages/pointless/pointless-spec.html](http://dries.ulyssis.org/rpm/packages/pointless/pointless-spec.html)


Thanks

---

### Post by joshrobinson on 2006-06-30
thats weird that you need those packages. im running the 64bit dapper with an ati card, and i dont recall having to install those packages, i looked on the ubuntu packages website and didnt see it.. i also checked a few of the other repo's i have enabled and didnt see it either

---

### Post by ovimunt on 2006-06-30
These packages are needed for the ATI proprietary drivers. I am running Ubuntu fine as it is, with its own ATI drivers, but I'm trying to install those ones to run a game.

---

### Post by joshrobinson on 2006-06-30
[QUOTE=ovimunt]These packages are needed for the ATI proprietary drivers. I am running Ubuntu fine as it is, with its own ATI drivers, but I'm trying to install those ones to run a game.[/QUOTE]

yeah i use the proprietary drives also. i did ```
sudo apt-get install xorg-driver-fglrx
```
i needed the proprietary drivers for xgl.

so you cant install from either the .run file from the ati website or through apt without these files? i dont understand how it makes you have them and i didnt need them

---

