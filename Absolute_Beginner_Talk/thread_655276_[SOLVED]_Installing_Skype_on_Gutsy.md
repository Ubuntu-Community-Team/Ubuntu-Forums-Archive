---
title: "[SOLVED] Installing Skype on Gutsy"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by unclejac on 2008-01-01
Hi Guys, need a little help here. Trying to install Skype. 

Found some steps on another thread here: [[COLOR="Sienna"]Best way of installing Skype?[/COLOR]]("http://ubuntuforums.org/showthread.php?t=345490")

I followed the code as described by [**hyper_ch**]("http://ubuntuforums.org/member.php?u=122588")

Though I think this line is no longer relevant:


deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

as I get this after I do the update:

Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 194.192.199.201 80]

Any ideas ? :-k

---

### Post by por100pre1 on 2008-01-01
Please add the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu") and then copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo apt-get install skype
```

---

### Post by unclejac on 2008-01-01
Many Thanks por100pre1!!!

Worked a treat \\:D/

Medibuntu repository looks quite usefull. . .

---

