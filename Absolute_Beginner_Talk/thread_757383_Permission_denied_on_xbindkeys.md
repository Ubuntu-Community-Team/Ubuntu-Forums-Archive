---
title: "Permission denied on xbindkeys"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Lolicon on 2008-04-16
When I try to run a command on xbindkeys-config, It gives me a permission denied. The output in terminal is:
```
sh: /home/w/foobar2000/foobar2000.exe: Permission denied

```
I have wine installed, and it runs fine, except I'm trying to make it work with global hotkeys.

---

### Post by Dark Aspect on 2008-04-16
> **Lolicon said:**
> When I try to run a command on xbindkeys-config, It gives me a permission denied. The output in terminal is:
```
sh: /home/w/foobar2000/foobar2000.exe: Permission denied

```
I have wine installed, and it runs fine, except I'm trying to make it work with global hotkeys.

I don't think you can run exe files as a script,I think you have to use wine.

---

### Post by Lolicon on 2008-04-16
How would I do that? do I add a wine in front of the home to make it:
```
sh: wine /home/w/foobar2000/foobar2000.exe: Permission denied
```

---

### Post by Lolicon on 2008-04-16
Now I get a 
> wine: /home/w/.wine is not owned by you
Even though I set the permissions correctly.

---

### Post by Dark Aspect on 2008-04-16
> **Lolicon said:**
> How would I do that? do I add a wine in front of the home to make it:
```
sh: wine /home/w/foobar2000/foobar2000.exe: Permission denied
```

Yes actually you would use wine that way.Odd the file is in your home folder and I don't think its a good idea to run wine as a root.Make sure you have the right permission to execute the file by right clicking on the file and going to properties.Then go to Permissions and check the allow executing the file as a progarm.

---

### Post by Dark Aspect on 2008-04-16
> **Lolicon said:**
> Now I get a 

Even though I set the permissions correctly.


Ok I think you need to change the group or owner,I'll edit this post for a solution in a minute.I can't remember the command line.

EDIT:

Okay try this:

> Chown w /home/w/.wine

That will change the owner.

---

### Post by Lolicon on 2008-04-16
Its in lowercase, and the command worked, except for some reason the output is still the same, I'm not the owner, even though in the GUI I clearly am.

---

### Post by Lolicon on 2008-04-19
Any help on this please?

---

