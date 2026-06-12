---
title: "ummm nautilus??"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Catfish_lolipop on 2007-10-26
A few days ago I upgraded to gutsy and i haven't had any problems besides the one that i have just ran into. I have no icons on my desktop and when I try to open any files or folders nothings comes up, I don't even have the ability to right click. What should i do??

---

### Post by Dr Small on 2007-10-26
You could try reinstalling Nautilus, and see if that has any effect on things.

Dr Small

---

### Post by MegaJim on 2007-10-26
can you get to a terminal?

---

### Post by Catfish_lolipop on 2007-10-26
yes, i can get into terminal.

---

### Post by MegaJim on 2007-10-26
I would check that your home directory is there, is your /home folder on the same partition as root or is it seperate?

---

### Post by Catfish_lolipop on 2007-10-26
it is on the same partition.

---

### Post by llamakc on 2007-10-26
Try running nautilus from the commandline in the terminal and see what happens.

Run it like:

```

nautilus &

```

and see if your icons reappear.

---

### Post by Catfish_lolipop on 2007-10-26
My icons did not show up, but the output from terminal command was "[1] 21852
"  I'm not sure if that helps any or not.

---

### Post by MegaJim on 2007-10-26
thats just the process identifier being displayed

```
ls -la ~/Desktop/
```

whats the output from that?

---

### Post by llamakc on 2007-10-26
Something is mucked up in your configuration files for your user. If you open from a terminal 

```

gconf-editor

```

And navigate to APPS | NAUTILUS | PREFERENCES and scroll down in the right pane to "show_desktop", is it checkmarked?

---

### Post by llamakc on 2007-10-26
> **MegaJim said:**
> thats just the process identifier being displayed

```
ls -la ~/Desktop/
```whats the output from that?

Heh. That's a great idea. I forgot to ask if the OP still had their wallpaper set.

---

### Post by Catfish_lolipop on 2007-10-26
total 28
drwxr-xr-x  5 daniel daniel 4096 2007-10-26 12:21 .
drwxr-xr-x 47 daniel daniel 4096 2007-10-26 16:37 ..
-rw-r--r--  1 daniel daniel    0 2007-10-20 21:43 madd~
drwxr-xr-x  2 daniel daniel 4096 2007-10-12 21:07 mike
-rw-r--r--  1 daniel daniel 4955 2007-04-10 15:44 nautilus-home.desktop
drwxr-xr-x  2 daniel daniel 4096 2007-10-21 07:56 NTP
drwxr-xr-x  3 daniel daniel 4096 2007-10-21 08:19 ****
-rw-r--r--  1 daniel daniel    0 2007-10-18 01:17 ZXDcasdf~

---

### Post by Catfish_lolipop on 2007-10-26
yes. it is checked. maybe I should try and use Dr Small's idea and re-install? I just don't understand how it works one minute, then all of the sudden it stops.

---

### Post by MegaJim on 2007-10-26
That's the next logical step.  If its still broken after that you can try

```
sudo dpkg-reconfigure gnome-desktop-data
```

GL

---

### Post by llamakc on 2007-10-26
You could delete the ~/.gnome ~/.gnome2 and ~/.gnome2_private directories in /home/daniel and try relogging in. Doing so WILL DELETE any settings you have saved. Your desktop/GNOME will go back to the default.

Another great way to see if Nautilus is working fine is to add a second user and try logging on as that user. See if it works just fine for that user. If so, it's something in your /home/USER directory that was inadvertently misconfigured.

---

### Post by Catfish_lolipop on 2007-10-26
I created a new user and everything works fine. so, i'm guessing that there is a problem that is only in my other account.

---

### Post by Catfish_lolipop on 2007-10-26
I LIED !!! just as i post that last reply everything started acting up again. when i click the 'show desktop' button it replys, "Your window manager does not support the show desktop button, or you are not running a window manager."

---

### Post by llamakc on 2007-10-26
> **Catfish_lolipop said:**
> I LIED !!! just as i post that last reply everything started acting up again. when i click the 'show desktop' button it replys, "Your window manager does not support the show desktop button, or you are not running a window manager."

So, have you tried installing compiz-fusion or beryl recently?

Open a terminal and type:

metacity -replace &

And see what happens.

---

### Post by Catfish_lolipop on 2007-10-26
yes, i installed beryl and everything worked fine with it until everything started acting weird. but when i put in that command it tells me "metacity: Unknown option -replace"

---

### Post by llamakc on 2007-10-26
My bad. I forgot a dash.

```

metacity --replace &

```

---

### Post by Catfish_lolipop on 2007-10-26
my screen went blank, and now everything works (for real this time lol) thank you so much for your help !!

---

