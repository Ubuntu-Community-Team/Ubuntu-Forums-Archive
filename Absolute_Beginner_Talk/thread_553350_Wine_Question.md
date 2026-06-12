---
title: "Wine Question"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by sarsippius on 2007-09-17
I have a problem I would like to solve.

I have Wine loaded on my 7.04 system.  I can get to all the programs, and run them from Wine File.  But if I wanted to make a launcher on the desktop, or menu, how do I go about doing that?

Any help will be much appreciated!

Thanks!

---

### Post by Hobo Joe on 2007-09-17
There should be a Wine launcher in the applications menu, you can copy the shorcuts to the desktop from there.

---

### Post by mc4man on 2007-09-17
if you install programs from the terminal sometimes they're added to application menu, sometimes not
also during install if your given option to create desktop shortcut go for it, it usually works
Other things that you can do are right click on exe. and create link.  You can add anything to your places tab- for instance go to program files then bookmark it and it will be added to places

---

### Post by sarsippius on 2007-09-17
The program in question only puts icons on the Start Men under Windows.

I've tried creating a launcher from the desktop, right clicking the file in Wine File (to copy and paste), clicking and dragging...nothing is working for me.

Don't get me wrong, I'm excited that I finally got this program to work.  But if I could get some icons out on the desktop, I'd be a little closer to saying "Windows...Now your failure is complete."

Thanks for the suggestions!

---

### Post by Shazaam on 2007-09-17
> **sarsippius said:**
>  But if I could get some icons out on the desktop, I'd be a little closer to saying "Windows...Now your failure is complete."!

Ahh but there is the rub, you are STILL using some form of Windows.

---

### Post by sarsippius on 2007-09-17
> **Shazaam said:**
> Ahh but there is the rub, you are STILL using some form of Windows.

Unfortunately the Linux version of this program is way to expensive for my company to dump money into.

---

### Post by mc4man on 2007-09-17
There are definite advantages to running the prog.   from the terminal
for example I have a app in program files  from the terminal it's
```
wine '/home/doug/.wine/drive_c/Program Files/ImgBurn/ImgBurn.exe' 
``` note the '...'  because of space in program files
for an app in drive_c
```
wine /home/doug/.wine/drive_c/LameXP.exe
```

If you want to navigate to drive_c go places- home folder, click view tab and click show hidden folders, find .wine click and your there   much more useful the wine file browser

---

