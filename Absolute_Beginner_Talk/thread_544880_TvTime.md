---
title: "TvTime"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by djbob on 2007-09-06
Installed tvtime and basically all was working except the sound.  I somehow accidentally hit the "mirror" option and now when I start it the initial screen stays on for 3-4 seconds and then it completely disappears.

When I attempt to start from terminal I get this response:

Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/bob/.tvtime/tvtime.xml
Segmentation fault (core dumped)

Yes, I am also a noob, but would be grateful for any assistance to this problem.

Thanks

---

### Post by yabbadabbadont on 2007-09-06
Try deleting the '.tvtime' directory in your home directory.  You will need to enable the option to show hidden files and folders in Nautilus in order to see it.  (Hidden files/directories all start with a period as the first character of the name)

---

### Post by djbob on 2007-09-06
Thanks!!!:) That fixed it.  Now I just have to work on the sound issue.

---

### Post by sargetech on 2007-09-13
Hi dudes,
I have another way to do it
if you go into your home folder
and find the .tvtime folder just go inside it and
open up the tvtime.xml with a text editor
and scroll to the bottom of the list and you'll find
a line like this

name="FullScreen" value="0"/><option name="MirrorInput" value="1"/></tvtime>

just change "MirrorInput" value to  "0" instead of "1" 
and save the file
tvtime will open up just fine after that and 
all other settings will be intact ( brightness,contrast,hue,,,,etc!!!)

Worked for me!!

Linux is Life!
Live long and Prosper!!:KS:KS:KS

---

