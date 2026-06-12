---
title: "How to uninstall all KDE-libs stuff"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-09-25
I recently installed yakuake into my ubuntu sys. (gnome only)

I remember that when I used synaptic the first time there were a few K-packages needed for it to run.

I installed the packages and since then I have not been able to get yakuake to run right.

When I F12 the terminal screen comes down but it sticks every 1/16th of an inch and draws a picture of itself so it looks as if there are 50 windows each getting progressively larger until it gets to the default size...

Anyways I wanted to get all of the associated KDE libs and dev things it installed because when I uninstall yakuake through synaptic it only pulls the yakuake package out and the problem seems to lie in the other dependent KDE packages...

I get this
charles@charles-desktop:~$ yakuake
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
Uh oh.. can't write data..

How can I pull yakuake out and take all of the dependencies that it brought with it?

---

### Post by bodhi.zazen on 2006-09-25
Use aptitude.```
sudo aptitude remove yakuake
```

---

### Post by charles.g.moore on 2006-09-25
bodhi I took it out using synaptic and also used this method each time I reinstalled and still got the same errors...any ideas?

---

### Post by bodhi.zazen on 2006-09-25
> **charles.g.moore said:**
> bodhi I took it out using synaptic and also used this method each time I reinstalled and still got the same errors...any ideas?

My only thought would be to remove it with synaptic, then install and remove with aptitude.

FYI: This is why, every now and again, you see posts advising to use aptitude.

---

### Post by bodhi.zazen on 2006-09-25
Otherwise you will have to do it manually.....

Further FYI: Aptitude is superior to synaptic at tracking dependencies. As you can see, synaptic does not remove dependencies. Aptitude will, but you have to install with aptitude first.

In your case it will be interesting to see what aptitude can do....

---

### Post by charles.g.moore on 2006-09-25
bodhi i did as you instructed but no luck I guess since I used synaptic to install aptitude has no list of dependencies associated with yakuake.

So am I right in saying that aptitude is synonomous with apt-get or are they different?  I checked each man page and they seem to have pretty much the same syntax.  Does apt-get also track dependencies like aptitude or should I use aotitude exclusively?

If so you recommend finding the package name with synaptic and then installing using aptitude ?

Would it be cool to go through synaptic find all of the KDE dependencies associated with yakuake and removing them by hand using aptitude?

Is it safe to assume that if I had a purely Gnome desktop before yakuake I can somewhat safely remove anything that starts with a "K" in the dependency list?

---

### Post by bodhi.zazen on 2006-09-25
> **charles.g.moore said:**
> bodhi i did as you instructed but no luck I guess since I used synaptic to install aptitude has no list of dependencies associated with yakuake.

I was afraid of that.

> So am I right in saying that aptitude is synonomous with apt-get or are they different?  I checked each man page and they seem to have pretty much the same syntax.  Does apt-get also track dependencies like aptitude or should I use aotitude exclusively?

Aptitude is more advanced then aptitude. Synaptic (GUI "front end") uses apt-get (CLI "back-end"). The difference comes into play not at the time of install, but rather at the time of removal. Neither apt-get nor synaptic will track the dependencies for removal.

> If so you recommend finding the package name with synaptic and then installing using aptitude ?

LOL :lol: Now I would. I am learning with you....

It takes a little more time, you will have to judge if it is worth the effort.

FYI you can install several packages at a time, just list them on the command line:
```
sudo aptitude install <package_1> <package_2>
```If that helps.....

> Would it be cool to go through synaptic find all of the KDE dependencies associated with yakuake and removing them by hand using aptitude?

Or google

[Yankuake](http://packages.ubuntulinux.org/breezy/source/yakuake)

The only package I would remove on this list is kdelibs-dev. Perhaps you can get a better list from synaptic.

> Is it safe to assume that if I had a purely Gnome desktop before yakuake I can somewhat safely remove anything that starts with a "K" in the dependency list?

I would tend to say [size=2][color=red]NO ![/color][/size]. I see the logic, but you should not remove anything you do not understand.

Unless you are willing to re-install.....

---

### Post by charles.g.moore on 2006-09-25
Well I have learned a valuable lesson and I think I will just take the yakuake package out only, just to be on the safe side...

I will just have to wait for yakuake for gnome...

Thanks for the quick responses...

---

