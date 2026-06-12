---
title: "at login screen but graphics is bad how do i fix it?"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by dq101 on 2006-07-08
how do i fix it, my graphics are really bad i cannot see anything?

---

### Post by Bossieman on 2006-07-08
You have to describe the problem more. Give as much info you can if you want help. Its hard to help when the problem is unclear.

---

### Post by Sonofmoog on 2006-07-08
Ctrl-Alt-F6 to get to a command line.  Login.  Run

```
sudo dpkg-reconfigure xserver.xorg
```

Answer the questions.  You should have your manuals for both your monitor and your graphics card handy.  

Ctrl-Alt-F7 to return to your graphical login screen.  Ctrl-Alt-Backspace to kill X.  If everything goes as you hope, the graphical login screen will come back, will be visible and in the correct resolution.

HTH

---

### Post by dq101 on 2006-07-08
Here is all the info about my pc and monitor:

 15inch screen is a P2 with 512mb of ram!

---

### Post by Bossieman on 2006-07-08
Did you try the solution presented by Sonofmoog?

---

### Post by confused57 on 2006-07-08
> **Sonofmoog said:**
> Ctrl-Alt-F6 to get to a command line.  Login.  Run

```
sudo dpkg-reconfigure xserver.xorg
```

Answer the questions.  You should have your manuals for both your monitor and your graphics card handy.  

Ctrl-Alt-F7 to return to your graphical login screen.  Ctrl-Alt-Backspace to kill X.  If everything goes as you hope, the graphical login screen will come back, will be visible and in the correct resolution.

HTH

Excellent instructions, but mis-typed:
```
sudo dpkg-reconfigure xserver-xorg
```

I do it all the time, thought I'd point it out.

---

### Post by Sonofmoog on 2006-07-08
> **confused57 said:**
> Excellent instructions, but mis-typed:
```
sudo dpkg-reconfigure xserver-xorg
```

I do it all the time, thought I'd point it out.

Thank you.  I hope you will continue to do so.

---

