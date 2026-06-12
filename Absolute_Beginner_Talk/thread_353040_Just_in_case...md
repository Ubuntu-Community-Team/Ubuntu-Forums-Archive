---
title: "Just in case.."
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by ubunick on 2007-02-04
Since I have been have issues with Edgy (after installed, won't boot) I have installed Dapper again.  I was wondering if you can actually upgrade to Edgy through the software updates? I don't want to do that right now but I'm not sure which file not to update.

---

### Post by sardion on 2007-02-04
You can, yes.  You just need to change your sources to point to edgy instead of dapper.

So either:

gksudo gedit /etc/apt/sources.list

and make every instance of "dapper" into "edgy"

or do the equivalent in synaptic or update-manager.

---

### Post by ubunick on 2007-02-04
So I don't need to worry about accidentally updating when I don't want to?

---

### Post by sardion on 2007-02-04
You won't update from dapper to edgy unless you do what I said above.  So long as your sources.list files says "dapper" all thru it, you'll be using dapper.

---

### Post by jvc26 on 2007-02-04
You cannot upgrade the entire OS without telling it to. The updates you will get will be for dapper (unless you change the repos) and hence you will just update your dapper system.
Il

---

