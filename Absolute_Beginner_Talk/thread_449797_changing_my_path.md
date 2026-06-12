---
title: "changing my path"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by michael_besselman on 2007-05-20
This should be easy, but I can not seem to find where with path is set in Feisty.  I want to add the local directory to the path, but which file do I need to do this in?

Thanks

---

### Post by taurus on 2007-05-20
You can do that in ~/.bashrc.

```
gedit ~/.bashrc
```
Then, add these two lines.

```
PATH=$PATH:/to_new_path
export PATH
```
Save the changes and either log out and back in again or rehash your bash again with

```
source ~/.bashrc
```

---

### Post by PhilJ on 2007-05-20
I used the following from another thread  (I cant remenber where it was) in my .bashrc to add /home/phil/bin

PATH=.:/to_new_path:"${PATH}"

Philj

---

