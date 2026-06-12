---
title: "installing aMSN"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by boboyo on 2008-01-19
i cant install the new aMSN 

i already have the old one that is in add/remove programs but i cant use it.The letters are too small and i cant makr them bigger. I tryed zoom desktop and i still can see whats written.

can anyone tell me how to install aMSN 0.97?

---

### Post by fatality_uk on 2008-01-19
Here's a direct link to the packages page with 0.97 on it.

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fa%2Famsn%2Famsn_0.97RC1%2Bdfsg-0ubuntu1_i386.deb&md5sum=566c12ac41f3c23b06802021d25bb3e4&arch=i386&type=main]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fa%2Famsn%2Famsn_0.97RC1%2Bdfsg-0ubuntu1_i386.deb&md5sum=566c12ac41f3c23b06802021d25bb3e4&arch=i386&type=main")
Just choose a local server

---

### Post by boboyo on 2008-01-19
it doesnt work
i think its because its not the 64bit thing

---

### Post by fatality_uk on 2008-01-19
Ok. What version of Ubuntu are you running?
Here's a link to the packages page.
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by boboyo on 2008-01-20
i have 7.10 gusty and its 64-bit

i dont know where to find amsn in the packages.

---

### Post by y-lee on 2008-01-20
> The letters are too small and i cant makr them bigger.

I had the same problem, see [Amsn 0.97b - non compiling & antialising fonts]("http://ubuntuforums.org/showthread.php?t=216689").

---

### Post by Ludford on 2008-01-20
I'm trying to install the .deb and it's telling me that libc6 isn't installed although it clearly is in synaptic.

---

### Post by y-lee on 2008-01-20
try adding  libc-dev, I always add the developer packages whenever I have problems like that. Doesn't always work but it can't hurt. :lolflag:

---

### Post by Ludford on 2008-01-20
Got that too :lolflag:

---

### Post by y-lee on 2008-01-20
Hmm what deb are you installing and where did ya get it? From the link above i send ya? 

Could you run "**dpkg --info whatever.deb | grep Depends**" in a terminal.  You  need to change "**whatever.deb**" to the actual name of the .deb file you're trying to install. And post your results here?

I'm new to linux so I might not be able to help. dependency problems are hard for me to figure out. Google helps sometimes and sometimes just confuses me.

---

### Post by bollix47 on 2008-01-20
Try using the script found [here.]("http://ubuntuforums.org/showthread.php?t=297676")

I had the same problem with small fonts and it did fix them for me.

---

### Post by boboyo on 2008-01-20
i cant install it
the thing u sent me is for 32bit ubuntu and i got 64

---

### Post by bollix47 on 2008-01-20
It's unclear if you are addressing my post but I can assure you that the script works fine on 64-bit cause thats what I use.

"This script works on Edgy, Feisty and Gutsy, and works on both 32-bit and 64-bit processors."

---

### Post by boboyo on 2008-01-20
I Cant Install It

---

