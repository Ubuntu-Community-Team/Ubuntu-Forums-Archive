---
title: "HELP! Terminal closing"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by mikej_96 on 2007-03-08
I was changing my terminal profile settings, and i accidentally checked the "Run a custom command instead of my shell" box. -   I didnt change the "When the command exits" option, which was defaulted to "Exit the terminal". 

Now I cannot open the terminal to change this back, since it closes before i can change anything. 
Does anybody know how i can change this??

---

### Post by o_fortuna on 2007-03-08
I think this can be fixed. Press Alt+F2 to bring up the run command and type
```
gconf-editor
```
Look under Schemas -- Apps -- gnome-terminal -- profiles -- default
Then find custom_comand. Right click and click unset key. That should do it.

---

### Post by mikej_96 on 2007-03-08
Ok, I just tried that, but I still the terminal still closes. The 'custom_command' keeps re-appearing every time i open a terminal. should I unkey the 'use_custom_command' as well?

---

### Post by skale on 2007-03-08
I have a dirty trick that might work. What we are going to do is start the terminal, when X starts, and get it to run something, which will possibly give you enough time to fix your settings before it terminates.  It's a long shot, but I have nothing better I can think of.

Open your .xinitrc file (in your home directory) with whatever editor you choose.  Go to the last line (which should say "exec <something>" and add a '&" to the end, so that line becomes "exec <something> &" Press enter, and on the next line type "gnome-terminal --execute top" (without the quotation marks of course!).  Now, [Ctrl] + [Shift] + [Del] to restart X, and log on again.  When you log on, ideally, the terminal should start, and should show a table of the processes running on your computer.  Quickly change the settings back to what they should be. After that, remove what we added to .xinitrc, so it goes back to what it was before.  If the terminal does not start, that will suck.  Check to make sure that your .xinitrc file looks like how I described.

If the above did not work, you are stuck with `sudo aptitude remove gnome-terminal && sudo aptitude install gnome-terminal` in your console ( [Ctrl] + [alt] + F1).  THat still might not work.


I also think there is a way to do it via gconf-editor, but since I am not at a GNOME computer, I can't tell you.  Look on the internet or these forums for something.  If there is, hurrah!
Good luck!

---

### Post by Daishiman on 2007-03-08
Actually, I think that what might work better is to uninstall and purge the Gnome-Terminal.

Do this: with Synaptic, do a complete (make sure it's "Mark for Complete Removal") the gnome-terminal and gnome-terminal-data packages.

Then install them again or install any other terminal.

---

### Post by mikej_96 on 2007-03-08
I cannot fine the file you described. (or any like it containing an exec line at the end.)

---

### Post by mikej_96 on 2007-03-08
I just tried doing a complete removal of the gnome-terminal and gnome-terminal-data packages. I reinstalled them but my terminal window still closes.

---

### Post by o_fortuna on 2007-03-08
The .xinitrc file can be found by hitting Ctrl+H to show hidden files (files starting with . are hidden and can be shown this way). But don't bother with this it would be easier to press Alt+F2, check "run in terminal" and type in top.

If that doesn't work, here's the best way to do it: ~/.gconf/apps/gnome-terminal/profiles/Default (remember to press Ctrl+H to see it). Open up the xml file in gedit (Text Editor) (NOT in firefox -- you need to right click it and select open with other app if Text Editor isn't there and look for it in the list). Find this line:
```
<entry name="use_custom_command" mtime="1173408725" type="bool" value="false">
```
"use_custom_commmand" is the important part. Yours won't be exactly the same -- make sure value="false" is there and not value="true"
Save it and try the terminal again -- it should work.

By the way, since you uninstalled gnome-terminal, make sure to go into synaptic and see that ubuntu-desktop is still installed.

---

### Post by mikej_96 on 2007-03-08
Thank you o_fortuna! the "top" thing worked. I was a delete the profile and restore the default. ( I looked in the hidden files and couldn't find the .xinitrc file. oh well though - pressing alt + f2 worked great ) 

also, yes i did make sure to reinstall the ubuntu-desktop. 

Thanks for your help everyone!

---

### Post by o_fortuna on 2007-03-08
> **mikej_96 said:**
> Thank you o_fortuna! the "top" thing worked. I was a delete the profile and restore the default. ( I looked in the hidden files and couldn't find the .xinitrc file. oh well though - pressing alt + f2 worked great ) 

also, yes i did make sure to reinstall the ubuntu-desktop. 

Thanks for your help everyone!
I'm glad it worked out :) I don't have an .xinitrc file either though, so I wouldn't worry about it.

---

