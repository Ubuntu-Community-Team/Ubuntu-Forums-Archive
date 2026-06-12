---
title: "How to see the content of only one repository"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by imaginos on 2006-10-12
I made my own local repository, and i want to instruct synaptic to show me ONLY packages from it. I don't want to browse through thousands of packages from remote repos, because I have selected just wnat I need in that local repo.

Ofcourse, after i'm done with installation, i would like to make contents of remote repos visible again.

How?

P.S.
Is it possible to make a script that will delete (and backup, ofcourse) /etc/apt/sources.list, then put only one line in it like this:
**deb file:/media/hda4/my/ instals/**
then:
**apt-get update**
and then:
[b]aptitude opera
aptitude thunderbird
aptitude sun-java5-jre
aptitude sun-java5-jdk[/b]

etc...

and then restore the backup of /etc/apt/sources.list, and:
**apt-get update**

? Will that work?

---

### Post by Iarwain ben-adar on 2006-10-12
Hi

To see the contents of your repo, try disabling the others..

Like this :D
```
gksudo synaptic
OR
kdesu adept
OR
sudo nano /etc/apt/sources.list
```

If you are in Gnome, Kde, or via CLI

There you just disable the other repo's
(in CLI this is using # infront of the repo's address)


Iarwain

---

### Post by imaginos on 2006-10-12
Thank you.

I tried to comment them, but Synaptic still shows a lot of packages, even after "Reload".

Then, I **deleted** all lines in sources.list except one:
**deb file:/media/hda5 installs/**

and still, Synaptic shows everything. 
It must have stored the list of packages somewhere, and won't refresh it. :( :(

P.S. now I see! 
It shows INSTALLED packages also. How can I hide them in Synaptic?

---

### Post by Iarwain ben-adar on 2006-10-12
Hi,
you could try to search for a way to unmark them..

In Adept it looks like this =>
[[IMG]http://img226.imageshack.us/img226/4882/adeptkz2.th.png[/IMG]](http://img226.imageshack.us/my.php?image=adeptkz2.png)

Just beneath the "Search" option, you have the "Show" option ;)
Untick "installed"


Iarwain

---

### Post by imaginos on 2006-10-13
Well, I have Ubuntu, so I don't have Adept. But, I have Synaptic. :)

Anyway, I can choose to see unistalled packages, but I need to see installed AND uninstalled packages ONLY from one specific repository.

---

### Post by anaconda on 2006-10-13
> **imaginos said:**
> 

P.S.
Is it possible to make a script that will delete (and backup, ofcourse) /etc/apt/sources.list, then put only one line in it like this:
**deb file:/media/hda4/my/ instals/**
then:
**apt-get update**
and then:
[b]aptitude opera
aptitude thunderbird
aptitude sun-java5-jre
aptitude sun-java5-jdk[/b]

etc...

and then restore the backup of /etc/apt/sources.list, and:
**apt-get update**

? Will that work?

That would definitely work, exept that you use apt-get to update and aptitude to install?? ööö.. why..?
how about;
apt-get update
apt-get install opera
etc..
and then restore the backup of /etc/apt/sources.list, and:
apt-get update

OR
aptitude update
aptitude install opera
...

I am not 100% sure, but I think you shouldn't mix the apt-get and aptitude like that..

---

### Post by imaginos on 2006-10-13
Really, you got the point! :)

I thought that apt-get update will refresh package list from repositories (on, in this case, one repository). I didn't know about **aptitude update**. :)

I thought to use aptitude because it remembers dependencies, and that could be useful for uninstalling packages..

Thank you for the answer!

---

