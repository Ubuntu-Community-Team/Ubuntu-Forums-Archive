---
title: "compiz problem !!!"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by drsyntax on 2007-06-29
after i installed compiz i faced this problem [http://ubuntuforums.org/showthread.php?t=486885](http://ubuntuforums.org/showthread.php?t=486885)

but i think that i got it solved by posting it on compiz.org forums 

i posted my problem at compiz.org forums and got this :

> As far as I can say the problem is related to a conflict between metacity and compiz. I think metacity can't start because compiz is already running but the session-manager waits for metacity to be loaded (or waiting times out after about 2 minutes). 

You can either remove 'gnome-wm' from your startup-programs (System/Settings/Sessions) or use gconf-editor to set the key /desktop/gnome/applications/window_manager to the value '/usr/bin/compiz'. Removing gnome-wm may only cause more trouble so try the second method first 

but the second soln didn't work ( may be i did something wrong ), so i tried the first soln and it fixed my problem
my first question is : what is 'gnome-wm' and what trouble it may cause if i removed it from start up ??

second question : every time i was starting my system i had to run 'compiz --replace' and 'gtk-window-decorator --replace' to run compiz and show my window borders, i added these tow commands to start up to make them rrun automatically , is there another way to make compiz start with my system rather than adding it to start up :D ?

Thanks, ANY HELP WILL BE APPRECIATED

---

