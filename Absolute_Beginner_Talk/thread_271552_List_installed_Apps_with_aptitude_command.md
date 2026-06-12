---
title: "List installed Apps with aptitude command"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by andiii on 2006-10-04
There is a command to list the installed programs or packages, I did use that a while ago to produce a textfile with all my programs listed. The output looked like this:

```

# head installed17sept.txt 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                   Version                                 Description
+++-======================================-=======================================-================================================
ii  915resolution                          0.5-1ubuntu6                            resolution modify tool for Intel graphic chipset
ii  abiword                                2.4.4-0ubuntu5                          WYSIWYG word processor based on GTK2


```

Now I don't remember this command.

---

### Post by jordanmthomas on 2006-10-04
was it 
```
dpkg --list
```
perhaps?

---

### Post by andiii on 2006-10-04
Ah ok, that was the command I was looking for. Thanks :)

---

