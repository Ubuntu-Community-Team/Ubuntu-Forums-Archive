---
title: "OpenOffice 2.1 on Dapper?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by keithpeter on 2007-02-08
Hello All

I have Dapper with xubuntu running on a reasonably fast computer (P4, 2Ghz, enough ram). I would like to install openoffice as I do worksheets with diagrams and formulas a lot. The repros version of OpenOffice is old and has interface issues (possibly just cosmetic, but then I have to look at this screen most days :0 )

Is there a way of installing OpenOffice 2,1 in such a way that I don't have problems with aptitude afterwards? The recipe at [http://ubuntuforums.org/showthread.php?t=318865](http://ubuntuforums.org/showthread.php?t=318865) results in aptitude trying to uninstall 'unused' libraries each time I install any new software.

One suggestion is that I compile OpenOffice from source. How would I go about this and put the package in my home directory so aptitude does not complain?

Thanks

---

### Post by emarkay on 2007-02-08
Interested, too...

---

### Post by shareMenaPeace on 2007-02-08
I installed openoffice under xubuntu with synaptic, well i didnt used it much but it looked exactly lke the ubuntu release to me. 

I think what you can do is
```

sudo aptitude install openoffice 
```(maybe case sensitive? OpenOffice or openOffice) 

or use System -> Administration -> Synaptic Package Manager

Or use 

[http://getautomatix.com](http://getautomatix.com)

---

### Post by keithpeter on 2007-02-08
Hello shareMenaPeace

Yup, thanks, and I know how to get OpenOffice version 2.02 on my computer with the security updates distributed as part of the Dapper release.

It's just that I would like the current 2.1 version. Looks more finnished, has a view menu that displays properly and so on. When I follwed the instructions I linked to in my original post, I got the software installed ok, but installing anything else or doing an update/upgrade lead to a huge rigmarole!

I'd settle for telling aptitude to leave OpenOffice alone.

Cheers

---

### Post by shareMenaPeace on 2007-02-08
Oh ok nvm than :)  gl

---

### Post by Daveth on 2007-02-08
have a look at

[http://bodmas.org/blog/?p=523](http://bodmas.org/blog/?p=523)

installed it myself a few days ago from this and it is sweet.

---

### Post by keithpeter on 2007-02-08
> **Daveth said:**
> have a look at

[http://bodmas.org/blog/?p=523](http://bodmas.org/blog/?p=523)

installed it myself a few days ago from this and it is sweet.

Er - that is my blog :)  

OpenOffice runs fine. The problem is that when I try to upgrade or update or install any new software, aptitude insists on uninstalling half of openoffice! I then had to re-run the dpkg command to re-install OpenOffice. I have ammended the blog post to warn people of this.

Now, are you running Xubuntu or Ubuntu? If Xubuntu, did you install and uninstall OpenOffice 2.02 from the repos first?

---

### Post by Daveth on 2007-02-08
oops, sorry, had not made the connection. I'm on ubuntu and uninstalled the standard version of oo that came out of the box (2.0.4??). Then straight  to 2.1. Excellent instructions by the way. Only using Synaptic not apt-get.

---

### Post by keithpeter on 2007-02-08
> **Daveth said:**
> oops, sorry, had not made the connection. I'm on ubuntu and uninstalled the standard version of oo that came out of the box (2.0.4??). Then straight  to 2.1. Excellent instructions by the way. Only using Synaptic not apt-get.

Good for you. What happens when you install new software :-) 

My particular hassle might be specific to Xubuntu; the original blog post related to a 'bog standard' Dapper Ubuntu install but I actually prefer the lighter system.

---

### Post by keithpeter on 2007-02-21
Replying to my own posts again - bad news.

I did a clean install of Xubuntu on the Dell laptop. I was then able to

[LIST]
[*]install alien using sudo aptitude install alien
[*]convert the OpenOffice 2.1 RPMs to debs
[*]install the debs using dpkg -i * .deb
[/LIST]

Just like the tutorial posted originally.

I have had no more wierd dependency problems. I have also managed to get OpenOffice 2.1 installed on a P4 desktop that already had inkscape, dia, kile, and a number of other programs installed - again no problems. 

My earlier issues must have been due to doing something stupid like trying to use the debs from the Dell P3 on the IBM P4.

---

