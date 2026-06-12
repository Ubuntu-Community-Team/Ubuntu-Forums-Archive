---
title: "[SOLVED] how do I upgrade from feisty to gutsy? (and other details: Beryl, Kubuntu, X"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by zachthejones on 2007-10-03
I'm thinking ahead at, waiting for the official release of Gutsy to upgrade from Feisty. A few questions have come up as I peruse the forums for the details:

1) How exactly do I upgrade? is there an upgrade manager I need to install?

2) Will the upgrade process take care of Beryl, or should I uninstall it before I upgrade?

3) Will Automatix interfere with the upgrade? should I just get rid of it?

4) I have installed Kubuntu and Xubuntu along with my Ubuntu - do I need to upgrade them separately, or will the Ubuntu upgrade pull in the upgrades for them?

I really don't know anything about this process, so any help/advice would be greatly appreciated!

---

### Post by bobplano on 2007-10-03
to upgrade you just need to go to the update manager when its released and click the button which says there is a new version. gutsy has compiz-fusion so i don't know how it will handle beryl; it might remove it.

it should upgrade kubuntu and xubuntu since those are just packages.

---

### Post by ThrobbingBrain66 on 2007-10-03
1) When Gutsy is officially released you probably will be presented with an option to upgrade when you start up update-manager.  Otherwise you can enter 'update-manager -d' into a terminal to start the upgrade process.

2) Gutsy comes with Compiz Fusion by default, so uninstalling Beryl is a good idea.  Also, get rid of any 3rd-party Feisty repos you have as they could cause problems with the upgrade.

3) See #2 :) [URL="http://mjg59.livejournal.com/77440.html"] Technical Review of Automatix
[/URL]
4) Unless you have Kubuntu and Xubuntu on seperate partitions, upgrading to Gutsy will upgrade EVERYTHING.  No need seperate upgrades.

---

### Post by xcesarfrancox on 2007-10-03
Hi dude, to upgrade from feisty to gutsy simply do this, hit alt+f2 and type in the following:

```

update-manager -d

```

then you'll see something saying you can upgrade your distro to 7.10, click on it and follow the steps

About beryl, gutsy comes with compiz fusion automatically activaded by default so you won't need it

Automatix... I don't know because I haven't used it and about kubuntu and xubuntu I guess they will be upgraded as well, I dn't really know...

Hope I have helped you ;) :)

---

### Post by tdrusk on 2007-10-03
> **xcesarfrancox said:**
> Hi dude, to upgrade from feisty to gutsy simply do this, hit alt+f2 and type in the following:

```

update-manager -d

```

then you'll see something saying you can upgrade your distro to 7.10, click on it and follow the steps

About beryl, gutsy comes with compiz fusion automatically activaded by default so you won't need it

Automatix... I don't know because I haven't used it and about kubuntu and xubuntu I guess they will be upgraded as well, I dn't really know...

Hope I have helped you ;) :)
Keep in mind this tip is for upgrading now, not in two weeks.

---

### Post by zachthejones on 2007-10-04
Thanks guys! Will the "update-manager -d" still work after the official release?

---

### Post by ThrobbingBrain66 on 2007-10-04
yes. :)

---

