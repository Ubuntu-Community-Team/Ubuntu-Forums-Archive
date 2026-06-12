---
title: "how to time an application?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2007-09-05
is there a way i can make an application execute every night?

---

### Post by Sensenseppl on 2007-09-05
Yes. :)

```
man crontab
```

---

### Post by RomeReactor on 2007-09-05
Hi. You can also use [gnome-schedule]("http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html"), which will let you do it through a graphical interface.

---

### Post by jinxjinx on 2007-09-05
Hi thanks,

For some reason i cant seem to find gnome-schedule

what repo is it in?

Thanks!

heres my sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
#AUTOMATIX REPOS END
 deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
 deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
 deb [http://media.blutkind.org/xgl](http://media.blutkind.org/xgl) edgy main (latest: beryl 0.1.1)
deb [http://beryl.xglusers.de/](http://beryl.xglusers.de/) edgy main (latest: beryl 0.1.4; no aquamarine) deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn ( bleeding edge beryl development, use with care )
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

---

### Post by RomeReactor on 2007-09-05
It's in universe; you shouldn't have had a problem installing it. Try from the command line:
```
sudo apt-get update
```
and
```
sudo apt-get install gnome-schedule
```

---

### Post by mahiyar on 2007-09-05
Maybe you can get it from here? gnome-schedule.sourceforge.net

---

### Post by RomeReactor on 2007-09-05
> **mahiyar said:**
> Maybe you can get it from here? gnome-schedule.sourceforge.net

Or alternatively you can get the official .deb package from [here]("http://packages.ubuntu.com/feisty/gnome/gnome-schedule").

---

### Post by Jason Weiss on 2007-09-05
I am trying to use gnome-schedule but I am having trouble with the commands, 

I am not sure what to enter to make the deluge open at midnight and close at midday.

---

