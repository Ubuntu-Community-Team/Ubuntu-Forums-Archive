---
title: "help with neat screen capture command"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Adam590 on 2007-06-21
What I'm trying to do is to easily and quickly be able to capture a portion of the screen (as a .bmp for best quality), open it in GIMP, manipulate it if I want to, then save it as a .jpg while deleting the original .bmp file. This process will allow me to grab a screenshot and have it at whatever file size/image resolution I want.

I plan on using one long command to do this, then entering an alias for it in .bashrc, like "cap" or something.


This is the command so far:

[COLOR="Blue"]cd Desktop/ && import capture.bmp && gimp ./capture.bmp && rm ./capture.bmp[/COLOR]

(I realize the "cd Desktop" part isn't really necessary, but I'm going to substitute a desktop directory/folder for that in #2 below)
 
Amazingly, it works, but I have a couple of ways I'd like to refine it:

1. I'd like to have the terminal hide/minimize itself at the beginning of the command so it doesn't end up in my capture. How do I do that?

2. I'd like a second version, called "capsave" or something, that would *not* delete the original. This would involve automatically changing the file name each time ("capture1.bmp", "capture2.bmp", etc.). Do I need to make this into a script to accomplish this, or could it be done with aliased commands? 

Thanks!

---

### Post by shearn89 on 2007-06-21
not sure about the terminal hiding (maybe try devilspie?), but for the second one you could create another script, and simply change ```
rm ./capture.bmp
``` to ```
mv ./capture.bmp ./capture2.bmp
```

EDIT:
you could also try and find the envrionment variables for date/time, so that the name isn't capture.bmp but date-time.bmp or something.

---

### Post by Adam590 on 2007-06-21
Thanks, but it seems I had a very poor understanding of what alias was all about. 
 
["There is no mechanism for using arguments in the replacement text"]("http://www.ss64.com/bash/alias.html")

Also, I don't think capture would work in an alias anyway - seeing as how it's not a bash command...?

---

### Post by shearn89 on 2007-06-21
you could download and install "scrot" (sudo apt-get...), and then write that into a bash script maybe?

---

