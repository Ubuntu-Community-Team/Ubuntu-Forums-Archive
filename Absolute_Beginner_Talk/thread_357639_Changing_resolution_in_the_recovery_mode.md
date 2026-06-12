---
title: "Changing resolution in the recovery mode"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by bobbyshafter on 2007-02-09
Hi i need help... 
                       After changing my resolution,dapper lock up before the log in screen.

 I tried loging in the recovery mode .I get the error message "i810 virtual width (2560) is too large for the hardware (max 2048).

 How do i change the resolution so i can get x to start........

Is there a easy way or do i have to edit the /etc/x11/xorg.conf file
I ask this because i have never use nano or vi  ...

---

### Post by taurus on 2007-02-09
From the recovery mode, run

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by bobbyshafter on 2007-02-09
Thank it works ...this is the what make linux great 
I learn somthing new ever day ...now i can help someone with the same problem.

---

### Post by bobbyshafter on 2007-02-09
How do i check which version of xorg i have?

---

### Post by taurus on 2007-02-09
Applications -> Accessories -> Terminal
```
X -version
```

---

### Post by r4wMUnt34q on 2007-12-19
Is there a way I can set the resolution to **generic, plug n play, 1280x800 + widescreen in recovery mode in text ui as root?** Because I have a big problem and I cant read the screen after ubuntu loads, I tried a data projector and I messed some settings up probably

---

### Post by jken146 on 2007-12-19
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

