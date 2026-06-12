---
title: "I need some help with ndiswrapper"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Captain CutLess on 2008-02-03
I have a wireless card that is taken care of by the r8169 driver,  However, whenever I install that driver, nothing happens.

What do I do?

---

### Post by bluewraith on 2008-02-03
Can you post the output of
```
ndiswrapper -l
```
thats a lowercase L at the end

---

### Post by Captain CutLess on 2008-02-03
> **bluewraith said:**
> Can you post the output of
```
ndiswrapper -l
```
thats a lowercase L at the end

I would, but the problem is that I get no output after doing that.

---

### Post by bluewraith on 2008-02-03
Do you have the driver for windows? If so, inside the terminal navigate to the directory you have it stored, then type 
```
ndiswrapper -i r8169.inf
```
replace r8169.inf with whatever the filename for your driver is. After that, the driver should be installed.
To check, rerun the code:
```
ndiswraper -l
```
and it should say something along the lines of 
> r8169: driver installed
device (14E4:4320) present 

If it lists an alternate driver, we will have to disable that one or else the two will conflict and not work.

---

### Post by Captain CutLess on 2008-02-03
> **bluewraith said:**
> Do you have the driver for windows? If so, inside the terminal navigate to the directory you have it stored, then type 
```
ndiswrapper -i r8169.inf
```
replace r8169.inf with whatever the filename for your driver is. After that, the driver should be installed.
To check, rerun the code:
```
ndiswraper -l
```
and it should say something along the lines of 


If it lists an alternate driver, we will have to disable that one or else the two will conflict and not work.

Still comes up blank.

---

### Post by bluewraith on 2008-02-03
Hrm.... try this
```
sudo depmod -a
```
It wont put any output out. 
Then, type
```
modprobe ndiswrapper
```
again, there should be no output. If theres an error, please list it.



Edit:
After all that, try the ndiswrapper -l again and see if it lists the driver.
If not.. I'm at a loss and maybe someone else can help out.

---

