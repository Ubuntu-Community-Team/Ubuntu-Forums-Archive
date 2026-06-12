---
title: "Absolute Beginner"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Exodus00FF on 2007-03-28
Hi all, 
I'm a beginner in linux and I'm trying to find out if anyone here has ever tried install Redhat Package Manager into Ubuntu.  If so would anyone be able to give me a tutorial into how to do it.

Thanks everyone for the help in advanced!

---

### Post by chili555 on 2007-03-28
No, and I never tried to put a Ford motor in a BMW, either.

Red Hat is an rpm-based distribution and Ubuntu is based on Debian, which is a deb-based distribution. Ubuntu uses a great update manager and synaptic which kick Red Hat to Chicago and back.

My assertions are based on many years experience with Red Hat's younger sister, Fedora Core. If I have misread your intention and objective, always a possibility, please post back and we can try again.

---

### Post by Stickymaddness on 2007-03-28
Why oh why would you want to install Redhat Package Manager into Ubuntu??? Synaptic (Ubuntu's package manager) is a thousand times better than dealing with ikky rpm's !!

---

### Post by brennydoogles on 2007-03-28
> **Exodus00FF said:**
> Hi all, 
I'm a beginner in linux and I'm trying to find out if anyone here has ever tried install Redhat Package Manager into Ubuntu.  If so would anyone be able to give me a tutorial into how to do it.

Thanks everyone for the help in advanced!

I would say that it's not a good idea. Is there a specific package that you need and can't find in Synaptic? You may need to [add some repositories (link)]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories"), or you may be able to [install the package via source code (link).]("http://www.monkeyblog.org/ubuntu/installing/") If you need help with anything just feel free to ask, and the community is usually very good at getting good answers to you quickly!!

---

### Post by mac.ryan on 2007-03-28
Hi Exodus, and welcome in the magic world of Linux... Other users have already pointed out that installing a RPM system in ubuntu doesn't sound like a gorgeous idea.

Beside any technical consideration (that I leave to more experienced users than me), it is primarily a matter of what I would call "system coherence": one of the most salient characteristics of ubuntu is its user-friendliness, and ease of use, and if you would force RPM into the system, this would probably degenerate in something difficult to manage coherently (just think to all the management of dependencies between different programs...).

Anyhow, if you are really in need to get a RPM program running on ubuntu, you might give "alien" a try:

[http://kitenet.net/~joey/code/alien.html]("http://kitenet.net/%7Ejoey/code/alien.html")

I never used it myself, but... well, I thought you wanted to know about its existence.

If you have access to the source code of the program you want to install, I believe it would be however safer to compile the entire program from the scratch rather than using alien.

Best luck for your journey into GNU/Linux, it's a steep learning curve, but it is worth it! :)

---

### Post by Yoooder on 2007-03-28
> **Exodus00FF said:**
> Hi all, 
I'm a beginner in linux and I'm trying to find out if anyone here has ever tried install Redhat Package Manager into Ubuntu.  If so would anyone be able to give me a tutorial into how to do it.

Thanks everyone for the help in advanced!

Nope, but there is a program called "alien" which is available within Ubuntu's software library that can convert most RPMs into .deb packages.  This allows you to manage the package using Ubuntu's main package management system, apt.

---

### Post by Exodus00FF on 2007-03-29
Like I said I am new to linux and this is one of my second expiriences with it, my first expirience is with redhat/fedora and I am familiar with using RPM.  Is there a good tutorial somewhere on installing with .deb or converting rpms to .deb in ubuntu?

---

### Post by mac.ryan on 2007-03-29
> **Exodus00FF said:**
> Like I said I am new to linux and this is one of my second expiriences with it, my first expirience is with redhat/fedora and I am familiar with using RPM.  Is there a good tutorial somewhere on installing with .deb or converting rpms to .deb in ubuntu?

Most of the packages (over 20.000) can be installed from "synaptic package manager" in the System menu, it is rather intuitive... please have a look to the "setting/repositories" if you want to enable ubuntu to install even more packages.

Anyhow, the link that brenny mentioned in his post for installing from source gives you a comprehensive view on synaptic as well:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

Enjoy! :)

---

### Post by chili555 on 2007-03-29
To install a package in Ubuntu:```
sudo dpkg -i <package_u_want>.deb
```Remove with *sudo dpkg -r* By far, the easiest way is with Synaptic. System -> Administration -> Synaptic Package Manager. Start with Settings -> Repositories and select everything you can. Close Repositories and press Reload. That will load up the packages from the new repositories you selected. 

Now, search for something you want to install, say dvdrip. Yes, it's there! Right-click and select Mark for installation. If there are dependencies, they will be taken care of. Click apply and quickly, your package will be installed.

Converting an rpm to a deb to install is pretty tricky and risky. I would stick with official Ubuntu debs if at all possible.

---

