---
title: "Install BOINC?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Beerdrinker on 2007-01-08
Hey.

New to Ubuntu and to Linux overall. But got a "spare" computer - and wanted it to give it a go. 

And I like it!

I will probably be sneakin around to learn more, and drop a question once a while.  But for now, only question is: How do I install BOINC? (love SETI)

It should be installed so that it starts up with the desktop - without any interference.

Is this possible?

(any replys - please make "noob" tutorial ;) )

---

### Post by Falcorian on 2007-01-08
You should be able to do this from the command line:

```
sudo apt-get install boinc-manager boinc-client
```

The manager allows a graphical configuration, which should allow you to easily set it up from there. The manager can be found in Applications > Accessories > BOINC Manager, or by using:

```
boincmgr
```


There is also a package I see called boince-app-seti, but I don't know anything about that.

Hope that helps!

---

### Post by Falcorian on 2007-01-08
I haven't tried this, but it looks like you want to get the boinc-app-seti package too.

It says this about itself:

> SETI@home application for the BOINC client
SETI@home is a scientific experiment that uses Internet-connected computers in
the Search for Extraterrestrial Intelligence (SETI). This packages contains
the BOINC version of the SETI@home client. It runs under the BOINC client
which downloads radio telescope data from a network server, analyzes the data
looking for signals of extraterrestial origin, and uploads results to the
server, repeating this cycle indefinitely.


So just change my step up there to:

```
sudo apt-get install boinc-manager boinc-client boinc-app-seti
```

---

### Post by Beerdrinker on 2007-01-08
> **Falcorian said:**
> I haven't tried this, but it looks like you want to get the boinc-app-seti package too.

It says this about itself:




So just change my step up there to:

```
sudo apt-get install boinc-manager boinc-client boinc-app-seti
```


Thks!! Will try this and post result :D

---

### Post by Falcorian on 2007-01-08
> **Beerdrinker said:**
> Thks!! Will try this and post result :D

Please do, I'll be watching and try to help you through any problems.

I've just noticed your on Dapper as well. I don't know if those packages are in the Dapper repositories (I'm on Edgy). They probably are, but if not, you can use Synaptic to search for similar ones:

System > Administration > Synaptic Package Manager

Then use the search and look for boinc.

---

### Post by BWF89 on 2007-01-08
I'm using KDE and would like to know if theres a way get BOINC (or any program for that matter) to startup automatically when I log in.

---

### Post by Beerdrinker on 2007-02-05
Well, I have had no time to try this out....I am gonna try out Edgy Edge before adressing this matter again.


But thks for replys!!

---

### Post by glotz on 2007-02-05
Also check out the Folding@Home project, the link is in my signature.

It's a very important project as it directly increases our understanding of how life itself works. It's about how proteins, the building blocks of all animal life, fold. Their shape largely decides their function. This project *will* lead to remarkable new inventions.

---

### Post by 95aspire on 2007-03-16
> **Falcorian said:**
> 

```
sudo apt-get install boinc-manager boinc-client boinc-app-seti
```

sorry to bring back a dead thread but i get this when i try to install the app-seti

```
sudo apt-get install boinc-app-seti
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package boinc-app-seti

```

---

### Post by glotz on 2007-03-16
If you google for boinc-app-seti, your 8th hit is [http://packages.ubuntulinux.org/feisty/science/boinc-app-seti](http://packages.ubuntulinux.org/feisty/science/boinc-app-seti)
on which it says in screaming red letters [color=red]universe[/color].

Do you have the universe repo enabled? [https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

---

### Post by 95aspire on 2007-03-16
same thing

---

### Post by glotz on 2007-03-16
Ah, it's in the Feisty universe. My bad, soz.

---

### Post by Songwind on 2007-03-16
> **BWF89 said:**
> I'm using KDE and would like to know if theres a way get BOINC (or any program for that matter) to startup automatically when I log in.

You can create a link in ~/.kde/Autostart to any app you want to run on login.  If you need to pass it command parameters you will need to write a script instead.

---

### Post by Mrwasab1 on 2007-03-16
do we have a team for the ubuntu forums for any of the projects?
im currently running seti@home and rosetta@home, would be good to create a team and combine credits...

---

### Post by 95aspire on 2007-03-16
> **glotz said:**
> Ah, it's in the Feisty universe. My bad, soz.

sorry but explain this please? im still new to linux and i love it so far. just confusing as heck about the whole repostories thing

---

### Post by glotz on 2007-03-18
Well, there are different repos like the default repos and then universe and multiverse. And you have one for each Ubuntu version, so you've got e.g. Dapper Drake multiverse and Edgy Eft multiverse.

Take a look for example
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
[http://en.wikipedia.org/wiki/Package_management](http://en.wikipedia.org/wiki/Package_management)

Welcome to a better world! Hope your day's a good one!

---

### Post by NyteGeek on 2007-03-28
> **Falcorian said:**
> You should be able to do this from the command line:

```
sudo apt-get install boinc-manager boinc-client
```

The manager allows a graphical configuration, which should allow you to easily set it up from there. The manager can be found in Applications > Accessories > BOINC Manager, or by using:

```
boincmgr
```


There is also a package I see called boince-app-seti, but I don't know anything about that.

Hope that helps!

The version of boinc in the repositories is old, anybody know if there are any plans for the package to be updated?

---

### Post by srouquette on 2007-03-29
> **NyteGeek said:**
> The version of boinc in the repositories is old, anybody know if there are any plans for the package to be updated?

+1

---

### Post by sblanzio on 2007-04-23
> **srouquette said:**
> +1

++

---

### Post by Cheese Sandwich on 2007-04-24
I downloaded BOINC from here:

[http://boinc.berkeley.edu/](http://boinc.berkeley.edu/)

it was pretty straighforward & runs fine, though the "run after idle" preference setting seems kind of soft, as its "non-running" while I'm using the machine is actually using up the CPU, except with a process that shows as "sleeping" & nice=19...

---

### Post by padre999 on 2007-05-11
Hi

Is the autostart working for you? I downloaded and installed the newest boinc version. Then I added  boinc and boinc manager to the sessions menu. But every time I start my computer boinc manager complains that it can't connect to boinc, and boinc itself is running in the background but is not doing anything.
I get them only to work properly if I start both by double clicking them in the boinc folder from within nautilus. Even if I create menu items and start them from the menu I get the same problems as with the autostart. Weird!?

Any ideas on what I am doing wrong? Thanks.

---

