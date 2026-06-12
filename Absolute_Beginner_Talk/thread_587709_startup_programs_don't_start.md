---
title: "startup programs don't start"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by ark on 2007-10-23
i just installed gusty and tried to use screenlets as widget for compiz and it worked but i realize they don't start when i log in... and they shouldn't because they are not on the genome startup programs, so i add them but any time i log out they don't just don't start, they disappear from the startup list. 

this problem doesn't happen only with the screenlets, any command / program i add to the list is the same.

what can i do to fix this?




thx

---

### Post by Inxsible on 2007-10-23
> **ark said:**
> i just installed gusty and tried to use screenlets as widget for compiz and it worked but i realize they don't start when i log in... and they shouldn't because they are not on the genome startup programs, so i add them but any time i log out they don't just don't start, they disappear from the startup list. 

this problem doesn't happen only with the screenlets, any command / program i add to the list is the same.
what can i do to fix this?
thx
did you try saving the session after adding the new startup programs ? Sometimes that's what is required :|

---

### Post by ark on 2007-10-23
if you refer to "remember currently running aplication"  i did, i also tried automatically remember running aplications when logginng out.

if that's not what you say then no, how can i do that?

---

### Post by ark on 2007-10-23
i just saw that when i close the window of sessions when i add the programs and open it again the screenlets dissapear, i didn't even log out what is going on?

---

### Post by ark on 2007-10-23
anyone?

---

### Post by oxboy on 2007-10-23
isn't there an option in the screenlets-manager to launch the screenlet on startup?

---

### Post by ark on 2007-10-25
there is  and i tried that too but still doesn't start.

i thought of create a a simple bash script to start all the screenlets and add it to the startup list, but as before, as soon i close (even if i save the session) the session manager  and open it again, the script is no more in the list.

is there a different way to run programs at start up?

---

### Post by markyb on 2007-10-30
Has anyone found a fix for this yet, as I am getting the same problem trying to get a script to run conky at startup, but whatever I put under the startup programs list disappears after you close it.  I have checked permissions under /home/user/.config etc and all ok.

---

### Post by markyb on 2007-10-30
Finally fixed it by removing the file ~./config/autostart.  Then entered details in startup programs and it stayed there this time and conky started after reboot.

Hope this helps.

---

### Post by jasonmeansfriend on 2007-11-11
> **ark said:**
> there is  and i tried that too but still doesn't start.

i thought of create a a simple bash script to start all the screenlets and add it to the startup list, but as before, as soon i close (even if i save the session) the session manager  and open it again, the script is no more in the list.

is there a different way to run programs at start up?

same here

anyone?

about the ~/.config/autostart thing, i don't even see that file (not even in hidden files), what do i do? that file just doesn't exist

---

### Post by Valde_91 on 2007-11-19
> **jasonmeansfriend said:**
> same here

anyone?

about the ~/.config/autostart thing, i don't even see that file (not even in hidden files), what do i do? that file just doesn't exist

Hi! I had the same problem, and I delete ~/.config/autostart, now I can add everything in my preferences-> session (thanks Markyb). To delete this file you must open a terminal then run:

```
user@pc:~$ cd .config
user@pc:~/.config$  rm autostart

```

answer yes to the rm question.

then you can add and/or remove what you want on your Preferences/Session menu. Next time you will log in everything should be working. 

I used that for adding avant-window-navigator, and for me worked.
 If you have some doubts,  I look in the autostart file by coding (clearly before deleting it!)

```
user@pc:~/.config$ sudo gedit autostart 

```

I saw that this file was about screenlets, so I decided to delete it. And now everything works fine!

bye Valde_91

---

### Post by jasonmeansfriend on 2007-11-22
FIXED IT!!!:KS:KS:KS

i don't know how, but (i tested on a clean install) the problem comes from an "/home/---/.config/autostart/" directory not existing (at least for me)

just go to "/home/---/.config" and create a folder named "autostart" and then enable screenlets autostart or in gnome session manager



hope this works for you, it did for me:)

---

