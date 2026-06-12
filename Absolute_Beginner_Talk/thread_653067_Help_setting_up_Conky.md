---
title: "Help setting up Conky"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-12-29
I installed conky using the guide on this link ([http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)). When I log on or off I can see all the system info for a few seconds. During regular use, however, I cannot. Could it be because it is conflicting with my gdesklets (which are located in the same area of the desktop)? Any help would be appreciated.

---

### Post by intense.ego on 2007-12-29
bump, anyone?

---

### Post by JillSwift on 2007-12-29
edit ~/.conkyrc and change the bit that says:```

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
``` comment out the top-right line and uncomment one of the others.
Hope this helps!

---

### Post by intense.ego on 2007-12-29
sorry for asking this but what do you mean by "commenting out"?

---

### Post by taurus on 2007-12-29
> **intense.ego said:**
> sorry for asking this but what do you mean by "commenting out"?

Means to remove the # in front of the line.  So, if you want conky to start at top right, you need to remove the # in front of **alignment top_right**.

---

### Post by intense.ego on 2007-12-29
Thanks both of you. I tried it and am going to reboot tomorrow after i get some sleep (i have some downloads going so i am not going to do it now).

---

### Post by JillSwift on 2007-12-29
no need to reboot, just (in a terminal window):```
killall conky
conky &
```to restart it =^_^=

---

### Post by intense.ego on 2007-12-30
It worked! However, as soon as I did "conky &" my gdesklets closed down. Should I just reposition them on the opposite side as conky? Also, is it possible to include a background in the conky display because it is hard to read with my desktop background?

---

### Post by JillSwift on 2007-12-30
> **intense.ego said:**
> It worked! However, as soon as I did "conky &" my gdesklets closed down. Should I just reposition them on the opposite side as conky? Also, is it possible to include a background in the conky display because it is hard to read with my desktop background?Don't know why gdesklets would have vanished on you. Try logging out then back in - that will probably bring them both back.

And yes, it's easy to change conky to add a background, or outline what it draws in black. The [conky site]("http://conky.sourceforge.net/") has a complete "manual". =^_^=

To have conky draw its window on a solid background, find "own_window_transparent yes" and set it to "no". Or, to have conky outline its drawing in black to help set it off from your background (my preference) find "draw_outline no" and set it to yes.

---

### Post by intense.ego on 2007-12-30
thank you again. is this all in the same ~/.conkyrc ?

EDIT: When I checked my desktop right now conky was not there so I did the "conky &" command and it appeared. However, if I close the terminal it goes away too. Here is the output of that command:


> Conky: can't load font 'arial'
Conky: statfs '/media/hda1': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hda1': No such file or directory
Conky: desktop window (e0005b) is subwindow of root window (52)
Conky: window type - override
Conky: drawing to created window (4200003)
Conky: drawing to double buffer


---

### Post by JillSwift on 2007-12-30
> **intense.ego said:**
> thank you again. is this all in the same ~/.conkyrc ?Yeppers =^_^=

---

### Post by JillSwift on 2007-12-30
> **intense.ego said:**
> When I checked my desktop right now conky was not there so I did the "conky &" command and it appeared. However, if I close the terminal it goes away too. Here is the output of that command:That's odd.
Close the terminal by typing "exit" instead.

---

### Post by intense.ego on 2007-12-30
I have figured out some ways of customizing conky with the conkyrc file but is there any more intuitive method, like with a GUI?

EDIT: 

Nevermind, I found this thread ([http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)) with many templates.

---

