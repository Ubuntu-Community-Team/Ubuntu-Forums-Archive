---
title: "Can't install anything."
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by mari102 on 2008-02-17
yeah I want to install hellanzb, and it's supposed to be in the repositories right?

I'm new to ubuntu and just installed it when I try;

sudo apt-get install hellanzb 

I get E: Couldn't find package hellanzb.

when I try to install unrar;

sudo apt-get install unrar

Package unrar is not available, but is reffered to by another package.  This may mean that the package is missing, has been obsoleted or is only available from another source.  
E: Package unrar has no installation candidate.

It's the same with par2.

I updated and upgraded. 

sudo apt-get update
sudo apt-get upgrade 

It worked and I restarted but it's the same thing.

Say theoretichally someone wanted to be able to get an nzb downloader so they could get a vista cd image from usenet so they could go back to an OS where installing their tablet driver takes 3 clicks of 'next' as opposed to having to follow a 100+ page documentation that assumes you have a degree in computer science, compiling a bunch of files editing x conf, tweaking kernal etc...

This could be quite a troublesome matter.

tetsudattemorau! ^^

---

### Post by adi_das on 2008-02-17
If u dont know how to use commands in Terminal , then learn it and use it. the simple way to install is go to synaptic and install the package that you need. 


If your question is answered by a User , dont forget to say him thanks .

---

### Post by kagashe on 2008-02-17
> **mari102 said:**
> yeah I want to install hellanzb, and it's supposed to be in the repositories right?No.

Read on [this page]("http://www.ubuntugeek.com/nzb-par-and-unrar-all-in-one-using-hellanzb.html") about installing this package.

kagashe

---

### Post by gfg on 2008-02-17
You should try to use the Add/Remove applications program. There is no need to use the terminal to install programs if you don't want to, or are not familiar with it.

---

### Post by jan quark on 2008-02-17
make sure your software sources are enabled
got to

system> administration > software sources
and check all sources then reload

and try to install again

---

### Post by mari102 on 2008-02-17
Kagashe, thanks for trying to help, but following that guide to a T I get...

sudo apt-get install python-dex python-twisted unrar par2

Reading package lists...Done
E: Couldn't find package python-dex

Even if hellanzb aint, I'm sure python-dex, unrar etc. are in the repositories aren't they?

Which brings us back to the topic of this thread, why cant I install anything?



> ~Oh Vista never did I know how much you meant to me, fear not my love for soon I shall returneth to thee.~

---

### Post by mari102 on 2008-02-17
jan quark, ty, they're not all added, shall try and report back

---

### Post by jan quark on 2008-02-17
yes check them and reload

and try to install again:)

---

### Post by ashmew2 on 2008-02-17
All you're missing are the Universe and Multiverse Repositories. You might want to read this :

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by mari102 on 2008-02-17
thanks alot jan, seems to have worked, well I'm half way there thanks to you....

install from command line aint working for some reason but I managed to score python-dev/twisted unrar and par2 via synaptic. now the journey to install hellanzb -_-

---

