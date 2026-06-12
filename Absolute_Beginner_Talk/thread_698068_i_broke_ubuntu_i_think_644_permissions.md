---
title: "i broke ubuntu i think???? 644 permissions?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by FREEMAN43228 on 2008-02-15
[B]says on start up
"user $ home/.dmrc file is being ignored"

and that something about 


file should be owned by user and have 644 permissions"


what the hack do i do to fix this???

if does it on start up after i enter my user name and password???[/B]

help ! ! !

---

### Post by PeterJS on 2008-02-15
What permissions does the file currently have?

The error message describes two requirements, being owned by your user, which can be set with:
```

sudo chown *username*:*username*

```
The second requirement is that it has permissions 644, which  can be set with
```

chmod 644 ~/.dmrc

```

---

### Post by emarkd on 2008-02-15
In the terminal, run:

```
ls -al | grep dmrc
```

and see if it shows

 rw-r--r--  yourusername

If the first part is wrong, run

```
 chmod 644 .dmrc
```

If the username is wrong, run

[CODE]chown yourusername .dmrc

---

### Post by kenora_kid02 on 2008-03-15
Worked like a charm, thanks!

---

