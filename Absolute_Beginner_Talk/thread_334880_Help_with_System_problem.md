---
title: "Help with System problem"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2007-01-09
I've really messed it up, I think.
I was having trouble with Totem so I removed the following using synaptic package manager: totem, totem-mozilla and totem-xine.
Now the system will boot only to the password page, and after I enter username and password it goes to a blank page and stops.
When I restart, ie. Ctrl+Alt+ Backspace I can choose an option which gives me the terminal window.
Can someone please tell me what to type in to continue the loading process or how to undo my blunder?
I'm running ubuntu 6.10 and I also have 6.06 on another computer which I could possibly get the files off of, if they are the same, and I knew which ones.
I'm using another computer now to access this forum.
I'm very new to linux too.
Thanks---Holly

---

### Post by jpeddicord on 2007-01-09
When you hit Ctrl+Alt+Backspace and you get the terminal, login with your user account that you normally use. (Note: When typing in your password, it will not give you any feedback.)

Then, type this and hit enter:
```
sudo apt-get install ubuntu-desktop
```
It will ask you for your password again. Then, it may ask you a yes or no answer. Type **Y** if it does and hit Enter. After that, it will re-download any missing files, including Totem that you uninstalled.

Once done, type:```
sudo reboot
``` to restart your system. Hopefully you should be able to sign in. If not, post again here with any errors that appear.

I'm not sure why removing Totem did this, but if putting it back on your system works then that is a problem solved. :)

Jacob

---

### Post by taurus on 2007-01-09
After you log in from a console, try to install those programs again or do

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by Milt888 on 2007-01-09
Guys, I'm not ignoring you. It's just loading a lot of stuff.
Thanks---Holly

---

### Post by Milt888 on 2007-01-09
Thank you--Thank you guys.
I'm now back on the system typing this.
Guess I'll learn to leave things alone 'till I learn more. I'm saving your instructions.
Such great help on this forum.
Thank you--Holly

---

