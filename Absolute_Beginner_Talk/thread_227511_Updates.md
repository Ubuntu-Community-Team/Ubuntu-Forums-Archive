---
title: "Updates"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by navymom on 2006-08-01
When I get a list of available updates, are these lists all pertaining to my system version or is it a list of all avail updates for all versions?  In other words, does it check to see if they are relevant updates for my system?

---

### Post by mlind on 2006-08-01
> **navymom said:**
> When I get a list of available updates, are these lists all pertaining to my system version or is it a list of all avail updates for all versions?  In other words, does it check to see if they are relevant updates for my system?

Depends what you're using to check the updates. APT tools like aptitude, apt-get and synaptic include only packages for distribution you've defined on /etc/apt/sources.list.

---

### Post by navymom on 2006-08-01
> **mlind said:**
> Depends what you're using to check the updates. APT tools like aptitude, apt-get and synaptic include only packages for distribution you've defined on /etc/apt/sources.list.

i'm not really using anything.  a little icon is at the top of my desktop telling me that updates are available.

---

### Post by mlind on 2006-08-01
> **navymom said:**
> i'm not really using anything.  a little icon is at the top of my desktop telling me that updates are available.

It's update-manager. update-manager checks available updates only for your distribution (Dapper , Breezy, etc.)

---

### Post by navymom on 2006-08-01
lol k thanks....still new to this so i don't really know what everything is called yet.  until i do, most things are dubbed "thingie". lol

---

### Post by navymom on 2006-08-02
Another question about updates....

When downloading/installing updates, should I get booted offline before they finish, will it redownload all the files or pick up where it left off?

---

### Post by eXisor on 2006-08-02
It'll pick up where you left off unless the cached version is newer in the repositories.

---

### Post by Otto-C on 2006-08-02
Be alert to what you are updating. In particular your
networking (Ndiswrapper and others) may break them.
Still trying to get Ndiswrapper working again.

---

