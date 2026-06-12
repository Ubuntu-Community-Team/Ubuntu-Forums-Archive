---
title: "New Installation, missing libraries, and upgrades"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by jbskaggs on 2008-03-29
Today was my forth Ubuntu Linux installation and by far the toughest.

Usually I put a cd in my drive press go and the thing installs itself.

NOT today.

Today my internet router changed passwords so the installer could not access the internet, but it installed 7.10 anyway.

I rebooted and it raan vry smooth and fast on an acer 3680 aspire notebook with 1gb mem.

I was so excited I was about to install a application I wrote on Gambas for book writers, when my app would not install said Dependency is not satisfiable:gambas2-runtime.

went to upgrade manager said I was upgraded. Went Synaptic manager said I was upgraded.  So I manually started installing libraries and learned I was missing hundreds of files.

Tried to apt get and some worked some didn't- you know the drill a convulated chase of dependent libraries thru the internet, help boards etc.

So eight hours later i go back to add / remove applications and it just kept reloading the source list everytime i pushed the button.  So it hit me- the upgrade and package managers were not going online!

I then went to preferences on add/ remove and saw that all upgrades via the internet had been turned off.  So I turned them on and viola!  I am now upgrading / installing the missing 222 files!

SO if you have a problem like mine where the add / remove is not working, upgrade manager isn't working- check add / remove to see if the internet access is turned off for application sources.

JB SKaggs

---

