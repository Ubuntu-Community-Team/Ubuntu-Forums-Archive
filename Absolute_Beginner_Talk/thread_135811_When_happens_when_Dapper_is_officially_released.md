---
title: "When happens when Dapper is officially released?"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by WackToMack on 2006-02-24
Hello again everyone.  So, what happens when Dapper is officially released?  Does Ubuntu update itself to from whatever version it is now, (for me it's Breezy) to the new version with Update Manager?  Or do we have to download/order CD's of Dapper and upgrade that way?  Do all the programs we have gotten through downloading/Synaptic roll over from the previous version of Ubuntu to the next?  I am just concerned because having to download and install all those programs again just to lose them in another 6 months is kinda a pain the the rear end.  Thanks in advance! :D

---

### Post by Stormy Eyes on 2006-02-24
When you're ready to upgrade to Dapper, you will have to configure Synaptic to point to the Dapper repositories instead of Breezy's. Or, if you don't mind doing it from the command line, you can do the following:

1. Press ALT+F2 and type in the following command:
```
gksudo gedit /etc/apt/sources.list
```

2. Use the "Find" button, type "breezy" into the find box and "dapper" into the replace box, and then press "Replace All". Save the file and close it.

3. Open a terminal and enter the following commands:
```
sudo apt-get update
sudo apt-get dselect-upgrade
```

Your upgrade is complete, barring problems. Save your files, log out, and log back in again. You may want to just reboot, but that shouldn't be necessary.

---

### Post by annsachd on 2006-02-24
Very interesting. Thanks for the post.

---

### Post by az on 2006-02-25
[QUOTE=Stormy Eyes]When you're ready to upgrade to Dapper, you will have to configure Synaptic to point to the Dapper repositories instead of Breezy's. Or, if you don't mind doing it from the command line, you can do the following:

1. Press ALT+F2 and type in the following command:
```
gksudo gedit /etc/apt/sources.list
```

2. Use the "Find" button, type "breezy" into the find box and "dapper" into the replace box, and then press "Replace All". Save the file and close it.

3. Open a terminal and enter the following commands:
```
sudo apt-get update
sudo apt-get dselect-upgrade
```

Your upgrade is complete, barring problems. Save your files, log out, and log back in again. You may want to just reboot, but that shouldn't be necessary.[/QUOTE]


I *think* that the update notifier will ask you if you want to upgrade.  You should not have to change you source lists by hand (either by the comman line or by tweaking it with synaptic)  This is a new feature for breezy (that we won't notice we have untill Dapper releases), I think.

---

### Post by fredtal on 2006-02-25
What about for those of us with slow modems who prefer to get another CD?

---

### Post by engla on 2006-02-25
[QUOTE=azz]I *think* that the update notifier will ask you if you want to upgrade.  You should not have to change you source lists by hand (either by the comman line or by tweaking it with synaptic)  This is a new feature for breezy (that we won't notice we have untill Dapper releases), I think.[/QUOTE]
Nope nope, sadly not so.

Someone is developing a new application that will do release upgrades for this, but what I understand it will only experimentally upgrade from breezy to dapper -- you have to install the package yourself. I don't know if this is going to ship with dapper, but I certainly hope so.

---

### Post by engla on 2006-02-25
[QUOTE=fredtal]What about for those of us with slow modems who prefer to get another CD?[/QUOTE]
Just like you can install extra packages from an install CD, you should be able to do this update with a CD too, with some caution.

*I don't know this* but in theory it should be like:
You add the CD in synaptic (Some menu > Add CD-ROM...) then disable all other repositories, mark all upgrades and apply.

---

### Post by az on 2006-02-25
[QUOTE=engla]Nope nope, sadly not so.

Someone is developing a new application that will do release upgrades for this, but what I understand it will only experimentally upgrade from breezy to dapper -- you have to install the package yourself. I don't know if this is going to ship with dapper, but I certainly hope so.[/QUOTE]
[https://launchpad.net/distros/ubuntu/+spec/release-upgrades](https://launchpad.net/distros/ubuntu/+spec/release-upgrades)

That is more current than [https://wiki.ubuntu.com/AutomaticUpgrade](https://wiki.ubuntu.com/AutomaticUpgrade)

---

### Post by gtkourounis on 2006-03-16
after you follow all these steps should the desktop look like all those screenshots from the dapper drake test pages? because i followed everything and it worked fine but... it stays with the same skin and everything, and i did restart my computer. Is it because i am running an AMD Turion64?

---

### Post by GarethMB on 2006-03-16
Do the feature is 6.04 warrant upgrading as soon as its released? What is going to be so radically different.

---

### Post by lucia_engel on 2006-03-16
Would it be safer or more stable if I do a clean install (wipe the partition and install Dapper)?

---

