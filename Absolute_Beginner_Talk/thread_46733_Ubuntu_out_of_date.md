---
title: "Ubuntu out of date?"
date: 2005-07-05
forum: Absolute Beginner Talk
---

### Post by fannymites on 2005-07-05
I've been a Debian SID user for the past few months and after having 2 hard drives die in the space of 3 days I managed to lose all trace of my installation, including backups.
So since I have to start from scratch, I decided to try out an Ubuntu 5.04 cd that I ordered a while ago but never got round to installing.

So, to get to the point, I have a problem and a query - 

Firstly, the problem - I've only ever used LILO as a boot loader.  I chose the default install so this installed grub but for some reason it hasn't detected my Windows partition.
The windows partition is accessable from within Ubuntu but it just isn't listed in the grub menu.
The partition in question is hda1 and I've tried adding it to menu.lst as (hd0.0) and (hd0,1) but when I try to select them from the grub menu I get an invalid system disk error.

Secondly, the query - I was under the impression that Ubuntu was really up to date since it came with x.org and Gnome 2.10 and KDE 3.4 which weren't available in Debian SID but I've noticed quite a lot of packages seem old, in particular my fave app of all - Firefox.
Firefox is at version 1.02 in Ubuntu but version 1.04 has been available for some time now.
Is Ubuntu behind the times or can anyone list which repostitories I should be using for more up to date packages?

---

### Post by Sye d'Burns on 2005-07-05
Does your /boot/grub/menu.lst should have a section that looks a bit like this?

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by ltmon on 2005-07-05
Ubuntu should be no more than 6 months old at any time, given each version is released every 6 months.  Of course, you can't just grab the most bleeding edge packages every 6 months so not everything will be up to date.

To get newer packages (i.e. those that are being prepared for the next release) go to the backports forum, which has guides on how to add these repositories.  I think firefox 1.04 is amongst them.

L.

---

### Post by fannymites on 2005-07-05
I don't have an entry like that but I did try the (hd0,0) again and it worked this time, I must have done something wrong before.
One problem solved.

I still can't seem to find any sources.list examples for Ubuntu though.

[EDIT] @ ltmon, you must have been replying at the same time as me.  I'll try the backports forum, thanks.

---

### Post by Sye d'Burns on 2005-07-05
[UbuntuGuide](http://ubuntuguide.org/#extrarepositories) gives you a good list of sources. It's an excellent source of tweaking info as well.

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=Sye d'Burns][UbuntuGuide](http://ubuntuguide.org/#extrarepositories) gives you a good list of sources. It's an excellent source of tweaking info as well.[/QUOTE]


Use those sources for the least amount of trouble.

---

### Post by fannymites on 2005-07-06
Well I've added the sources suggested in the UbuntuGuide, including the backports and I now have Firefox 1.04 amongst other more up to date packages and so far no problems.  Thanks for all the help.

One last thing, are those backport sources safe, since they are unverified? In particular, is there some control over who adds software to the repositories?

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=fannymites]
One last thing, are those backport sources safe, since they are unverified? In particular, is there some control over who adds software to the repositories?[/QUOTE]

They are very safe. The verification thing is new, so the bugs aren't worked out. 

But the person that runs it:

[http://www.ubuntuforums.org/member.php?u=780](http://www.ubuntuforums.org/member.php?u=780)

Is one of the top members in the community. He excercises great control over his packages.

---

### Post by fannymites on 2005-07-06
Thanks again, my mind is at rest.  
I must say, I'm mighty impressed with Ubuntu so far, aside from the nightmare of getting my modem to work and the grub problem, which it turns out was probably my fault, everything is just working. It's the first time I've been able to say that about linux.
I was originally planning to replace the sources with Debian SID ones and do a dist-upgrade but I think I'll keep with Ubuntu now.

---

### Post by fannymites on 2005-07-09
Just to go back to my first problem with grub.  I have a new hard drive so I've moved things around a bit and my Windows partition is now on hdb1.
Now I am unable to boot into windows from the grub menu.  I changed the entry in grub to (hd1.0).
If I change the bios to boot from the second hard drive, Windows boots up fine so it must be something to do with grub.

---

