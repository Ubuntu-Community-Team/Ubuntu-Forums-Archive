---
title: "[SOLVED] I've lost the letter &amp;quot;e&amp;quot;!"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by nachomania on 2007-11-20
I was trying to get the button a my keyboard to open and close my CD drive. I found that the command "eject -t" closed my drive after it was opened (I could open it already). 
     I opened gconf-editor (Alt-f2,), then went to metacity (apps). In keybinding commands, I changed command_1 to eject -t. In global keybindings, I changed run_command_1 to <0X81>e (0X81 was the button to open the drive). 
     This was successful in opening and closing the drive, but I lost the use of my "e" key. "E" still works. In a panic, I changed command_1 to "e", and run_command_1 to "e". Now, whenever I press the "e" key without capitals, a message saying  

"There was an error running "e":
Failed to execute child process "e" (No such file or directory)."

shows up. How can I fix my letter "e"? :confused:

P.S. Writing this was agonizing (Ctrl-V)

---

### Post by Pumalite on 2007-11-20
Maybe reconfiguring xserver and having keyboard recognized automatically will do it. But better wait for more experienced advise or people to whom this has occurred.

---

### Post by Skefflock on 2007-11-20
I've read bout a man who completely lost his keybord, so he was writing by copying letters from the names of files and links on the desktop, so you're just half as hero:) but anyway, try to unbind you "e" into gconf-editor and set the value parameter to disabled. I think this will do it.
But how to make work this too cool features (i mean letter "e" and closing the drive simultaneously - I have no idea.

---

### Post by nachomania on 2007-11-20
Well, I've gone into Synaptic, searched for keyboard and reinstalled everything I had installed

---

### Post by Dr Small on 2007-11-20
If all else fails, try Pumalite's suggestion, as it seems like it should work.

---

### Post by nachomania on 2007-11-20
I've taken out both bindings, now I'm going to try th xserver thing...

---

### Post by nachomania on 2007-11-20
Yay! It worked! Thanks a litteral ton! If you'll excuse me, I'll be typing the letter e for a few minutes.

---

