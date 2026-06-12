---
title: "[SOLVED] HELP installing build-essential"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by (((X))) on 2008-01-25
I wanna install build-essential, it asks me for ubuntu cd,so I inserted it..
Now I got error: dpkg: syntax-
error unknown group debian-exim in statoveride file E: subprocess /usr/bin/dpkg returned error code (2)
packages could not be installed:(

whatcanIdo?

---

### Post by ubuntu27 on 2008-01-25
Do you have a "high speed" Internet conection? If so, you can download it from the itnernetr instead of installing from the CD> Let's try it.

Go to System/Administration/Sources (or I think it says SOftware Sources)

UNCHECK both entries were it says Ubuntu CD

CLick OK.

Now, Update the Apt  

```
sudo apt-get update
```

and try installing it again.

---

### Post by RSLxH on 2008-01-25
Open synaptic package manager, Click Settings and Sources, and uncheck the cd option. This way all your apps will come form the repo, not the cd.

[IMG]http://technical-itch.co.uk/wp-content/uploads/2007/09/screenshot-software-sources.png[/IMG]

---

### Post by (((X))) on 2008-01-25
tried both solutions, but with no positive results:
maybe the package isnt ready to be installed..I´ll wait and see then

---

### Post by stump138 on 2008-01-25
you should be able to get this package w/o issue, try this out :)  This should repair issues with apt
```
sudo apt-get -f install
```

then:
```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by (((X))) on 2008-01-25
stil no luck, I dont know how.
Now I&#7743; unable to install anything wierd..I wanted to setup wireless today, have 2 Gutsy gibbons now:)
I&#314; try all posts above tomorrow
Thanks

---

### Post by (((X))) on 2008-01-25
Thread solved!:)

I uninstalled all orphaned and resudual config-packages, disabled cd-rom.
now I&#7743; ok.
I enclose my Synaptic-history, if someone has a same problem..

---

