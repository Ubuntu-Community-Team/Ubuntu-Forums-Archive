---
title: "How to install OpenOffice?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by tiachopvutru on 2007-10-25
Dependency sucks, lol... I was trying to reinstall OpenOffice when I encountered the problem. After uninstalling the pre-installed OO, I went the OpenOffice site to download the .deb.tar.gz package. When I extracted the files, I found several deb inside. Some deb don't require dependency, while other do, which the dependencies (some of them, at least) should be in the same folder as well. This is where I had issue. When I stumbled through the core01 deb package, it had dependency issue, needing core02 to install first. So then, I went to the core02 deb, only to find out it needed the core01.

That whole dependency issue had also exist when I went into the terminal and type sudo apt-get install openoffice.org

Since something alike to this happened to me before, I would like to know how to get around this for future preference.

Thanks in advance :)

---

### Post by aysiu on 2007-10-25
Why did you uninstall the preinstalled OpenOffice?

---

### Post by multifaceted on 2007-10-25
Try using "Add/Remove"...

---

### Post by mmmfottrell on 2007-10-25
Just go to Applications>>Add/Remove programs.

Search for Open Office and you can install whichever parts you desire.

No need to go to the website.

If that doesn't work you can try the searching for open office in Synaptic Package Manager and try it that way.

---

### Post by magicman5421 on 2007-10-25
if add/remove doesn't work, try synaptic. it takes care of dependencies for you.

---

### Post by tiachopvutru on 2007-10-25
Thanks, I will try Add/Remove Application. It would solve the problem but I'd also like to know how to install from the file I download. All the dependencies are quite annoying so I want to know how to get around that for preference.

> **aysiu said:**
> Why did you uninstall the preinstalled OpenOffice?

I uninstalled it by going through all the openoffice.org in Synaptic and marked for uninstallation

---

### Post by taurus on 2007-10-25
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by magicman5421 on 2007-10-25
> **tiachopvutru said:**
> 
I uninstalled it by going through all the openoffice.org in Synaptic and marked for uninstallation

That tells how and not why.

---

### Post by tiachopvutru on 2007-10-25
> **magicman5421 said:**
> That tells how and not why.

I went to a thread on OpenOffice forum and it said that Ubuntu's preinstalled OpenOffice sometime gives issue so it's advisable to download the package from openoffice website and install from there instead.

---

### Post by tiachopvutru on 2007-10-25
> **taurus said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

It only says I have to take care of dependencies myself but not how... especially in situations like this

---

### Post by Buried:. on 2007-10-25
Well Sypnatic always work search for "Open Office:" and Install everything that has OpenOffice, no need for that.

---

### Post by tiachopvutru on 2007-10-25
Nevermind my question about how to install debs with dependency on each other. It looks like I have to do them in the same line of dpkg -i

Anyway, my problem is solved. Thank you to anyone who have tried to help. :)

---

