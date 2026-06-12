---
title: "Directories with two words in the name"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by mrbsee on 2008-04-01
I'm using hellanzb to download files and I'd like to store them on one of my internal hard drives.  The drive is labeled "New Volume".   I'm trying to figure out how to point hellanzb to that drive... 

i've tried '/media/New\ Volume'  and a few other uses of the backslash forward slash but I can't figure it out... what is the correct usage to point to that drive... it's driving me bat **** crazy.  Now i have a bunch of directories made by hellanzb that I would like to get rid of but I can't delete them because they are in my media directory... 

Help would be greatly appreciated!

---

### Post by Barrucadu on 2008-04-01
/media/New\ Volume/ should do it. Assuming it is mounted there, of course.

---

### Post by FreewareFan on 2008-04-01
I would say you need to enter it like this:

'/media/New Volume/'

---

### Post by mrbsee on 2008-04-01
This is how I have part of it setup..   Yet it still won't download to that drive... it keeps making new directories.. for some reason it created folder in media directory called New\ Volume instead of writing to the drive... It's like it's ignoring the space and using the slash as a character instead. It is mounted there... there is a folder New Volume and it does access the drive. It's almost like it is ignoring the \ as a space command and using it as a character.

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = '/media/New\ Volume/downloads/working/'

---

### Post by mrbsee on 2008-04-01
Problem Solved!  Thank you freeware fan!  Man always when pointing to multi word directories i've had to use the \ as space... but not this time. You actually type it the way it looks... anyways thanks again.  Sheesh

---

### Post by FreewareFan on 2008-04-01
You are most welcome!  It took me a while to get used to the syntax that Ubuntu uses also..  Two things to remember in Ubuntu..  Case sensitivity is important, and if there are spaces within the file names, or directory names, you have to encase the string in '   '  .

---

### Post by Junglizer on 2008-04-01
Which is why it is often easier to simply use an underscore '_'

---

### Post by Oldsoldier2003 on 2008-04-01
> **Junglizer said:**
> Which is why it is often easier to simply use an underscore '_'

+1 spaces and Capitals are highly overrated. Underscore FTW.

---

