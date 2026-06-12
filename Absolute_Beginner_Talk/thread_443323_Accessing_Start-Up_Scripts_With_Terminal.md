---
title: "Accessing Start-Up Scripts With Terminal"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by StJimmy on 2007-05-14
I've been using ubuntu for a while, and i thought maybe i had enough experience to try to install compiz, with the xgl accelerator. so i did it, but it was really sluggish, and windows wouldn't refresh by themselfs, so i figured i'd try rebooting, but before i did, i made a big mistake  :( i added the compiz to my start up. now every time i start up, ubuntu crashes before i can do anything. i tried starting up in the "fail safe mode" or what ever it is... but it still crashes. all i can start up in is the terminal "fail safe mode". so I have a list of things i want to try, first is taking the compiz off my start up, so i just need to know how to get to System -> Preferences -> Sessions with the terminal, as I've been unable to find out how.  

If that doesn't work, then i probably messed something up while installing xgl, i followed this guide [http://ubuntuguide.org/wiki/Ubuntu:Edgy/EyeCandy](http://ubuntuguide.org/wiki/Ubuntu:Edgy/EyeCandy) and in it, they had me make backups of all the files i changed, so in the terminal, i could try to copy the backup to the modified version, and hopefully that will get me set (hopefully)

---

### Post by lazyart on 2007-05-14
In your home folder there is a hidden folder which contains the sessions file.  Since you're in terminal only, try

nano /home/*user_name*/.gnome2/sessions

you might have to use sudo first...  nano is a funky text editor but it gets the job done.  Conversely you can rename the sessions file to something else so you can get into the GUI and then use gedit.

---

