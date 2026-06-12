---
title: "what did i do"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by loserboy on 2006-09-12
not sure what i did but now when i run updates it says this (see screenie)

only thing i knew to do was check my sources list, but it looks normal

---

### Post by halitech on 2006-09-12
I stand to be corrected but I get the same thing but a different program. What I understand is that the official sources may be an older version that what something else has installed so it is being ignored until such time that the sources files are newer then what you have installed.

If I'm wrong, someone please correct me.

---

### Post by confused57 on 2006-09-12
You could try opening Synaptic PM, click on reload, then mark all upgrades, and apply...if apply is not an option, you could do a search(in Synaptic PM) for "checkinstall" and see if there is an updated version to install.

---

### Post by jordanmthomas on 2006-09-12
This error will go away in a few days, chances are.  The reason it can't be installed yet is that it would conflict with current packages.  It gets worked out quickly so you can just ignore it safely.

---

### Post by jordanmthomas on 2006-09-12
Might not be the best time to ask, but what is the application with the stats on your desktop?  I have seen it done with gdesklets and superkaramba, but it doesn't *appear* that that's what you're using.

---

### Post by loserboy on 2006-09-13
well i can upgrade checkinstall, but synaptic says it will remove installwatch if I do.
"Installwatch is used to track the changes made during the installation of
local (i.e. non-deb) software."

so im a lil nervous to do that without someone telling me its ok
> 
what is the application with the stats on your desktop?
thats called conky, [this]("http://www.ubuntuforums.org/showthread.php?t=205865") is the best howto for it that i know of, its a lil hard to setup but really customizable.


haha after looking at my own screenie i just realized how much it looks like a mac, funny ive never owned a mac....maybe my subconsious is telling me something

---

### Post by jordanmthomas on 2006-09-13
I wouldn't bother upgrading right now.  You should be able to soon with no issues.

Are you using 
```
sudo apt-get dist-upgrade
```
?

Sometimes this will work, but don't worry too much if it doesn't.

---

### Post by loserboy on 2006-09-13
```
sudo apt-get dist-upgrade
```

```
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  checkinstall
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

im not really worried about it but i dont think its gonna change cuz its been this way for a few weeks.

---

### Post by jordanmthomas on 2006-09-13
sorry about that...

thanks for the conky link!  now...to get it to not be a solid black box if compiz is running...

---

### Post by loserboy on 2006-09-13
oh lol... search around, i'm pretty sure i saw something about that,

---

### Post by andb on 2006-09-13
Its ok to remove installwatch. Ive done it to use checkinstall, too. No problems. Must be removed to install the other.

---

### Post by loserboy on 2006-09-13
cool thanks i'll try it when i get home from work,  just out of curiosity what needs installwatch?

---

### Post by andb on 2006-09-14
Checkinstall is actually takes advantage of installwatich code, I found out. [http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/) tells more about it.

---

### Post by loserboy on 2006-09-14
lol well that just makes this more confusing....

---

