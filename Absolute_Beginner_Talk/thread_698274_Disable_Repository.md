---
title: "Disable Repository"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Krishnan.V on 2008-02-16
How do i disable repositories from internet when i update it through my Dvd

---

### Post by forestpixie on 2008-02-16
you can either use the software sources app in system>admin or edit your sources.list and put a # in front of those you don't want to use

```
gksudo gedit /etc/apt/sources.list
```

to back it up 

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

---

### Post by billgoldberg on 2008-02-16
An easier way would be to go to "system -> administration -> synaptic package manager".

Then go to "settings -> repositories". 

And then untick the boxes and also the repo's in the "third party software" tab.

Then reload.

Insert dvd, do the updates".

Then tick the boxes again.

---

### Post by forestpixie on 2008-02-16
> An easier way would be to go to "system -> administration -> synaptic package manager".

Then go to "settings -> repositories". 

which as far as I am aware does this

> you can either use the software sources app in system>admin

:)

Edit - nice sig - twice I've seen that in the last 20 minutes - when I saw it in the blog thing I read I thought that'd work :)

---

