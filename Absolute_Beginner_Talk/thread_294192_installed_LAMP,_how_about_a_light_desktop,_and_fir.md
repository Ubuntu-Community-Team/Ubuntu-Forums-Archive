---
title: "installed LAMP, how about a light desktop, and firefox/blufish?"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by bowie101 on 2006-11-06
hi all. after much tribulation , I've installed Dapper's Lamp server on an old laptop that has no internet connection to it. (I'm doing this for learning and testing.) 

I now want to install a light-weight desktop on it, as the computer is only 128mb RAM.... And then *firefox* and *bluefish* to enable editing and browsing of localhost. 

no internet connection for the computer in question, and what i'm on now is dial-up. 

the disks i have are: 

ubuntu dapper drake desktop cd, 
the server cd that i just installed, 
xubuntu dapper drake alternate install cd.

i thought i had xubuntu regular install of drake, but that image is no good.

do i have all i need? how do i proceed? hey, is there any documntaion on this stuff, as i sure don't see any!

---

### Post by devilsadvocate1987 on 2006-11-06
there is some way to use the alternate install cd as a repository. look around in the forums for that, its pretty straigtforward. add the xubuntu alternate cd as a repo and install xubuntu

---

### Post by Bachstelze on 2006-11-06
```

sudo -i
echo "" > /etc/apt/sources.list
apt-cdrom add
* insert your xubuntu alt cd and press Enter, apt will scan it for the packages list *
apt-get install xubuntu-desktop

```

voilà :) Some people will certainly suggest *aptitude* instead of *apt-get*, you can use either. It won't make the slightest difference.

---

### Post by bowie101 on 2006-11-06
god bless you! will try it now..

---

### Post by devilsadvocate1987 on 2006-11-06
you might have to do apt-get update before installing

---

### Post by Bachstelze on 2006-11-06
Nope, apt-cdrom does it automagically ;)

---

