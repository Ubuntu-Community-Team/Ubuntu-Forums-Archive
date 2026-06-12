---
title: "ubuntu to xubuntu"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by agentc0re on 2006-10-28
i currently have a pentium III 677 (maybe, i can't remember it's old) laptop.  i mainly just use it to browse the web and try to learn linux off it.  when i heard edgy came out i went to the website to see what i needed to do to upgrade.  So i guess here's my 2 questions.

to upgrade to edge do i need to download the iso or is there an a!tual upgrade package that is going to come along with my update manager that im running right now for all updates?

and 2
when i went to the site i saw xubuntu, so i checked it out and it looks like it is designed for slower machines like mine.  if i wanted to switch distro's would i  need to wipe and reinstall?

any help or suggestions is much appreciated.
thanks guys

---

### Post by John.Michael.Kane on 2006-10-28
Fresh install is the best way to go.

However if you want to upgrade from where your at [COLOR="Red"]**you do so at your own risk**[/COLOR]

```
sudo aptitude install xubuntu-desktop
```

Followed by this.

```
sudo gedit /etc/apt/sources.list
```
replace all the words that have dapper to edgy

Then run these:
```
sudo aptitude update 
sudo aptitude dist-upgrade
```

---

### Post by gn2 on 2006-10-28
I recently did one of those things, which was to get Xubuntu.

I just marked Xubuntu-desktop for installation in Synaptic, 45mb and ten minutes later I had Xubuntu.

When re-booting select xfce session and it will start Xubuntu.

I created a new user for Xubuntu, and I can go back to my Ubuntu by switching user if required.

Xubuntu seems generally quicker than Ubuntu opening applications on my P3 500mhz 192mb RAM Portege 3440CT

Haven't tried 6.10 yet, too soon for me......

---

### Post by David_T on 2006-10-28
No you don't need to reformat/reinst.
You would just want to do:
```

sudo apt-get install xubuntu-desktop

```

Then after getting things the way you want in dapper, you can upgrade to
edgy by doing dist-upgrade.  The normal guides to doing this upgrade still apply to xubuntu.

I started out installing ubuntu dapper, and I have apt-got my way to xubuntu edgy.

---

