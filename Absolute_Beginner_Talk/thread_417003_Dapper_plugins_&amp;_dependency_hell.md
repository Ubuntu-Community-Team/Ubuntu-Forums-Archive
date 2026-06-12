---
title: "Dapper plugins &amp; dependency hell"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by RH9R on 2007-04-21
'Changed from a microstar motherboard to an Asus, and all that worked well died.
I'm trying to get plugins/packages to play media & keep getting messages about 
 
unresolvable dependency: gstreamer...ugly.. depends on xxx but it is not installable.
 
It appears that repository lists get alot of threads, and this noob is not good at (but unafraid) to manipulate the files. 
 
If a simple upgrade to edgy or feisty would solve it, I'd do it, but I'm guessing I'd still need to be able to troubleshoot those dependencies.
 
Anyone have similar trouble w/ Asus? Is it likely something else?
 
Any/all help is very much appreciated. I had 6 months on Dapper & fell hopelessly in love w/ the interface. 'Haven't seen anything as simple and intuitive since the old 'lunch pail' style Mac & OS 6.7.

---

### Post by SOULRiDER on 2007-04-21
Uhm, what i would do is disable any custom repositories you might have added and run these commands:

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by RH9R on 2007-04-21
I'm not smart about what constitutes 'custom repositories'. Is that merely switching off the non-supported universe/multiverse, or editing a source list. If its editing - pls let me know where that is. 
 
Thank You, Soulrider. 'Wish I weren't such a noob.
 
In case the source list helps

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univer se multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
root@gix1k5:/etc/apt#

---

### Post by RH9R on 2007-04-21
Soulrider. Without knowing what other 'custom repositories needed to be shut off, I just tried the commands you recommended, and at least the first one I've tried (gstreamer0.10-plugins-ugly) loaded just fine. I'll keep trying to load those that would be normally done by easyubuntu (which gave instant joy with my last motherboard). 
Again, SR, Thank You for your kind help.

---

### Post by SOULRiDER on 2007-04-22
Well, you dont have any custom repos. Those two commands will downlaod updates and get rid of stuff with dependency problems, but you might need to remove some packages manually. If you want you can join the Kubuntu -yes, kubuntu, not ubuntu- channel on IRC, im allways there so we can talk and sort this problems out.

---

### Post by RH9R on 2007-04-24
Hi SoulRider,
 
Thx for the invite for IRC. I've not set up Gaim before. Perhaps its time I did the noobie searches and got in the habit. 'Hard to say how much I appreciate the kindness.
 
'Hope all is well with the SoulRider.

---

