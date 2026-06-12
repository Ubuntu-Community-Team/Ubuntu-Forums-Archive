---
title: "RealPlayer launcher error"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by MCO2ORD on 2006-04-08
Greetings.  Newbie here. 
I recently installed RealPlayer 10, via the wiki instructions.  I installed to the /opt directory.  Installation went well.  However, when I then go to run RealPlayer from the launcher in the Apps menu, it returns an error: "Details:Failed to execute child process "realplay" (No such file or directory)
However, when I check the /opt dir, realplay is there, and I am able to run it from there.  Any ideas on how to fix the launcher?  Any help is appreciated.

---

### Post by trent dillman on 2006-04-08
make a script, call it real.wrap

```

#!/bin/bash
cd /opt/realplayer
./realplay

```

and run that instead.

Don't forget to chmod u+x and change the directory to wherever it's installed!

---

### Post by MCO2ORD on 2006-04-09
Ok, created the real.wrap file and saved it to my desktop.  However, not quite sure what you mean by chmod u+x and changing directory... am i to chmod the real.wrap file?

---

### Post by trent dillman on 2006-04-09
First, MAKE SURE your path is right with the script (/opt/realplayer probably isn't right)! It needs to be the full path to the realplayer executable...

Open a terminal (applications > accessories > terminal), then

```

sudo mv ~/Desktop/real.wrap /usr/bin
sudo chmod 755 /usr/bin/real.wrap

```

This will move it off your desktop (less clutter) and allow other users (if any) to use real.

---

### Post by Perfect Storm on 2006-04-09
[Ubuntu Restricted wiki - Installing Realplayer]("https://wiki.ubuntu.com/RestrictedFormats#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b")

---

