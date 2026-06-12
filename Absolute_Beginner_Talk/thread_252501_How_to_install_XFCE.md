---
title: "How to install XFCE?"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by buckdog05 on 2006-09-06
I am using an old (500 MHZ PIII) computer with 300+Mb of ram, and would like to use XFCE to speed it up.  I have tried to install it by downloading the graphical installer, and Ubuntu couldn't run it.  Did I download the wrong thing?  I am an absolute noob, today is my first day wtih Ubuntu installed and working perfectly.

Thanks!

---

### Post by croak77 on 2006-09-07
Did you;
```
sudo aptitude install xfce4
```

---

### Post by benfindlay on 2006-09-07
If you've installed ubuntu, then it's got gnome installed already. I'd recommend downloading the iso for xubuntu, which comes with xfce as the default desktop.

If you've installed ubuntu server then you can just type ```
sudo aptitude install xubuntu-desktop
``` and it will download and install the entire desktop package for you (office apps, gimp etc etc are all included I believe).

However, if you already have gnome installed then I'd recommend removing gnome once xfce is on, as together they take up a lot of space!

Works extremely well on older machines! ;)

---

### Post by shoot2kill on 2006-09-07
dont forget to update

```

sudo aptitude update
sudo aptitude install xubuntu-desktop

```

---

### Post by buckdog05 on 2006-09-07
When I tried the command, I got an error that read:
0 packages upgraded, 88 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 204MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Error!
E: Couldn't find a changelog for ivy
E: Couldn't lock list directory..are you root?


What should I do?

Thanks!

---

### Post by buckdog05 on 2006-09-07
Also, I tried going into Apps and Add/Remove, but nothing seems to work.  Thanks!

---

