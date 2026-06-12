---
title: "Ppoe/dsl"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by nycajulio on 2006-03-29
:confused: I am having trouble setting up my DSL connection with Ubuntu 5.10. 

I have typed in a terminal sudo ppoeconf and the terminal states command not found.

I ran dpkg -s ppoeconf and it states ppoe not installed. No further information is available. 

Lastle I ran Synaptic Package Manager twice and it appears that it installed ppoeconf but when I check to see if it was installed, I receive the same message in the terminal that states ppoeconf not found.

Could use some suggestions. I am not a Linux or programming expert. Thank you all for the help.

---

### Post by meborc on 2006-03-29
try **pppoeconf **(with 3 p's) :mrgreen:

---

### Post by nycajulio on 2006-03-29
THANK YOU!!!:D :D 

I knew I should have read the instructions a little more (D'OH!). One last question. Do I have to type in pon dsl-provider evertime I boot into Ubuntu and if so, how do I turn off my connection when I am finished? Thank you.

---

### Post by StefanoCole on 2006-03-30
To turn off the connection type: ```
poff dsl-provider
```

> Do I have to type in pon dsl-provider evertime I boot into Ubuntu 

When you run "sudo pppoeconf" you are asked if you want to start the connection at boot time. If you answer yes then you do not need to type in pon dsl-provider everytime. Otherwise you have to manually connect.

Stefano

---

