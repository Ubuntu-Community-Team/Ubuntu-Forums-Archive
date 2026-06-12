---
title: "Very basic questions"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by petef on 2006-01-16
New to Linux\Unix and Ubuntu couple of really dumb questions.

1) How do you input spaces for directories in Terminal ? E.g: Folder in my home directory called My Prictures

2) How can I tell what is installed on my machine ? Should I use synaptic or is their a quicker way through the terminal etc

Thanks in advance

Pete

---

### Post by earobinson on 2006-01-16
1) you can put the dir in quotes (you can do this for any terminal command that needs spaces eg [code]terminalCommand "arg1 with spaces" "arg2 with spaces"

so in your case you want to do a cd "/mount/My Pictures", or whatever.

NOTE: you can also type cd/mount/My<hit tab> and it might auto compleat the dir.

2) Synaptic is the best way I know of to do this. Since anything in the terminal will be very hard to deal with because of a lot of text.

EDIT: anyone else finding the forums a bit slow?

---

### Post by lha on 2006-01-16
[QUOTE=petef]New to Linux\Unix and Ubuntu couple of really dumb questions.

1) How do you input spaces for directories in Terminal ? E.g: Folder in my home directory called My Prictures

2) How can I tell what is installed on my machine ? Should I use synaptic or is their a quicker way through the terminal etc

Thanks in advance

Pete[/QUOTE]

1) Use \ (backslash).
```
cd My\ Documents
```

2) I'm not sure what you mean with "installed on your machine" but ```
dpkg-query --list
``` gives you a list of all packages installed on your system. It's quite a long list, I have ~1100 packages on a couple of weeks old installation and I haven't installed many additional packages yet.

---

### Post by petef on 2006-01-16
Thanks guys very helpful as always 

Pete

---

### Post by tktreload on 2006-01-16
If you like using the terminal you can also check wether a package is installed by using:

aptitude search "package_name or part there of"

if aptitude returns something like:

i     package       blablabla

then the package is installed therefore the i.

c is for conflict, I think. Then you can also get a v for virtual package, a p for package (that are the ones that I'm reasonably sure of)

then you can get an a, and some others that i really don't know...

---

