---
title: "Changing buttons on touchpad"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by jeepinpete on 2007-04-15
I am trying to reassign the left button on my laptop touchpad to be the middle button.  I use the touchpad itself as the left button, and leave the right button as is.  So far I have tried xmodmap with no luck.  Any ideas?

Thanks,
Pete

---

### Post by mac.ryan on 2007-04-15
> **jeepinpete said:**
> So far I have tried xmodmap with no luck.

What did you try? Where did you get stuck?

---

### Post by jeepinpete on 2007-04-18
I am following this [how-to]("http://ubuntuforums.org/showthread.php?t=316441&highlight=touchpad+button")

Enter ```
xmodmap -pp
```And get: ```
There are 9 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              4
        5              5
        6              6
        7              7
        8              8
        9              9

```Then I enter:```
xmodmap -e "pointer = 2 1 3 4 5 6 7 8 9"
```

The result: ```
xmodmap -pp

There are 9 pointer buttons defined.

    Physical        Button
     Button          Code
        1              2
        2              1
        3              3
        4              4
        5              5
        6              6
        7              7
        8              8
        9              9

```

Now when I use xev, it still report button 1 when I click on the left button.  I am not certain whether that is right or not (is xev reporting the hardware, or the interpretation?).  But in Firefox, where a middle click opens a link in a new tab, it is instead still acting as a left mouse button and opening the link in the same tab.  Since I have had this laptop for three years, using the left touchpad button as the middle button is so ingrained that it is driving me nuts!:lolflag:

---

