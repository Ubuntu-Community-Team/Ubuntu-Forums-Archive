---
title: "Updates"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Uncle_John on 2006-09-02
This question may be stupid](*,)  but what do you think is recomended to install 
all updates? Which one if not all? Is there need to install any of them?

---

### Post by Jussi Kukkonen on 2006-09-02
Definitely install all security updates. 

The rest is debatable: do you want to take a small risk of things breaking because of the updates to get small bug fixes? For servers you probably won't, for desktop you might (I do).

---

### Post by Uncle_John on 2006-09-02
How do you know which are security updates?
Do you have to check every single security update?
And do all those updates take a lot of disk space?(in case i install all of them?)

---

### Post by Jussi Kukkonen on 2006-09-03
> How do you know which are security updates?
By their source. Look at *Settings-->Repositories-->Installation Media* in Synaptic, and check the ones you want (like only "security updates"). In command line you can do the same by editing */etc/apt/sources.list*.

> Do you have to check every single security update?
Not sure what you mean. If you have automatic updates on, you will get a notice saying "there are updates available" or something like that -- this will include every update from sources you have selected in *Settings-->Repositories-->Installation Media*...

> And do all those updates take a lot of disk space?(in case i install all of them?)
Not really -- they may be large downloads (as the update system currently downloads the whole package even if the change is really small), but the installed size rarely changes.

---

