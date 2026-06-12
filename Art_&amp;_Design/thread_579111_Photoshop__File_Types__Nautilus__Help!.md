---
title: "Photoshop / File Types / Nautilus / Help!"
date: 2007-10-18
forum: Art &amp; Design
---

### Post by JeffD on 2007-10-18
Hello,

I have Photoshop 7 working via wine, and I can launch on the command line.  What I can't seem to figure out how to do is launch it as a helper application within nautilus.

I don't want it to be the default helper app, but I would like to be able to right click on a jpeg in Nautilus, and choose "open with" and have Photoshop listed, whereby the file would open in wine Photoshop.

Is this even possible?  I have spent so much time trying achieve this seemingly simple feat.

Any clues appreciated,

Jeff

---

### Post by Hairy_Palms on 2007-10-19
right click on the file you want to open and select properties, go to the open with tab, then click Add, enter a custom command to launch photoshop. then when you right click on files of that type from now on it should give you an option to open with photoshop

---

### Post by JeffD on 2007-10-19
This *almost* works.

Photoshop opens, with an error:

Could not open "/home/user/file.jpg" because of a disk error


When I follow your steps, I am basically putting this in for my photoshop command:

wine /path/to/windowsprogramfiles/Photoshop.exe 

Is there some kind of % placeholder symbol or something I need to put in here?  I am thinking that maybe photoshop, in wine, thinks my
home directory is H:/  and linux thinks it is /home/JeffD and, hence, the error?

Any clues?  I  am close!  Thanks!
:guitar:

---

### Post by Hairy_Palms on 2007-10-20
hmm,i thought that would work, i dont know how to get around the disk error though :(

---

### Post by JeffD on 2007-10-22
Bump...

Anyone else have any ideas?

Thanks!

---

### Post by Curtiss on 2007-10-22
I dont have an answer for your problem but Gimp is a very good image editor. In windows I used Photoshop Elements and Lightroom neither would work with wine and I gave gave up. 

Now that I am using Gimp the learning curve is a bit steep but Im growing to like its a very capeable editor. Raw files also open in Gimp with the raw plugin and there is also LightZone.

Good Luck

---

