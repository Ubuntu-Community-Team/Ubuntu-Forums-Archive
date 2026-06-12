---
title: "i liked to make a script to run sudo pon dsl-provider"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by jimbean on 2007-09-29
i dont know if it is called a script
but in windows it was called a {.bat} file
i could make a {.bat} file in windows and it would run commands to enable certain thing
i could also give the {.bat} file an icon on the desktop so it would look nice

this is what i would like to do in ubuntu fiesty
i would like to create a  script for

sudo pon dsl-provider

any help would be great

---

### Post by cursebg on 2007-09-29
Try this:
Create an empty file named whatever.sh and add the following lines

> #!/bin/sh
gksu pon dsl-provider

Another way is to right-click on the desktop, choose 'create launcher' and fill in for yor needs. I recommend that the launcher type be a Terminal Application

if you are using KDE replace gksu with kdesu

---

### Post by jimbean on 2007-09-29
thankyou i left clicked on desktop
 and created a launcher
and typed sudo pon dsl-provider in the command line
and changed type to, application in terminal
and named it, start internet
and it worked this time
ive tried this before
and it did not work
must be getting things straight in my nogging for linux
about 1 year learning curve
have a good night

---

