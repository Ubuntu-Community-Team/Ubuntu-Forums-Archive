---
title: "upgrading ubuntu"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by chubbiecanuk on 2007-08-06
I sent for the Ubuntu disks last year and recently installed them on a separate system to play with..

Now I want to upgrade to a newer release, and don't want to overwrite everything on the disk..

how do I go about just upgrading??

---

### Post by PriceChild on 2007-08-06
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) Is a good guide to get through it.

Please remember to always keep backups of important data.

---

### Post by Rocket2DMn on 2007-08-06
Have you checked out [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
This is the suggested approach from going to Edgy to Feisty.

---

### Post by greybit on 2007-08-06
Do you have an internet connection?  If so you can simply type the following in a terminal:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

Or, graphically in gnome:

Click System -> Administration -> Update Manager where you can install updates and upgrade the distribution if a new one is available.

If you don't have an internet connection you can send for the new disks and upgrade with them.

---

### Post by chubbiecanuk on 2007-08-06
[QUOTE=greybit;3144569]Do you have an internet connection?  If so you can simply type the following in a terminal:

```

sudo apt-get update
sudo apt-get dist-upgrade

```


hmm...  I tried this an got 0 upgraded, 0 newly installed, 0 to remove, and 0 not upgraded..

any idea what went wrong..

---

### Post by greybit on 2007-08-11
You may already be up to date then.  Do you know what version of Ubuntu you have installed?  Feisty Fawn 7.04 is the latest non-experimental release.  You can check what kernel you are using by typing into a terminal:

```

uname -r

```

I have 2.6.20-16-generic installed.

You could also fiddle around with your repository sources:

Click System -> Administration -> Software Sources

Then click on the Updates tab and check the boxes of the updates you are interested in.

Then try running

```

apt-get update
apt-get dist-upgrade

```

again.

If you get the same response I'm guessing you're probably up to date.  If you want to search for new packages to install you can proceed with any of these steps:

Click Applications -> Add/Remove
where you can pick programs to install.

Click System -> Administration -> Synaptic Package Manager
where you can also pick programs to install.

Open a terminal and type:
```

apt-get update
apt-cache search program

```
where "program" is replaced with a particular program or program description that can consist of one or more words.  After finding a program that you are interested in installing you can type:
```

apt-get install program

```
where "program" is replaced with the specific name of the package listed when you did the search.

Oh, I'm assuming here that you are using the gnome desktop environment, but perhaps you are using KDE?  Well, if you are, the movements through the menus may be a little bit different but the commands executed in a terminal will work the same.

I hope this helps.

---

