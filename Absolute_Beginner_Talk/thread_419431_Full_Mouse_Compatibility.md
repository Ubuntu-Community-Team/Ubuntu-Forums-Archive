---
title: "Full Mouse Compatibility"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by punkypine on 2007-04-23
I have a 5 button logitech mouse, as well as a scroll well that goes sideways.

the left, right, and wheel push, as well as vertical wheel scroll all work, but the back and forward buttons dont do anything, and neither does side scrolling. there arent any options for button mapping in the default mouse setup in preferences, so how would i make these buttons functional?

---

### Post by igknighted on 2007-04-23
> **punkypine said:**
> I have a 5 button logitech mouse, as well as a scroll well that goes sideways.

the left, right, and wheel push, as well as vertical wheel scroll all work, but the back and forward buttons dont do anything, and neither does side scrolling. there arent any options for button mapping in the default mouse setup in preferences, so how would i make these buttons functional?

Oh man... it takes a little more work (not hard though), but multi-button mice are so much better utilized in linux (and logitechs are well supported) than windows.  Heres a link to a tutorial (it says for dapper, although I used it on edgy and it worked AOK and I imagine the same is true of feisty.  There are many more good ones on the forums as well if you care to look.  You can set up the extra buttons to do anything you want (even emulate keyboard shortcuts) so all your favorite commands are just a mouse click away... Link: [http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+tilt+wheel](http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+tilt+wheel)

---

### Post by freebird54 on 2007-04-23
Here's a link that helps:

[http://ubuntuforums.org/showthread.php?t=246770&highlight=multi+button+mouse](http://ubuntuforums.org/showthread.php?t=246770&highlight=multi+button+mouse)

Good luck


EDIT: Too slow!

---

### Post by punkypine on 2007-04-23
thanks for the links

i followed the instructions that freebird's link had (they seemed much easier, lol), and... well the buttons do stuff now, just not the right stuff. the forward button acts as a second middle mouse button while the back buttons acts as a right click. 

i have a logitech mx400 laser mouse btw

any idea whats going on?

---

### Post by freebird54 on 2007-04-23
I think it's all in the order you specify the buttons in xorg.conf.  Several of the people responding to that thread I pointed you to had similar things to tweak.  Take a look at the z axis mapping entry.  Isn't this fun?  ](*,)

---

### Post by punkypine on 2007-04-23
something went horribly horribly wrong.

i was trying to do it, made the computer restart
couldnt load it all the way
it then took me to a blue screen asking me if i want to look at the error
i hit okay, seemed like it had something to do with the mouse.

then i got back to a black screen where i could type, but nothing did anything there, no matter what i typed (is it supposed too). so i turned my computer off and restarted it in recovery mode. at this point, i logged in and typed in 
> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-logi
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
but even after the first line, it said "file could not be found", so it didnt do anything

in other words, i cant load up ubuntu anymore and i have no idea what to do.

---

### Post by ilovebsod on 2007-04-23
do you see xorg.conf listed in /etc/X11 when you browse to it in CLI?  can you open it w/ vi?  browse to the areas you modified, are they the modified versions or the original?

---

### Post by punkypine on 2007-04-23
> **ilovebsod said:**
> do you see xorg.conf listed in /etc/X11 when you browse to it in CLI?  can you open it w/ vi?  browse to the areas you modified, are they the modified versions or the original?

could you explain how to do that? i have no idea what that means, lol. i just started using ubuntu/linux like 2 days ago.

---

### Post by freebird54 on 2007-04-23
If you open a terminal, try to get a listing of the file names in the folder /etc/X11 with:
```

ls -l /etc/X11
```

This will tell us exactly what is in there.  Probably just a typo on the filenames used there.

---

### Post by ilovebsod on 2007-04-23
> **punkypine said:**
> could you explain how to do that? i have no idea what that means, lol. i just started using ubuntu/linux like 2 days ago.

when you reboot and X is unable to launch it should take you to command line eventually.  login w/ your username/password then cd /etc/X11, do a 'dir' or 'ls' to list the contents of the directory.  do you see a xorg.conf file?  do you see a xorg.conf.bak (I assume this is the backup file you created)?

if the xorg.conf file is present type 'vi xorg.conf' (w/o the quotes), this will open the xorg.conf in vi (a text editor).  scroll down to the sections you edited, do you see your edits or do the see the original entries?

do a 'shift+:' (w/o quotes) then type 'q' (w/o quotes) and enter, this will close down the editor w/o saving.

now open your backup file in the same way.  Do you see the changes or the original?  if the original exit out then do a 'sudo rm xorg.conf' (this will delete the current xorg.conf file), then 'sudo cp xorg.conf.bak xorg.conf' (this will copy the backup file and rename it, removing the .bak).

reboot and you should be good.

---

### Post by punkypine on 2007-04-25
ok here's the thing...

when i boot up normally i never get to a command line... after showing me the error report thing, it just takes me to a screen with nothing. i can type on it, but its not a command line.

if i go in recovery mode, i do get to a command line but it always says that even the directory is not found...

---

### Post by punkypine on 2007-04-25
bump/update

but if i go into safe mode and do first "cd /etc/"
then on the next line "dir"

on the list of stuff that comes up, x11 is there.

but then if i do "cd /etc/x11" it says not found...

---

### Post by freebird54 on 2007-04-25
Just a thought - CAPS COUNT! :)  The directory is /etc/X11.  For editing in this mode, I would suggest using nano, which shows the possible commands on the bottom of the screen (where ^o means <ctrl>o).  This is easier than trying to remember them all right away!

cp is Copy   ls is List  mv is Move and the <tab> key will help fill in your commands for you (with long filenames etc)

---

### Post by punkypine on 2007-04-25
hahaha omg caps? i never thought of that

lemme go try that

---

### Post by mister mick on 2007-04-29
> **punkypine said:**
> something went horribly horribly wrong.

i was trying to do it, made the computer restart
couldnt load it all the way
it then took me to a blue screen asking me if i want to look at the error
i hit okay, seemed like it had something to do with the mouse.

I have this same exact problem.  I had made a few changes to my xorg.conf without restarting in between each change, but I was able to restore it and narrowed it down to the code change I found at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox)

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

This bit of code added to my xorg.conf crashes X and the error log refers to the input device section of the xorg.conf, but then says no screens could be found.  The only other change I have made to my xorg.conf is my nvidia-settings changes.

Any suggestions would be greatly appreciated as I use my mouse button 5 in WoW.

---

