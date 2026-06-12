---
title: "chmod query"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by niteblind on 2007-01-31
Hi All.

Is it possible to change the permissions of a folder to 777 so that all the subfolders change to that as well or do you have to do it to each individual folder?

niteblind

---

### Post by K.Mandla on 2007-01-31
I believe 

```
sudo chmod -R 777 folder-name
```
might do it. Someone correct me if I'm wrong.

---

### Post by bodhi.zazen on 2007-01-31
> **K.Mandla said:**
> Someone correct me if I'm wrong.

Alas, I can only confirm that this is correct.


niteblind: Be careful what folder we are talking about :)

I would advise against this command with /home/your_login_name and system folders such as /etc

---

### Post by niteblind on 2007-01-31
dont worry it is not anything like that. dont suppose u know how to make an application the default one for KDE at all?

niteblind

---

