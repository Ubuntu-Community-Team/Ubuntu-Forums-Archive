---
title: "how do i install d loaded pkgs"
date: 2005-07-14
forum: Absolute Beginner Talk
---

### Post by QDR06VV9 on 2005-07-14
this is my first hour with ubuntu 5.04 fire fox needed an update so i did
now how do i insall it :roll:

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=runrickus]this is my first hour with ubuntu 5.04 fire fox needed an update so i did
now how do i insall it :roll:[/QUOTE]

First do this:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then go into synaptic and hit reload.

Then search for "firefox" and click the box to upgrade it. Then click apply. Life is good.

Make sure Firefox is closed while you are upgrading it in synaptic.

---

### Post by royg1234 on 2005-07-14
try with synaptic first.  If you really need to, you should get debian packages (something.deb), and get into terminal and type:

```
sudo dpkg -i something.deb
```

---

### Post by QDR06VV9 on 2005-07-14
[QUOTE=royg1234]try with synaptic first.  If you really need to, you should get debian packages (something.deb), and get into terminal and type:

```
sudo dpkg -i something.deb
```[/QUOTE]
First do this:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then go into synaptic and hit reload.

Then search for "firefox" and click the box to upgrade it. Then click apply. Life is good.

Make sure Firefox is closed while you are upgrading it in synaptic.
__________________
"Because Linux is more than just an os.Without overstating it, Linux, and the beliefs behind it, helps us, (in small or large part) define who we are, as individuals, and as a community."



did this and nothing  i'm very new to linux also
maybe  exat instructions needed i'm very sorry if this is a huge request
but i'm a fast learner thanks your help is great..

---

### Post by poofyhairguy on 2005-07-15
[QUOTE=runrickus]
did this and nothing  i'm very new to linux also
maybe  exat instructions needed i'm very sorry if this is a huge request
but i'm a fast learner thanks your help is great..[/QUOTE]

Its not a big request. We have more fleshed out isntructions. You need to do this:

[https://wiki.ubuntu.com/UbuntuBackports?highlight=%28backports%29](https://wiki.ubuntu.com/UbuntuBackports?highlight=%28backports%29)

( I would suggest this:

[https://wiki.ubuntu.com/HowToAccessTheUniverseRepository?highlight=%28universe%29](https://wiki.ubuntu.com/HowToAccessTheUniverseRepository?highlight=%28universe%29)

and this:

[https://wiki.ubuntu.com/HowToEnableTheMultiverseRepositoryInUbuntu?highlight=%28multiverse%29](https://wiki.ubuntu.com/HowToEnableTheMultiverseRepositoryInUbuntu?highlight=%28multiverse%29)

as well)

and then open synaptic how those guides say, hit reload and then hit the search button. type in firefox and hit enter. Click on the black squre next to the firefox name chose the upgrade open.

then click the apply button. new stable firefox for you.

---

### Post by poofyhairguy on 2005-07-15
Here is a good help

[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

