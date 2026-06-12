---
title: "How do i install the tahoma font to make staem work?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-07-07
I need a simple explanation that is up to date.

---

### Post by ~~Tito~~ on 2007-07-07
please help me. I need a simple explanation that can install the font. The last one i did didnt work. I have the cabextract files it made. Its in my desktop.

---

### Post by Vague on 2007-07-07
OK, I'll give it another go.  Open up terminal and type ```
sudo apt-get install msttcorefonts
```  Then, the easiest way to get Tahoma is either to use google to find a place where you can download tahoma.ttf, or grab it off a Windows partition.  Can't really help you there, but there are plenty of places to get it.  Put the font file on your desktop, open a terminal and type ```
sudo cp ~/Desktop/tahoma.ttf /usr/share/fonts/truetype/msttcorefonts
```  That should be it.  If that doesn't work, you might also need to do ```
sudo cp ~/Desktop/tahoma.ttf ~/.wine/drive_c/windows/fonts/
```  But I think you'll be set just doing the first one.

---

### Post by atria on 2007-07-07
Unfortunately, tahoma is not included in msttcorefonts by default. 

Try not to copy the tahoma font that you downloaded into /usr/share/fonts/truetype/msttcorefonts as it is not included in the msttcorefonts package and will only "dirty" the apt installation.

Perhaps create a custom directory inside /usr/share/fonts

Also the fonts will not be initialized by default. You have to execute
```
sudo fc-cache -f -v
```

---

### Post by Vague on 2007-07-07
> **atria said:**
> Try not to copy the tahoma font that you downloaded into /usr/share/fonts/truetype/msttcorefonts as it is not included in the msttcorefonts package and will only "dirty" the apt installation.

Really?  I haven't really heard of anyone having a problem doing it that way.  At any rate, just copying it to ~/.wine/drive_c/windows/fonts/ should work fine, assuming you'll only need it for Steam.

---

### Post by ~~Tito~~ on 2007-07-07
thanks so much i have them now i am about to run steam. (I did this before you guys posted i forgot to install the mscorefonts package to make the drive so it can move the .tff in there. Tanks for the help you guys im such and idiot!!

UBUNTU RULES!!

---

### Post by Vague on 2007-07-07
> **~~Tito~~ said:**
> I did this before you guys posted i forgot to install the mscorefonts package to make the drive so it can move the .tff in there.

It's really not essential in this case, since it doesn't contain Tahoma, but it's nice to have with Wine.

---

### Post by atria on 2007-07-07
[quote=Vague]Really? I haven't really heard of anyone having a problem doing it that way. At any rate, just copying it to ~/.wine/drive_c/windows/fonts/ should work fine, assuming you'll only need it for Steam.[/quote]

You won't have a problem actually, its just that things are going to be neater. Future manual uninstallations of those fonts are going to be far easier too ;)

Tito:
Glad it worked for you! Have fun with Ubuntu

---

### Post by ~~Tito~~ on 2007-07-07
Now for IE6!!!
and how do i completely remove the cadega prog from ubuntu? I dont want it anymore.

---

### Post by atria on 2007-07-07
How did you install cedega? Through a package or through CVS?

Whatever your reasons are, good luck with IE6 : x
 It takes some effort to set it up from scratch.

---

### Post by Vague on 2007-07-07
> **atria said:**
> You won't have a problem actually, its just that things are going to be neater. Future manual uninstallations of those fonts are going to be far easier too ;)

Ahhh, fair enough.  That makes sense.

---

