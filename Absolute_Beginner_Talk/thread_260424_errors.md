---
title: "errors"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2006-09-18
i get this everytime i try to run automatix,kwrite and a couple of other programs 

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

any ideas??/

---

### Post by Najand on 2006-09-18
Sorry, bud... But this is not a forum for 
Automatix... Please use their own forum to
solve your problem.

---

### Post by arnieboy on 2006-09-18
this post has the solution:
[http://ubuntuforums.org/showpost.php?p=1264009&postcount=3](http://ubuntuforums.org/showpost.php?p=1264009&postcount=3)
The issue is not even vaguely AX related.

---

### Post by tagra123 on 2006-09-18
> **Najand said:**
> Sorry, bud... But this is not a forum for 
Automatix... Please use their own forum to
solve your problem.

Hey, help if you can....

---

### Post by arnieboy on 2006-09-18
> **tagra123 said:**
> Hey, help if you can....
I agree.. Being totally uninformed about an issue before replying to it and calling it an Automatix issue (just because the word Automatix was mentioned in the first post) can be a little annoying at times.
Atleast give the link to our forum ( [http://www.getautomatix.com/forum](http://www.getautomatix.com/forum) ).
I have seen this poster (Najand) do it multiple times with the same message everytime.

---

### Post by swp6499 on 2006-09-18
thanks guys that fixed it...another thing is everytime i reboot adept pops up and asks me to run as root and the starts???

---

### Post by arnieboy on 2006-09-18
> **swp6499 said:**
> thanks guys that fixed it...another thing is everytime i reboot adept pops up and asks me to run as root and the starts???

Its probably added to KDE session Autostart. I very strongly recommend that folks not use Adept (I would also suggest that you remove it). 
Install synaptic (though its gtk based) and use it instead.
```
sudo apt-get remove adept
sudo apt-get install synaptic
```

---

### Post by swp6499 on 2006-09-18
is it harder to find stuff for kde using synaptic...i have used synaptic in ubuntu but never really looke for anything kde except k3b...??

---

