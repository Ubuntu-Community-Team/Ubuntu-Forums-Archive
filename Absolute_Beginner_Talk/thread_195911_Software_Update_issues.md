---
title: "Software Update issues"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by JDavid5381 on 2006-06-13
I have now switched to Dapper Drake and everything has gone fine accept for when I try to install all available updates I get this message: Cannot install all available updates

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely

The following updates will be skipped:

libopenal0

However, when I do the above suggested tasks, it still does not correct the problem. Does anybody know how to correct this, or this normal at all?  Any help when someone has the time would be much appreciated.

Thanks,
James

---

### Post by uzi09 on 2006-06-13
try:
```

sudo aptitude update
sudo aptitude upgrade -f

```

---

### Post by mlind on 2006-06-13
Does it say that some packages are 'kept back' ?

---

### Post by cormic on 2006-06-19
I am also getting the error message.

The following packages have been kept back:
  libopenal0

---

### Post by MaximB on 2006-06-19
it's like somtimes when you try to install software it says that you cannot install it b/z of a conflict isue
what you need to do is go to advanced mode and get the package from there and it will automaticly remove the "conflict" package (it will tell you what is it going to remove).

---

### Post by Culito on 2006-06-19
My system is doing the same thing, but it's these two packages:

sudo aptitude upgrade -f
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  gnome-cups-manager python-netcdf
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

I can't seem to upgrade those.

---

### Post by cholly on 2006-06-29
same problem with [COLOR="Red"]**libopenal0**[/COLOR]

---

