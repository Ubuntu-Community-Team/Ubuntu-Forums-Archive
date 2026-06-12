---
title: "Help with Resolution and Mouse"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by snipes23 on 2007-06-05
K, I Finally get Ubuntu Installed.  Had to do a little more than the ATI X**** sticky which I plan on posting to help out.  

Problem 1) 
I'm having a resolution problem.  I go into graphical xorg config by typing sudo dpkg-reconfigure xserver-xorg,  At resolutions, i have the first 3 at bottom selected, as well as 1280x768.  But once I save everything, reboot, get back in.  It Displays on 1024x768.  I try to change res in screen resolution preferences, but all it gives is 1024x768, this is using vesa driver.  Should I attempt to change to ati?  Or should I download ati install file? not sure what to do.  

Problem 2)
Is there any fixes for a mouse, I can move cursor, use right and left side for clicking, but no scroll.  I just checked razer site and no linux drivers.  Gonna so some more searching about these two problems.  

Would really appreciate the help.

Thanks, Mike.

---

### Post by raeb on 2007-06-05
I have a razer diamondback as well, and here's my section of the xorg.conf that allows me to use 5 of the 7 buttons and the wheel works perfect.

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```

As far as the resolution goes, you can try adding the resolution manually to your xorg.conf.  Make a backup of your config and add "1280x768" to the right Depth mode that you run.  Then restart xserver with ctrl-alt-backspace.

---

### Post by snipes23 on 2007-06-06
Im debating If I should take the chance with the res, Thanks for the mouse fix.  I was literally going crazy without a scroll mouse esp. using mozilla haha.  Later

---

