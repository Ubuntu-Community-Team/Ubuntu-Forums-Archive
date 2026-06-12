---
title: "Downloading apt-get as deb?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by SurR3AL on 2007-04-26
here's the deal....i just upgraded to feisty, and one of my friends wants to do the same :). but he doesnt have an internet connection on his computer. so i was going to use ["AptOnCD"]("aptoncd.sourceforge.net/") to burn a cd with all the required stuff and ubuntu restricted packages and everything....

but just now i did a "sudo apt-get clean" without realising that erases the apt cache of installation files....i dont mind downloading everything again....but how? is it possible to download only the .deb files from apt-get?

Thanks....

---

### Post by Bachstelze on 2007-04-26
Yes, there is a switch you can pass to apt-get to tell it to just download the packages, not install them. I don't remember what it is but I know it exists, the man page will tell you.

---

### Post by justleen on 2007-04-26
i think even just a apt-get without option (this gives the help) will tell you how to.

---

### Post by justleen on 2007-04-26
-d or --download-only 
```
 apt-get -d install package 
```

---

### Post by SurR3AL on 2007-04-26
there's still a problem....all those packages i cleared, i have them installed on my computer....so for example, when i try "sudo apt-get -d install ubuntu-restricted-extras", it gives this output : > Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by justleen on 2007-04-26
try adding --reinstall  
```
  apt-get -d --reinstall install package 
```

it will try to reinstall, but the -d will cause it to only download..

---

### Post by SurR3AL on 2007-04-26
> **justleen said:**
> try adding --reinstall  
```
  apt-get -d --reinstall install package 
```

it will try to reinstall, but the -d will cause it to only download..

that worked PERFECTLY!!! thank you so much.... :)

---

### Post by dreadlord_chris on 2007-04-26
> **SurR3AL said:**
> there's still a problem....all those packages i cleared, i have them installed on my computer....so for example, when i try "sudo apt-get -d install ubuntu-restricted-extras", it gives this output :

if you just wanted to download the packages just use the **-d** option without the *install or reinstall* option.

---

### Post by SurR3AL on 2007-04-27
> **dreadlord_chris said:**
> if you just wanted to download the packages just use the **-d** option without the *install or reinstall* option.
 that doesnt work....it still needs a switch like install or upgrade or update or whatever

---

