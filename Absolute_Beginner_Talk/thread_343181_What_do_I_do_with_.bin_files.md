---
title: "What do I do with .bin files?"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by SpoonerV1.3 on 2007-01-21
i want to install limewire in linux but it's in a .bin file format and i have no idea what to do with it....



and how do i use .exe files? im just so damn used to windows =(

---

### Post by Error1312 on 2007-01-21
For .bin files, simply open a terminal and enter:
sh <nameofbinfile>

You can't use .exe files on linux though, but you could try to run them using Wine.

---

### Post by kinematic on 2007-01-21
you'll get all the answers you need if you do a search for "execute bin file".

---

### Post by SpoonerV1.3 on 2007-01-21
thanks...do i need to include a directory or just the name of the .bin file? and do you have any info about .exe files?

---

### Post by ajmorris on 2007-01-21
> **SpoonerV1.3 said:**
> thanks...do i need to include a directory or just the name of the .bin file? and do you have any info about .exe files?

You only need to specify the directory if you are not in the directory with the .bin file. Also if you wish to change the default install directory then you need to specify that too.

2 good sites for .exe files in windows are:
[www.frankscorner.org](www.frankscorner.org)
[www.winehq.org](www.winehq.org)

(but remember support is limited)

---

### Post by Quillz on 2007-01-21
If you use a program such as Automatix, it can automatically install Frostwire for you. (Frostwire is Limewire with a different color scheme.)

---

### Post by ajmorris on 2007-01-21
> **Quillz said:**
> If you use a program such as Automatix, it can automatically install Frostwire for you. (Frostwire is Limewire with a different color scheme.)

it is also in the normal repositories.

---

### Post by SpoonerV1.3 on 2007-01-21
wow thanks guys...this is the fastest i've ever gotten replies on help forums.... im starting to like linux more and more

---

### Post by SpoonerV1.3 on 2007-01-21
i change the directory in the terminal to /tmp (which) is where the .bin file is and i type "sh jre-6-linux-i586.bin" and it says "sh: Can't open jre-6-linux-1586"

---

### Post by pay on 2007-01-21
You probably don't have permision to do that in that folder. Try ```
sudo sh jre-6-linux-i586.bin
```or copy it to your home directory and run sh jre-6-linux-i586.bin

---

### Post by ajmorris on 2007-01-21
if pay's doesn't work try "sh ./jre-6-linux-i586.bin" (i find it needs the ./ with the sh sometimes)

---

### Post by laxmanb on 2007-01-21
well... first make sure that the .bin file is executable (right click it in nautilus, go to permissions and check make sure execute is checked... )

then in nautilus, double click the file and select run in terminal... done!!

that isn't the entire way 2 get Java up and running...

---

### Post by kinson on 2007-01-21
> **SpoonerV1.3 said:**
> wow thanks guys...this is the fastest i've ever gotten replies on help forums.... 

Yeah, this forum kinda spoils you. I'm so used to getting super fast replies here (fatest I got was almost instantaneous), that when I'm on some other forums, I usually get a bit miffed when there are no replies after 12 hours :wink: 

Cheers,
Kinson

---

### Post by xpod on 2007-01-21
> If you use a program such as Automatix, it can automatically install Frostwire for you. (Frostwire is Limewire with a different color scheme.)

You can also just visit the Frostwire site and "click! to download:D 

AX is certainly a great tool for struggling noobs but not for someone  wanting nothing more than FF.
Of course if your looking for a bunch of other handy stuff then go for it:D

---

