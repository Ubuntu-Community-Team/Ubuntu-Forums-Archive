---
title: "cant update repositories"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2006-09-10
Just that when I click on repositories, it crashes and I cant add to them , is the site being uodated?

when I try apt-get , I get cant find package

Any ideas??
Stephen

---

### Post by lukew on 2006-09-11
I think you need to be a bit more descriptive in your words.

The "clicking on repositories" is this in symaptec package manager? Does any error message ocur? what is in dmesg |tail .

When you apt-get ... could you provide you complete command. It sounds like the package you are trying to install can not be found. 

Luke

---

### Post by Najand on 2006-09-11
The easiest way to update the repositories is to use the command
```
$ sudo apt-get update
```
And the easiest way to upgrade them is;
```
$ sudo apt-get upgrade
```
To add repositories try to edit /etc/apt/sources.list in gedit or vim like:
```
$ sudo gedit /etc/apt/sources.list
```
and update and upgrade your system...


To install packages by using apt-get use:
```
$ sudo apt-get install <PACKAGE NAME>
```
OR by aptitude:
```
$ sudo aptitude install <PACKAGE NAME>
```

To search installable packages use:
```
$ sudo aptitude search <SEARCH WORD>
```

---

