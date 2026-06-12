---
title: "Vey simple Xserver question!"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Rakeris on 2006-08-07
Ok, this is like the king of stupid questions, but I just can't figure out how to tick options in the Xserver. Like in monitor config, I need to select the screen resolutions but I can't.  -_-

Please someone! As working in 1024x768 res is driving me insain!
Thanks!

---

### Post by professor_chaos on 2006-08-07
You either need to do one of two things.

Either open the file "/etc/X11/xorg.conf" and change the values for your monitor resolution. Placing the highest resolution first. Like ```
Modes           "1600x1200" "1024x768" "800x600" "640x480"
```. Then restart your X server. "ctrl+alt+backspace" 

OR

run the command "sudo dpkg-reconfigure xserver-xorg" in the commandline, making sure to select all of the possible resolutions your monitor can handle.

---

### Post by Rakeris on 2006-08-07
That is what I was trying to do, using the sudo dpkg-reconfigure xserver-xorg command. But I couldn't figure out how to select the options under screen res...I swear I tried everything, but just couldn't tick them.

But I edited the "/etc/X11/xorg.conf" and all is well. Thanks.

---

### Post by bmonkey on 2006-08-07
Hit the space bar to check the options

---

### Post by Rakeris on 2006-08-07
I knew it was something horribly simple like that...thanks.

---

