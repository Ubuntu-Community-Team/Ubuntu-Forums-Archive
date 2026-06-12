---
title: "[SOLVED] xubuntu how to take screenshot ?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by arai on 2007-09-17
it was easy to take screenshot in ubuntu because of a separate menu there. How to take screenshots in Xubuntu ?

---

### Post by arai on 2007-09-17
Used Gimp image editor

file >> acquire >> screenshot 

it worked.

---

### Post by raul_ on 2007-09-17
There's also a panel applet. doesn't the print screen button work?

---

### Post by arai on 2007-09-17
print screen didn't work for me (xubuntu)

---

### Post by capsid on 2008-05-19
I'd really like a way to use the print_screen button, but I'm not sure how to do it.  I don't mind opening gimp for now, but that seems a bit heavyweight when all you want is a quick screen or window cap to go right to your home (or Pictures) folder.  

As always, I appreciate any suggestions you can offer!

---

### Post by 00l0 on 2008-06-02
> **capsid said:**
> I'd really like a way to use the print_screen button, but I'm not sure how to do it.  I don't mind opening gimp for now, but that seems a bit heavyweight when all you want is a quick screen or window cap to go right to your home (or Pictures) folder.  

As always, I appreciate any suggestions you can offer!

hello there
my suggestion:
 
__first of all install 'scrot' package, which is a command line screen capture utility 
$sudo aptitude install scrot

__make some dir where you want to store the screenshots as a default option
e.g.  
$ mkdir ~/captures

__in XFCE, system settings > keyboard > shortcuts
Add new shortcut;
command: scrot -e 'mv $f ~/captures'
key:  Print button

that's all :]

check the man page, 'man scrot', so you find the options that suit your needs such as countdown or picture quality

---

### Post by Unix_Slayer on 2008-06-02
> **00l0 said:**
> hello there
my suggestion:
 
__first of all install 'scrot' package, which is a command line screen capture utility 
$sudo aptitude install scrot

__make some dir where you want to store the screenshots as a default option
e.g.  
$ mkdir ~/captures

__in XFCE, system settings > keyboard > shortcuts
Add new shortcut;
command: scrot -e 'mv $f ~/captures'
key:  Print button

that's all :]



check the man page, 'man scrot', so you find the options that suit your needs such as countdown or picture quality


[B]Doesn't alt+print do the same thing?
[/B]

---

### Post by 00l0 on 2008-06-03
> **Unix_Slayer said:**
> [B]Doesn't alt+print do the same thing?
[/B]

hey not in my case, running XFCE
i gave it a try anyway D:

---

### Post by Unix_Slayer on 2008-06-03
> **00l0 said:**
> hey not in my case, running XFCE
i gave it a try anyway D:

Ahhhh... I see.....

---

