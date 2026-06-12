---
title: "Synaptic package manger"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Mekanto on 2007-07-18
It will not work, i get the following error. 
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```
Does anyone understand whats the problem?

---

### Post by Anicka on 2007-07-18
Try (in the terminal) ```
sudo dpkg --configure -a
```

---

### Post by Steven_B on 2007-07-18
Synaptic uses dpkg behind the scenes to actually install the packages.  In your case, dpkg ran into a problem, and needs to be run in a different mode to correct the problem.

I would do what it says - open a terminal and type (or paste in with ctrl-shift-v): ```
sudo dpkg --configure -a
```

---

### Post by Mekanto on 2007-07-18
Yeah, I got this
```
Setting up j2sdk1.4-doc (1.4.2.02-1ubuntu3) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    j2sdk-1_4_2-doc.zip j2sdk-1_4_0-doc-ja.zip j2sdk-1_4_2-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/j2se/1.4.2/download.html

now and download.  The file should be owned by root.root and be copied
to /tmp.

```
So my java has messed it up?

---

### Post by mlentink on 2007-07-18
> **Mekanto said:**
> 
So my java has messed it up?
Did you install it from the repos? If not: I have seen this particular error message pass by a couple of times lately, you might want to search the forum for it

---

### Post by Majorix on 2007-07-18
Are you sure you need Java SDK? Its usually used by Java Developers.. Why did you install it?

---

### Post by Mekanto on 2007-07-18
> **Majorix said:**
> Are you sure you need Java SDK? Its usually used by Java Developers.. Why did you install it?

So i could use some online chatrooms and games

---

