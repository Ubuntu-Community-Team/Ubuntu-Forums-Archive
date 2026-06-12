---
title: "Help...with ubuntu rolling into edubuntu"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by geektyme on 2006-08-15
Hello all, I am hoping that I can find some help without having to re-install ubuntu (not that it took me long to install), however really do not want to. 

Anyways what happened is that I have loaded ubuntu and somehow after a update or something it turned into edubuntu and I do not know how or why.

in my boot up screen I have 4 different options for ubuntu and one for WinXP (dual boot), I tryed both of the Ubuntu commands and they both eventually boots up edubuntu not ubuntu.

I am sure there is a quick fix to this however I am what they say "linux ignorant" but I am learning...

Any help would be incredible. Hope to find all my needs here, seems like I have been missing out on a great OS while bashing my head with being a windows user. HAHAHAHA  ](*,)

---

### Post by John.Michael.Kane on 2006-08-15
This should remove edubuntu and it's depenancies.
```
sudo aptitude remove edubuntu-desktop
```

Make sure to reinstall ubuntu-desktop
```
sudo aptitude install ubuntu-desktop
```

---

### Post by geektyme on 2006-08-15
excuse my ignorance, but I am trying...but I am assuming that I need to do this from when I first boot up. What is the process on getting to that point? Thanks again for the help.

---

### Post by John.Michael.Kane on 2006-08-15
You type those commands inside the terminal after you log into your install.

---

