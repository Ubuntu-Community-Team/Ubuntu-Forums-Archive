---
title: "Where is the &quot;Typing break&quot; applet in Cinnamon? I loved using it while on MATE"
date: 2012-10-11
forum: Any Other OS
---

### Post by pepperminty on 2012-10-11
Hello, 

I switched from Mint 13 MATE to Mint 13 Cinnamon. In MATE, I have appreciated using the Typing Break applet found in the Keyboard settings. The Typing Break applet locked me out of my screen every hour, encouraging me to stand up and give the wrists and the eyeballs a break. Yet where is the program (or a similar program) in Mint 13 Cinnamon?

Please help. 

Thanks.

---

### Post by pepperminty on 2012-10-16
bump.

---

### Post by AllRadioisDead on 2012-10-16
Maybe you should post this on the Linux Mint forums.

---

### Post by pepperminty on 2012-10-16
AllRadioisDead,
I have posted this on the Linux Mint forums. But I have not gotten any response, so I thought I'd post in a forum with a bigger community.

---

### Post by BigSilly on 2012-10-16
That's fair enough, but the reality is no-one here is going to have the answers to this. You'll really be better off persisting with the Mint forums.

---

### Post by pepperminty on 2012-10-16
BigSilly,

Thanks. I'm so tempted to return to Ubuntu, my first Linux distro, given Ubuntu's huge community.

---

### Post by westie457 on 2012-10-16
In Ubuntu 'typing break' is called xwrit, it might be the same in Mint.

---

### Post by pepperminty on 2012-10-16
westie457,
Thanks for your post.
 ```
xwrit
```
> No command 'xwrit' found, did you mean:
 Command 'xwit' from package 'xwit' (universe)
 Command 'xwrits' from package 'xwrits' (universe)
xwrit: command not found

 I installed xwrits (with an S at the end) 
```
sudo apt-get install xwrits
```
> Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe xwrits amd64 2.21-6.1 [97.7 kB]


I then ran
```
xwrits
```
but nothing happened.

---

### Post by jrog on 2012-10-16
> **pepperminty said:**
> westie457,
Thanks for your post.
 ```
xwrit
```N
 I installed xwrits (with an S at the end) 
```
sudo apt-get install xwrits
```
I then ran
```
xwrits
```but nothing happened.
xwrits (with an 's') is the right package. See:
```
apt-cache show xwrits
```
> Package: xwrits

. . . 

Description-en: reminds you to take a break from typing
 xwrits helps you prevent repetitive stress injury.
 .
 xwrits is a small reminder program designed to let you know it is time
 to take a break from typing to rest your wrists and prevent any damage
 to your wrists (or at least make them feel better if you've already
 damaged them). Normally works on the honor system, but if you find
 yourself unable to stop typing during your break, it can also lock your
 keyboard.

I've never used it before, though, so I have no idea how it works, and thus no idea whether anything should happen when you invoke it from the command line.

---

### Post by pepperminty on 2012-10-16
jrog,
thanks for confirming that xwrits (with the S) is the right package. I don't usually start a program from the command line, but I searched my Mint Menu for it. I tried "typing", "xrwr..", "keyboa...", but nothing showed up.

---

### Post by westie457 on 2012-10-16
Sorry about the typo - speed typing is not for me.

See ```
man xwrits
```for more information

---

