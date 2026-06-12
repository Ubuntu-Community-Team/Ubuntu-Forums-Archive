---
title: "How do I make a 'launcher' in KDE?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by EddieA on 2007-02-27
Sorry about this but I can't figure out how to make a launcher (as in Gnome) in KDE!
In particular I want to launch apps I've installed and  .sh files which KDE keeps opening  in Kate etc for editing.
It's probably staring me in the face but I can't find it](*,)

---

### Post by mahy on 2007-02-27
Try right-clicking the desktop and select 'launcher' from the context menu. Is that what you want?

---

### Post by EddieA on 2007-02-27
The only thing I see similar is 'create new/link to application' - but if this is it I don't know what to put in the 'command' box to get a .sh file to run.

---

### Post by igknighted on 2007-02-27
Try either /path/to/file.sh or sh /path/to/file.sh

---

### Post by EddieA on 2007-02-27
Thanks for your help but it ain't working - ](*,) 
the install instructions say 
'navigate to install directory and run "./filename.sh"' - and this works
but I want to run it from a shortcut on the desktop or panel
this should be so easy!

---

### Post by mahy on 2007-02-27
did you type an absolute path, i.e. /home/username/filename.sh ??

---

### Post by EddieA on 2007-03-01
Hi sorry about the delay in replying.
Yes I tried both the suggestions above

---

### Post by Detonate on 2007-03-01
Do the permissions of the file allow it to be "executable"?  And who owns the file?  Does it have to be run as "root"?  If so, you have to use the "Run as a different user" function and specify "root' and it will ask for the password when you try to execute it from the desktop icon.

---

### Post by picpak on 2007-03-01
Try running

```
chmod +x ./filename.sh
```

then create the shortcut.

---

### Post by EddieA on 2007-03-01
All the permissions are mine- i installed it :) 
if i navigate to the directory in konqueror press ctrl-E and enter the './filename.sh' command it runs. But I cannot make a launcher to run it.

---

### Post by Maestro23 on 2007-03-01
Try this. Open terminal:

> whereis program

Should give you the path to the bin file.  Use this path in you launcher.

---

### Post by EddieA on 2007-03-02
#tx for help
Whereis doesn't find anything
this is a script to launch a java program - so it's probably nor installed as per usual programs.
as I've said if I launch Ctrl-E; './filename' from the installation directory it works but I can't launch it from the desktop or panel.

---

### Post by igknighted on 2007-03-02
Ok, I played with KDE a bit and I think you might not be going to the right tab when you create the shortcut.  Try going 'create new' -> 'link to application' -> application tab -> put /path/to/file.sh in the box labeled "command".  Then title it what you want and you should be good to go.  You can even give it an icon if you wish.

---

### Post by EddieA on 2007-03-02
igknighted tx
This is exactly what I've been doing - even 'browsing' from 'command' to get the exact path with no typos.

While writing this reply I decided to try one more thing - I set the 'Work Path' in the same tab (below the 'command' box) and bingo! - worked first time.  - Yippeee - Done it! 

Now why couldn't the install instructions tell me that ???

Thanks everybody for helping me with this - much appreciated! :)

---

### Post by igknighted on 2007-03-02
> **EddieA said:**
> igknighted tx
This is exactly what I've been doing - even 'browsing' from 'command' to get the exact path with no typos.

While writing this reply I decided to try one more thing - I set the 'Work Path' in the same tab (below the 'command' box) and bingo! - worked first time.  - Yippeee - Done it! 

Now why couldn't the install instructions tell me that ???

Thanks everybody for helping me with this - much appreciated! :)

interesting... i've never used that line before.  You know, that might be the same as checking "run in terminal" in gnome, since its a .sh that might be necessary... hmm.  I can't explain to you why that works, so if anyone else knows I'd love to hear as well.

---

### Post by EddieA on 2007-03-02
I don't know if this is the answer but I have Netbeans installed which also runs from a script
 but installs its own shortcuts/launchers.
I compared the scripts and Netbeans make references a 'program directory' variable and subsequently sub-directories of that  - the other program (Compendium) doesn't. The Compendium script makes reference only to 'system' directories and there is no reference to where the program resides or it's files are located.
As the install instructions said to launch it from the install directory presumable they expected it wouldn't be necessary to write a  better script - but to forget launching it from elsewhere??
I'll email them anyway.

---

