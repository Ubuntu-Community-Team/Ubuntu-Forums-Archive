---
title: "question about 7.10 repositories"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by rdsii64 on 2007-10-19
I just downloaded the 32 bit 7.10 ISO and burned it to a disc.
When I use it to upgrade my 7.04 box. will it automatically change my 7.04 repositories to 7.10 repositories?

Also I have Automatrix2 installed on my current 7.04 box. is there anything special I should know  concerning upgrading to 7.10

thanx

---

### Post by Technoviking on 2007-10-19
> **rdsii64 said:**
> I just downloaded the 32 bit 7.10 ISO and burned it to a disc.
When I use it to upgrade my 7.04 box. will it automatically change my 7.04 repositories to 7.10 repositories?

It should change the official repos from 7.04 to 7.10. If not, just open /etc/apt/sources.list with gedit and replace feisty with gutsy.

> **rdsii64 said:**
> 
Also I have Automatrix2 installed on my current 7.04 box. is there anything special I should know  concerning upgrading to 7.10

In the pass people have had problems upgrading to the next version of Ubuntu if Automatix was install, but I do not know if that is the case if upgrading 7.04 to 7.10. The best place to ask Automatix questions is on the Automatix forums ([http://www.getautomatix.com/forum](http://www.getautomatix.com/forum)).

---

### Post by mikeyphi on 2007-10-19
Unless I missed something - using the iso will give you a 'new' install not an upgrade. So, to be clear, if you install using the iso you will wipe your old os.

unless, of course, you are using the alternate CD method of upgrading!

But to answer your questions:
Yes the repositories will be changed to reflect gutsy
Automatrix2 will probably not work unless you install an 'upgraded' version

---

### Post by rdsii64 on 2007-10-21
> **mikeyphi said:**
> Unless I missed something - using the iso will give you a 'new' install not an upgrade. So, to be clear, if you install using the iso you will wipe your old os.

unless, of course, you are using the alternate CD method of upgrading!

But to answer your questions:
Yes the repositories will be changed to reflect gutsy
Automatrix2 will probably not work unless you install an 'upgraded' version
You are correct, it gave me a fresh install. Also as you suggested, I had to install Automatrix2 from scratch. So far I have no issues with my Gutsy install. All has gone pretty well.

---

