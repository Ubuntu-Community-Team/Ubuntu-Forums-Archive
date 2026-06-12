---
title: "Photoshop 7.0 launcher problem"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by devosion on 2007-11-02
I've managed to run Photoshop fine from a terminal but after creating a launcher Photoshop 7.0 is telling me...
> 
Cannot complete your request because of missing or invalid personalization information.

Which makes absolutely no sense because when I run it in a terminal the program does just fine, but from my .sh file, which runs the exact same commands that I would normally use in terminal, I get the problem.

The commands in the .sh file are as follows...
> 
cd '/root/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/'
wine photoshop

---

### Post by BLTicklemonster on 2007-11-02
Bash it? 

how the heck did you get PS to work in the first place? I have CS2 to where it will start, and come up, but it's really slow, and eventually just stops running all together.

---

### Post by devosion on 2007-11-02
Not quite sure what bash means, but i'll try it if you let me know. :)

And 7.0 worked pretty easily when I installed and ran it through wine. Im not surprised CS or CS2 are giving you problems though, even when I was messing around with them in windows I was surprised by the security features adobe implemented into those versions of PS. Case in point why 7.0 is my fave.

---

### Post by skywisenight on 2007-11-02
How about just making a luncher with the full out command instead of a .sh file?

> 
wine '/root/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/photoshop.exe'


---

### Post by devosion on 2007-11-02
Just tried that. Ran into the same problem again. This is very strange...

---

### Post by skywisenight on 2007-11-03
Are you logged in as root when you try to run this?  If not, maybe you should install ps7 under your own profile.

---

### Post by mdpalow on 2007-11-03
Photoshop 7 is the highest version that currently works consistently with Wine. If you want to run CS2 or CS3, install VMware. It's also a heck of a lot better than Wine.

---

