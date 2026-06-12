---
title: "Package Problems"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by dr_d on 2007-02-21
One of the reasons I like Ubuntu, is that in theory I won't have to completely reinstall my OS every time a new release comes along. This is currently not the case for Windows. However in order for this to work, the Ubuntu install has to actually last 5+ years without getting messed up to the degree that I end up wanting install the next version from scratch rather than upgrading.


Anyways, I've got a dilemma about which apt-frontend to use, Synaptic+UpdateManager _OR_ aptitude.

If I use Synaptic to install, and UpdateManager to upgrade... then I get every single change stored in Synaptic's history.

However if I use aptitude to both install and upgrade, I get no log (except for /var/log/aptitude, which doesn't last forever)... On the flipside, this method keeps my system free of orphan packages.

**Ideally, I want _both_: a detailed log of installed packages and no orphaned packages on my system. **

Now here are the solutions I see to this dilemma:

1) keep using synaptic+updatemgr... if i ever want to uninstall something, search thru the history first and make sure to get all of the orphan suckers out of the way.

2) install deborphan. however i have a question.. **if i use deborphan to remove packages will the changes be stored in the synaptic history?** is deborphan called from inside synaptic or do i use it externally?

3) find a way to make /var/log/aptitude last forever... manually copying it each time would be just as messy as manually checking synaptic history each time i want to uninstall. messing around with logrotate wouldn't be satisfactory because /var/log/aptitude doesn't have any detail and it also stores 'intended' changes.

4) find a way to make synaptic behave like aptitude. from what i've read in the forums this can't be done.



suggestions / comments / feelings ?
cheers!

---

### Post by mcduck on 2007-02-21
If you install deborphan, you can create a new filter in Synaptic to list only orphaned packages. This gives you very easy way to uninstall orphaned packages with Synaptic. Also, in Edgy apt-get has 'autoremove' feature(also accessible from Synaptic) which also helps removing unneeded packages.

I prefer apt-get/synaptic. partly because aptitude sometimes seems to do weird things..

---

### Post by dr_d on 2007-02-21
oh great! how do i set up the filter?

also what does autoremove do and how do i access it from synaptic?


thanks,
dr d

---

### Post by mcduck on 2007-02-21
First install deborphan. Then in Synaptic go to Settings/Filters, and create a new filter (you could call it 'Orphaned', and mark only 'Orphaned' on the 'Status' tab. Then Click 'OK', and now you'll find your new filter in the Custom Filters-section in Synaptic (the button is in lower left corner).

The autoremove will add a filter called 'Installed (auto removable)' in Synaptic's 'Status'-section when it detects any packages automatically installed as dependencies that are not needed any more.

To find more info about apt-get's autoremove function read this: [http://www.ubuntuforums.org/showthread.php?t=46547]("http://www.ubuntuforums.org/showthread.php?t=46547")

---

### Post by dr_d on 2007-02-22
Thanks that really helped me out!

Cheers :popcorn:

---

