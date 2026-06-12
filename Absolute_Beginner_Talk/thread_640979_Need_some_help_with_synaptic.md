---
title: "Need some help with synaptic"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by pcgame612394 on 2007-12-14
Whenever i go to synaptic it says this E: Type 'wget' is not known on line 67 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Please Help

---

### Post by diatribe on 2007-12-14
Whenever i go to synaptic it says this E: Type 'wget' is not known on line 67 in source list /etc/apt/sources.list

this tells you exactly what your problem is, on line 67 of your sources.list you have an invalid instance of wget.  fix it.

---

### Post by taurus on 2007-12-14
There is something wrong with line 67 of your /etc/apt/sources.list.

Edit it

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of line 67 to comment it out.  Then, save it and run

```
sudo apt-get update
sudo apt-get upgrade
```
Otherwise, post your /etc/apt/sources.list here then.

```
cat /etc/apt/sources.list
```

---

### Post by wormser on 2007-12-14
There is something wrong with /etc/apt/sources.list file on line 67.  

```
sudo gedit /etc/apt/sources.list
```

Remove the line that starts with wget, it should be on line 67. Save it.

```
sudo apt-get update
```

Now try again.  If you are still having issues post your /etc/apt/sources.list file.

---

