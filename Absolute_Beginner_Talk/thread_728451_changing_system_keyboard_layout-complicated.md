---
title: "changing system keyboard layout-complicated"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by BetterSense on 2008-03-18
I'd like to  know exactly how the system keyboard layout is controlled. I usually install Ubuntu with a US keyboard and layout. Then I change the keyboard layout within the gui or, on a buddiy's machine, with

```
 setxkbmap dvorak
```

However if I set the keyboard layout in the GUI, the login screen is still Qwerty. In this case adding 

```
"Option" "Xkbvariant"  "Dvorak'
``` 

to the xorg.conf enables Dvorak layout in the login screen. However, if I hit Ctrl+Alt+F2 to get to the 'real' terminal, the keyboard layout is in Qwerty, I assume because it exists below the Xserver and I installed the system as US.

Now when I installed on my eeepc, I told the installer to use Dvorak keyboard layout. On this machine, to the best of my memory, the keyboard layout was Dvorak in the shell, the gui, and the login screen from the get-go. But since I never relabel my keys, what if I want to change the keyboard layout to Qwerty in the terminal, so my friend can help me work on my machine?

 Is there any way to change the keyboard layout in the terminal?

---

### Post by BetterSense on 2008-03-19
bump for great justice

---

### Post by Daveth on 2008-03-19
I had a similar mismatch between the xorg and gnome, with one saying I had a "gb" setting and the other a "us", though when i checked they were both "gb". I used the configuration editor in system tools, and altered the setting from there (just re-typed over the "fault") and it solved that problem. Might work for you.

---

