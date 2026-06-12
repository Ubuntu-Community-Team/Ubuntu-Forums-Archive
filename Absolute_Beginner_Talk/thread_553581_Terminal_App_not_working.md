---
title: "Terminal App not working"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by technoidiot on 2007-09-17
I am totally new to Linux and its derivatives but am somewhat knowledgeable with computers. Today was my first full day with Ubuntu. Trying to get things set how I would like them to look and run. Problem is 'Terminal' in the apps menu seems to be lost. The option is there but when clicked the window opens then immediately closes. In researching on what I did or what happened to it I found the program folder and can not see it. I have tried to install the app from the Synaptic Manager with no luck as each time it shows different dependencies but will not install them. As I remember it worked prior to my installation of Beryl. ](*,)

Am also looking for syntax rules to be able to move things around or get them into the startup folder. :confused:

In advance, in the event i forget, thanks to all who respond and help.

---

### Post by alienexplorers on 2007-09-17
Try running > sudo aptitude reinstall xterm

---

### Post by redbob on 2007-09-17
Well, if your menu doesn't show the launcher "Terminal", you could take a while in a command-line shell:
- Press Alt-Ctrl-F2 to open command-line session;
- make a login;
- at the cursor, type the line suggested by Alienexplorers or "sudo apt-get install xterm";
- Alt-Ctrl-F7 bring you back to Gui interface, or the Gnome, as they call it!

---

### Post by technoidiot on 2007-09-18
Neither option worked. Tried both entries. Is it possible one or more of the dependencies is not installed?

---

### Post by alienexplorers on 2007-09-18
Try doing from ctrl-alt-F2:
> sudo aptitude update 
sudo aptitude upgrade
sudo aptitude reinstall xterm
enter ctrl-alt-F7

---

### Post by ravenwere on 2007-09-18
Isn't the package called gnome-terminal?

Pardon me I'm a kde user

---

### Post by alienexplorers on 2007-09-18
try: ctrl-alt-F2
> sudo aptitude reinstall gnome-terminal
ctrl-alt-F7

---

### Post by garyed on 2007-09-18
I'm pretty new at this but I'll throw in my 2 cents.
If I understand you right  you can see the Terminal in Applications but clicking on it doesn't take you into the terminal. Why not try right clicking on Terminal & then add it  to your Desktop.
Then you can right click on the Desktop Icon you added &  go to properties> launcher & see what it shows for command line. It should just say  gnome-terminal , at least in Feisty.
"gnome terminal" is found in /usr/bin directory. Could your path be messed up?
You could try entering the entire path in the command line window - /usr/bin/gnome-terminal       
 & see what happens. 
Just a shot.

---

### Post by alienexplorers on 2007-09-18
try;
> alt-F2 and type in gnome-terminal if it comes up it's working.

---

### Post by technoidiot on 2007-09-18
have tried everything mentioned above. nothing worked. error message 

"wasn't able to locate file for gnome-terminal package need to manually fix, couldn't lock list directory." - this message was for update - upgrade - reinstall xterm

GPC error - the following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3ff0db166a7476ea. - this message was for reinstall gnome-terminal.

Could Beryl be having a conflict with my system? it seems windows will not open properly unless i have beryl running. Also system crashed when i tried crt-alt-F7.

---

