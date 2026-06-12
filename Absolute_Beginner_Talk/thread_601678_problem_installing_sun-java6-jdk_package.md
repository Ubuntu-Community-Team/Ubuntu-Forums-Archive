---
title: "problem installing sun-java6-jdk package"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by badperson on 2007-11-03
Hi,

I'm new to ubuntu, just installed 7.10 on one of my old machines (thisis a different machine than I was describing in another post)

I was trying to install the jdk on my machine. 

I typed sudo apt-get update. 
that was fine. 

I typed sudo apt-get install sun-java6-jdk

that went fine until the console turned into this screen explaining the software license, but I didn't know where to go from there...I didn't see an option to accespt, it was like opening a file in a dos prompt, I didn't know what to do other than close the file. 

tried to compile a test java file...didn't work, said the package wasn't installed. 
so, I tried to do it over again, but it said the install was interrupted and I would need to run dpkg --configure -a. 

I tried that, but it said I needed super-user priveleges. 

any idea how to work through this? Didn't see an explanation in the docs. 
thanks, 
bp

---

### Post by PmDematagoda on 2007-11-03
When you reach the part of the license agreement, just go down to the end of it using the Enter button, once you reach the end, just type yes and press enter.

---

### Post by PmDematagoda on 2007-11-03
Since you need to be sudo to fix the problem simply append the command by putting sudo in front of the command, enter the password and there you are, for example your command would go like this:-

```
**sudo** dpkg --configure -a
```

When you enter the password in the terminal you won't see a thing, this is normal, just keep typing normally and after the password is typed, just press enter.

---

### Post by badperson on 2007-11-03
> **PmDematagoda said:**
> When you reach the part of the license agreement, just go down to the end of it using the Enter button, once you reach the end, just type yes and press enter.


Hi,

the enter key doesn't do anything; I can page down to the bottom of the file, but I can't get the cursor anywhere so I can add text. Is that a preference in the Terminal I need to change? 
bp

(btw, I got the part about adding  "sudo" before the dpkg comnand, thanks)

---

### Post by schorsch on 2007-11-03
Press "TAB" to navigate to the accept button.

---

### Post by PmDematagoda on 2007-11-04
Once you reach the end of the license agreement you should be able to just type "yes" and then go on with the installation process.

---

