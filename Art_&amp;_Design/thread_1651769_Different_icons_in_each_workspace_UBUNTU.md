---
title: "Different icons in each workspace UBUNTU"
date: 2010-12-23
forum: Art &amp; Design
---

### Post by ELRINDELL on 2010-12-23
[http://www.youtube.com/watch?v=_meEsxZRppk](http://www.youtube.com/watch?v=_meEsxZRppk)

---

### Post by ELRINDELL on 2010-12-27
**Different icons and wallpapers in each workspace UBUNTU:**

[http://www.youtube.com/watch?v=mIRCpHIBueQ](http://www.youtube.com/watch?v=mIRCpHIBueQ)

I've improved the script, the next video I will explain the script

---

### Post by Razor338 on 2010-12-27
you have not uploaded any script there!!!

---

### Post by ELRINDELL on 2010-12-28
hello:

I explain how I've achieved, the script can be improved:

DESKTOP SET FOR FOUR:

**NEED**:

sudo apt-get install avant-window-navigator ((((DIFFERENT DESKTOP LAUNCHER))))
sudo apt-get install wmctrl (((TURN THE DESK)))

***_1__) YOU HAVE TO GO TO THIS FILE_:*** home / manuel / .config ((((MANUEL CHANGED))))) 

Open the file, **user-dirs.dirs**

AS YOUR LANGUAGE, PLEASE NOTE THAT SAYS:

XDG_DESKTOP_DIR="$HOME/**Escritorio**" (((THIS IS SPANISH, ESCRITORIO = DESKTOP)))

*_**2) BELIEVE IN THE Folder:**_* home / manuel / (((MANUEL CHANGED))))

((((Where the Escritorio folder exists in my language )))))

MAKE THAT THREE OTHER FOLDERS calls just as you noted in point 1;

**Escritorio2, Escritorio3 and Escritorio4**

_***3) Now inside the folder;*** home / manuel / .config_

YOU CREATE THESE **5 folders:**

Any name, preserve it in the final script

**FOUR named folder;**

DESKTOP1, DESKTOP2, DESKTOP3, DESKTOP4

**And another folder:**

LANZADORES

((((( IN SPANISH Lanzadores = LAUNCHERS ))))

***4) Now copy the file user-dirs.dirs, which is in home / manuel / .config***

you paste the file **user-dirs.dirs** inside FOUR folder you created:

DESKTOP1, DESKTOP2, DESKTOP3, DESKTOP4

*_5) **Now go into that folder**_* and modifies the **user-dirs.dirs** ARCHIVE

IN FOLDER DESKTOP1:

XDG_DESKTOP_DIR = "$ HOME/Escritorio"  ((((no change)))

IN FOLDER DESKTOP2:

XDG_DESKTOP_DIR = "$ HOME/Escritorio2"

IN FOLDER DESKTOP3:

XDG_DESKTOP_DIR = "$ HOME/Escritorio3"

IN FOLDER DESKTOP4:

XDG_DESKTOP_DIR = "$ HOME/Escritorio4"

*_**6) CREATE SCRIPTs inside  Lanzadores folder:**_*

you must create 4 script, empty files, you paste the script inside, give execution permissions, (((RIGHT BUTTON UP, LEAVES)))

_**1 THE CALL TO SCRIPT DESKTOP1:**_

[B]gconftool-2-s-t bool / apps / nautilus / preferences / show_desktop false
gconftool-2 - type string - set / desktop / gnome / background / picture_filename "/ home/manuel/.config/imagenes_escritorios/mini_1.jpg"
cp / home/manuel/.config/desktop1/user-dirs.dirs / home / manuel / .config /
wmctrl-or 0.0
killall nautilus
sleep 0.15
gconftool-2-s-t bool / apps / nautilus / preferences / show_desktop true; nautilus[/B]

THE FIRST LINE hide the icons ....
THE SECOND LINE; THE DESKTOP WALLPAPER NEW (((CHANGE "/ home/manuel/.config/imagenes_escritorios/mini_1.jpg" WHERE HAVE YOUR PICTURES)))) (((I create a folder with ALL WALLPAPERS EN / home / manuel / .config / imagenes_escritorios)))
THE THIRD LINE COPY OF DIRECTORS DESKTOP1 (you created) the file user-dirs.dirs and paste it into / home / manuel / .config / DELETING that existed before
THE FOURTH LINE TOUR DESK (((NOTE my screen is 1280X800, THEN FOR EACH desktop you 1280 wmctrl add ))))) 
THE FIFTH LINE NAUTILUS RESTORES 
The sixth line makes a stop in the process 
THE SEVENTH LINE SHOWS THE DESKTOP ICONS

**_2 THE CALL TO SCRIPT DESKTOP2:_**

gconftool-2-s-t bool / apps / nautilus / preferences / show_desktop false
gconftool-2 - type string - set / desktop / gnome / background / picture_filename "/ home/manuel/.config/imagenes_escritorios/mini_2.jpg"
cp / home/manuel/.config/desktop2/user-dirs.dirs / home / manuel / .config /
wmctrl-o 1280.0
killall nautilus
sleep 0.15
gconftool-2-s-t bool / apps / nautilus / preferences / show_desktop true; nautilus

**_3 THE CALL TO SCRIPT DESKTOP3:_**

conftool-2-s-t bool / apps / nautilus / preferences / show_desktop false
gconftool-2 - type string - set / desktop / gnome / background / picture_filename "/ home/manuel/.config/imagenes_escritorios/mini_3.jpg"
cp / home/manuel/.config/desktop3/user-dirs.dirs / home / manuel / .config /
wmctrl-o 2560.0
killall nautilus
sleep 0.15
gconftool-2-s-t bool / apps / nautilus / preferences / show_desktop true; nautilus
**_4 THE CALL TO SCRIPT DESKTOP4:_**

gconftool-2-s-t bool / apps / nautilus / preferences / show_desktop false
gconftool-2 - type string - set / desktop / gnome / background / picture_filename "/ home/manuel/.config/imagenes_escritorios/mini_4.jpg"
cp / home/manuel/.config/desktop4/user-dirs.dirs / home / manuel / .config /
wmctrl-o 3840.0
killall nautilus
sleep 0.15
gconftool-2-s-t bool / apps / nautilus / preferences / show_desktop true; nautilus

WHEN I HAVE ALL THE SCRIPT IN Lanzadores FOLDER, I can  CALL FROM  avant-window-navigator


I HOPE THAT SOME PROGRAMMER ENCOURAGES AND DOES IT WITH AN ALONE SCRIPT WHO BELIEVES ALL THE DIRECTORIES ACCORDING TO THE LANGUAGE OF EACH ONE...
 I CANNOT PROGRAMME ONLY I HAVE BEEN EXPERIMENTING, THANK YOU

sorry for my english

---

### Post by ELRINDELL on 2010-12-28
[http://www.youtube.com/watch?v=I634Q1Ucjls](http://www.youtube.com/watch?v=I634Q1Ucjls)

---

### Post by jlahn on 2011-01-17
Thanks a lot, elrindell for this workaround! I do not know how you got your script running, though, because I had to do a lot of man learning and googling before I got it working for me. 

Now I can switch between the workspaces, and the wallpapers and icons load with a certain lag. Moving windows from one workspace to another does work, but still only switches workspaces, but not wallpapers or icons. So the script is not triggered by workspace switching, but calling the script triggers workspace switching. 

Also, of course, the first Desktop folder is still the default in Places and for Save Under dialogues. But the time lag before windows and background load is clearly the most irritating, although minor. And the pictures are a little stretched - how do I adjust stretching settings here?

Also, while I could link the scripts to my hotkeys for workspace switching, the panel workspace switching buttons do still not take this whole scripting workaround into account. _*Anybody got any idea for how to do this?*_ I mean, technically you have the same wallpaper and icons on all workspaces at the same time now, as far as i can tell, and only the fact that windows are still being on different workspaces makes this whole thing useful. But when I use the workspace switch now, forgetting the scripting solution, I find myself with different windows (say, work instead of pleasure), but still the same wallpaper and icons and have to quickly call the script to make the workaround seem pleasurable... :rolleyes:

Also, being a complete beginner, I cannot really judge whether this workaround has the potential to seriously disrupt my system or could provoke any negative consequences. *_Any pros who would like to comment on this? _*Thank you so much. :D

Well, but apart from these 'minor' and some aesthetic issues (which is why it would not necessarily label the whole thing SOLVED, it works. At last, different workspaces for different activities with different icons and wallpapers!

Here's the script code that got it working for me (deleted several spaces and corrected several arguments, reduced lag time by reducing sleep, also had to fiddle with the wmctrl x and y values for each launcher, they have to be different for each workspace!, also added no-default-window so nautilus would't open a new window each time I changed):

> #!/bin/bash

gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/XXXXX/.config/desktop_pictures/desktop.jpg"
cp /home/XXXXX/.config/Desktop/user-dirs.dirs /home/XXXXX/.config/
wmctrl -o 0,0
killall nautilus
sleep 0.01
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop true; nautilus --no-default-window

# end scriptOk, so far - thank you a lot for commenting on the implementation and safety issues mentioned above!

---

### Post by jlahn on 2011-01-17
Ok, I wanted to post a link to this thread from 

#1 [http://ubuntuforums.org/showthread.php?t=1516915](http://ubuntuforums.org/showthread.php?t=1516915)
#2 [http://ubuntuforums.org/showthread.php?t=357146]("http://ubuntuforums.org/showthread.php?t=357146&page=3")

so that people might find it and comment on this workaround and other options (I did not really get the difference between the php approach mentioned in #2 and the one here), but due to maintenance issues this won't be possible for some time:

[http://ubuntuforums.org/announcement.php?f=11](http://ubuntuforums.org/announcement.php?f=11)

I'll try to do it it later. :)

---

### Post by predato on 2012-10-08
Nice job ELRINDELL! Though the script you posted has some typoes I managed to run script manually. it must be "wmctrl -o 0,0" needs comma not dot. I have a problem with nautilus, after it has been killed,the spawned process spikes cpu. 
Thank you for showing us that it's possible to have different icons in each workspace

---

### Post by overdrank on 2012-10-08
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

