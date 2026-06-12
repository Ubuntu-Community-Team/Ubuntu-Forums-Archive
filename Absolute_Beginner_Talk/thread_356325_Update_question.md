---
title: "Update question ??"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-02-08
Why is my security updates showing unchecked and uninstalled?  The older ones are installed,but the new ones are greyed out !  Any thots would be appreciated.  They aren't locked BTW.

---

### Post by dannyboy79 on 2007-02-08
not sure what you mean but could you post the output from typing this into the terminal.
sudo cat /etc/apt/sources.list

make sure you post all of it. thanks. also, have you gone into the various gui locations which set the defaults for how your system is automatically updated? I think 1 place is under System, Admin, Synaptic, then within there you can look in preferences or somethin like that. I am not at home so I can't tell you exactly where to look but if you don't find it let me know and I can repost when I get home later.

---

### Post by banditti on 2007-02-08
This is just a suggestion, but there are quite a few threads about this, can we consolodate?  this has the most posts:

[http://ubuntuforums.org/showthread.php?t=356257](http://ubuntuforums.org/showthread.php?t=356257)

---

### Post by dannyboy79 on 2007-02-08
> **banditti said:**
> This is just a suggestion, but there are quite a few threads about this, can we consolodate?  this has the most posts:

[http://ubuntuforums.org/showthread.php?t=356257](http://ubuntuforums.org/showthread.php?t=356257)

I disagree, his problem has to do with HOW is system defaults are set as far as what gets updated and when. The thread you linked to has to do with things being held back due to Nvidia issues and other things like that. He can do what he wants but I don't believe they are similar issues.

---

### Post by banditti on 2007-02-08
My bad.

---

### Post by MrKlean on 2007-02-08
Here ya are dannyboy

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./
#ntfs-3g & fuse-2.5 repo
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main
deb-src [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main
deb [http://debian.websterwood.com/](http://debian.websterwood.com/) edgy main
deb-src [http://debian.websterwood.com/](http://debian.websterwood.com/) edgy main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END

---

### Post by dannyboy79 on 2007-02-08
well Ijust wanted to see if you had the main security repo uncommented and it appears as though you do. what happens when you do a sudo aptitude update and then a sudo aptitude -s upgrade. which should simulate an upgrade per the man pages. otherwise did you look in the locations that I suggested about how your install will automagically update it's security? other than that, I can't tell ya? this might mean that those udpates that you see greyed out are for the universe and multiverse only since you don't have those uncommented.

---

### Post by MrKlean on 2007-02-08
Thanks...I'll un comment those and see what happens ; )
Thanks again !

---

### Post by MrKlean on 2007-02-08
Nope...still won't update....it's a linux-header-generic and 2 others....maybe they're down for some reason ???

---

### Post by louieb on 2007-02-08
I don't know what going on but the updater displayed a message box with:
```
Cannot install all available updates

Some updates require the removal of further software. 
Use the function "Mark All Upgrades" of the package manager "Synaptic" 
or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.
 The following updates will be skipped:

linux-image-386
linux-restricted-modules-386
```Been using Ubuntu Dapper since it came out. Never seen anything like this before. Wonder what is going on?

---

### Post by jd65pl on 2007-02-08
There is a problem with a kernel update see this [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73)

---

### Post by dannyboy79 on 2007-02-08
> **MrKlean said:**
> Nope...still won't update....it's a linux-header-generic and 2 others....maybe they're down for some reason ???

OK, wait a second. You specifically stated that they were something like security updates. If you had stated exactly what they were, and I would have known that you were referring to this, I could have answered this long ago. Read the last post and you'll have your answer. Hell that guy who jumped in in the begining tried telling us this but since you said somehting about security updates not being downloaded I didn't think you were referring to the kernel images etc etc. Next time when you see an error, it's best to inform people exactly what the error is instead of beating around the bush. I am glad that this is now resolved. Well it's not, but at least now you know you go to the this thread ([http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408)) and find out what to do if anything yet.

---

### Post by jd65pl on 2007-02-08
dannyboy79

This guy was just reading it like he saw it and thats exactly what you see when you use the update manager. Bad error reports are always a problem but the reporter isn't (usually) trying to be difficult.

---

### Post by MrKlean on 2007-02-08
Dannyboy,  sorry for the confusion...but it did say security updates..Next time I'll make sure I have the info clearer.  Thanks for the help ; )

---

### Post by raydekok on 2007-02-09
same problem here. i don't know what's happening. it is since 2 days, day before it worked.

---

### Post by jd65pl on 2007-02-09
raydekok: look at my link at the top of this page.

---

