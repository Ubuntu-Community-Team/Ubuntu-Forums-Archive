---
title: "Gutsy Gripe"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-10-18
I like to use Epiphany, it works fine on Feisty, Gutsy says web browser can not be installed on your 

computer type i386. What's the deal?:)

---

### Post by Dr Small on 2007-10-18
Assuming that you are running 64Bit ?

---

### Post by rosswmcgee on 2007-10-18
How do I check that? All I know is it worked fine on Feisty.

---

### Post by rosswmcgee on 2007-10-18
Now I see the same thing with Digikam, what do I need Gutsy for if it won't do the things Feisty does?  Must I go back  to Feisty?:(

---

### Post by rosswmcgee on 2007-10-18
When I boot up it says 64 in the left corner.

---

### Post by RomeReactor on 2007-10-18
Hi. Did you download Epiphany and Digikam from their website, or tried to install from the repositories?

To find out whether you're running Ubuntu 32 or 64 bit, run this in the terminal:
```
uname -m
```
If the result is **x86_64**, then your system is 64 bits. Also please post the output of this:
```
cat /etc/apt/sources.list
```

---

### Post by rosswmcgee on 2007-10-18
from the repositories

---

### Post by rosswmcgee on 2007-10-18
it says i686

---

### Post by RomeReactor on 2007-10-18
Then you're running 32-bit Ubuntu. Do you have any extra repositories that you added to your sources.list?

---

### Post by rosswmcgee on 2007-10-18
No I have added nothing other than what came with Gutsy

---

### Post by RomeReactor on 2007-10-18
Open Syanptic, go to "Settings->Repositories" and on the first tab make sure all the boxes are checked. Close that window, press the blue "Reload" button, and try installing Epiphany again.

This is really odd.

---

### Post by rosswmcgee on 2007-10-19
Roger last transmission, mission accomplished/and thank you so much. Ross

---

