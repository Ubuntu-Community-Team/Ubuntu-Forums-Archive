---
title: "Want to switch to KDE from GNOME without upgrading to EE"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Chake99 on 2006-11-05
Just looking for clarification, I found this tutorial online:

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

And it says to sudo aptitude update before going for a sudo aptitude install kde-desktop. I'm wondering if just doing the sudo aptitude install kde-desktop would somehow muck up my system, as I do not want to chance an Edgy Eft installation.

---

### Post by MasterOfDisaster on 2006-11-05
It should not damage or muck up your system, although your will have a multitude of libraries lying around.  Installing kde-desktop means that at your login screen, you can choose from Gnome Session or KDE Session.

Anyways, it works.

---

### Post by Epperly on 2006-11-05
You would do sudo apt-get install kde-desktop ,then once installed logout you would go to options>select session, and choose KDE. All the same programs will still be installed, along with the new KDE ones. The panel-customization might be different though, but that's easy to fix(never switched outta Gnome so I'm not sure)

[edit]oops haha I didn't realize you posted a link with the instructions already, sorry
also on that site if you're sticking to KDE only, you should try "pure KDE" as listed to get rid of all the gnome stuff you'll have lying around[/edit]

---

### Post by CatKiller on 2006-11-05
The update won't upgrade to Edgy. Since Dapper is LTS, they aren't going to upgrade you unless you make a particular effort to. The update just means that you have an up-to-date package list to choose from.

---

### Post by Epperly on 2006-11-05
Well, he posted he doesn't particularly want to upgrade to Edgy, though.

---

### Post by bsussman on 2006-11-05
> **Chake99 said:**
> And it says to sudo aptitude update before going for a sudo aptitude install kde-desktop. I'm wondering if just doing the sudo aptitude install 

Please consider learning the difference between update and upgrade.

If you never do update, you will never get bugfixes.

update has nothing to do with 6.10 - the 6.06 repositories do not see 6.10 code.  Ever.

---

### Post by Chake99 on 2006-11-05
Thanks for the info.

Does pressing the orange button that launches the GUI updater do the same thing as the sudo aptitude update though?

---

### Post by NeoLithium on 2006-11-05
Yes it does do the same thing :)

---

### Post by aysiu on 2006-11-05
> **Chake99 said:**
> Thanks for the info.

Does pressing the orange button that launches the GUI updater do the same thing as the sudo aptitude update though?
No, it's different.

```
sudo aptitude update
``` merely checks to see what software is available for installing/upgrading.

The orange button is the equivalent of ```
sudo aptitude update
sudo aptitude dist-upgrade
``` which will not only check what's available but install any necessary upgrades.

---

### Post by ewl1217 on 2006-11-05
Since there seems to be some confusion about the seperation of Dapper and Edgy, let me explain. All software avaliable from Ubuntu is stored in online repositories. Edgy and Dapper use entirely seperate repositories, so unless you edit the file /etc/apt/sources.list, you will still be using Dapper. In that case, you will continue to receive updates for Dapper, but likely only bug and security fixes. This is ideal you want a rock-solid system (well, software at least). You can however, by editing the sources.list file, switch over to the Edgy repositories, where you will find many, many feature and major version updates (although probably not as stable, since it isn't as tried and true). Since Dapper is a Long Term Support (LTS) release, you can continue using it for quite a while now and still receive updates. Really, there's no major reason to upgrade to Edgy, unless you prefer being on the cutting edge or are having problems with Dapper that may have been resolved in Edgy.

---

