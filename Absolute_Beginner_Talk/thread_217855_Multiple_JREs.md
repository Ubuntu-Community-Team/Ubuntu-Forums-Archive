---
title: "Multiple JREs?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by kash4u on 2006-07-17
I want to install GanttProject 2.0.1. I have been told I need Sun's JRE installed rather than the one installed by default (gcj i believe). I don't want multiple jre's installed for different software - it feels wrong.  Therefore, my question is can I uninstall gcj and its various bits (eg gcc4.0 base and so on) and install sun's jre without detriment to existing programs?

Thanks.

---

### Post by woedend on 2006-07-17
gcc4.0 isnt java...i wouldnt remove it :p.  Honestly why not just install sun's jre and use it but leave the rest alone?

---

### Post by Jagot on 2006-07-17
I agree with woedend.  You can select the Sun's JRE so the others will not be used:

```
sudo update-alternatives --config java
```

---

### Post by kash4u on 2006-07-17
Well I installed Sun's JRE as you guys suggested. Ran:

*sudo sh ganttproject.sh*

and got:
[I]
ganttproject.sh: line 5: cd: ganttproject.sh: Not a directory[/I]

What does this mean?

---

### Post by Ragazzo on 2006-07-17
> **kash4u said:**
> Well I installed Sun's JRE as you guys suggested. Ran:

*sudo sh ganttproject.sh*

and got:
[I]
ganttproject.sh: line 5: cd: ganttproject.sh: Not a directory[/I]

What does this mean?

Try this instead:

```

sudo chmod +x ganttproject.sh
sudo ./ganttproject.sh

```

---

### Post by kash4u on 2006-07-18
Well I tried that too and other than asking for the password I got no visible response at all - it just returned me to the command prompt. So how do I install this piece of software? With windows there were MSI installers. With linux there are several different ways to install - each with their own problems - this is really frustrating.

---

