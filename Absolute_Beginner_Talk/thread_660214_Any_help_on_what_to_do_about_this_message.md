---
title: "Any help on what to do about this message"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by tjpearson on 2008-01-06
I'm having a bad day today, if it can go wrong or not work then that has happened all day to me.

Does anyone now what the hell this message means and what to do to fix things, thanks.

---

### Post by wheredidrealitygo on 2008-01-06
it means a package failed to install properly, messed up, and you need to run```
sudo dpkg --configure-a
``` in a terminal to fix it. It will ask you for a LOT of answers to questions, but it should fix your problem.

---

### Post by taurus on 2008-01-06
If you want to take a screenshot next time, increase the time delay to 1 or 2 seconds so the screenshot window won't be in the way.  

Regarding your problem, close synaptic window first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by tjpearson on 2008-01-06
Sorry,  screen shot again

---

### Post by philinux on 2008-01-06
Can just about see through the image.

In a terminal copy the command its telling you to run and run it.

---

### Post by tjpearson on 2008-01-06
Thanks so much, really appreciate the help.

---

### Post by tjpearson on 2008-01-06
I'm now getting 

'requested operation requires superuser privilege'

and still no fix.

---

### Post by rodo-&gt;dave on 2008-01-06
you probably just need to put 'sudo' before the command:

$ sudo dpkg...

---

### Post by wheredidrealitygo on 2008-01-06
You need to do sudo before it, as I mentioned above.

```
sudo dpkg --configure-a
```

---

### Post by taurus on 2008-01-06
> **wheredidrealitygo said:**
> You need to do sudo before it, as I mentioned above.

```
sudo dpkg --configure-a
```

You need to add a space between **--configure** and **-a**.

```
sudo dpkg --configure -a
```

---

### Post by tjpearson on 2008-01-06
Thanks, I've sorted it.

Using this fantastic creation but not thinking it yet, I'm sure that will come in time, anyway it's fixed itself.

I'm not being corny but I think you are all fantastic the way you help, thanks again to all that replied.

This forum is so needed and people like you, how you know all this stuff is beyond me !!

:)

---

### Post by philinux on 2008-01-06
> **tjpearson said:**
> Thanks, I've sorted it.

Using this fantastic creation but not thinking it yet, I'm sure that will come in time, anyway it's fixed itself.

I'm not being corny but I think you are all fantastic the way you help, thanks again to all that replied.

This forum is so needed and people like you, how you know all this stuff is beyond me !!

:)

From being in the same jam as you. :lolflag: and folks on here in the know.

How it started - chicken and egg comes to mind.

---

