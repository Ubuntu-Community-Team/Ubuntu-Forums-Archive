---
title: "Kubuntu Session Manager?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by croppyboy on 2007-01-06
I have been using Ubuntu (gnome) for about 5 months and have decided to give Kubuntu a try . . .

My question: Is there an equivalent to the Gnome session manager for KDE? I want to add programs that will auto-start with the system - and assign different priorities so that Beryl will start before other programs - but I haven't been able to figure out how to do this in Kubuntu . . .

I know I can add a program to the .kde/autostart . . . but how do I assign a startup priority? Is there a simple session manager equivalent?

Also, since Kubuntu auto-saves previous sessions . . . will the startup programs conflict if they were running in the previous session (I sometimes get a message on startup that a previous instance of Kontact is running after I reboot)?

---

### Post by quartzy on 2007-01-06
There is a basic sort of autostart manager.

Use alt+f2 and run kcontrol.

KDE Components -> Autostart Applications

But it doesn't appear to have anyform of priority, I would assume it's done by the order it reads them so a hack maybe to make it so the ones you want run first are called 1-Beryl 2-Something etc.

---

### Post by croppyboy on 2007-01-06
Thanks for the help . . .

I tried kcontrol . . . however, on reboot, there are error messages (for each of the apps) after the desktop loads saying that there is no "type=" . . .

Any ideas?

---

### Post by quartzy on 2007-01-06
Ok after some playing found that the number ordering should work, 1-name 2-name 3-name etc.

And as for the Type open the files it created in ~/.kde/Autostart and add the line

```
Type=Application
```

And all should be well :)

---

### Post by croppyboy on 2007-01-06
Thanks for the help . . . I'll give your method a try.

I also found a work-around that I just tried (before reading your post) . . .  [http://gentoo-wiki.com/HOWTO_Autostart_Programs]("http://gentoo-wiki.com/HOWTO_Autostart_Programs")

I created a bash file in .kde/Autostart and made it executable . . .
```
#!/bin/bash
/usr/bin/beryl-manager
```

It worked . . . but I only wrote the one for beryl (to test it) so I am not sure how it will order it . . .

---

### Post by quartzy on 2007-01-07
The Number system should still work for scripts like that, I was playing with that system but it seems fairly vague for when it wanted to work and when it didn't ](*,)

---

### Post by croppyboy on 2007-01-07
Thanks for your help . . .

I am using the method you suggested and everything seems to be working. I was having a few problems with beryl . . . but I finally got it sorted out and it is starting when I want it to now . . .

For beryl, I also had to add the following (to 1-beryl.desktop):
```
X-KDE-autostart-after=kdesktop
```

and create a new folder ~/.kde/env with the following script:
```
export KDEWM=/usr/bin/beryl
```

saved it as kdewm.sh - rebooted - and now everything starts when I want it to.

Thanks again! :-D

---

### Post by croppyboy on 2007-01-07
Forgot . . .

I found this part of the solution at [http://forum.beryl-project.org/viewtopic.php?f=44&t=54&p=5380]("http://forum.beryl-project.org/viewtopic.php?f=44&t=54&p=5380")

---

### Post by quartzy on 2007-01-07
> **croppyboy said:**
> Thanks again! :-D

No problem, glad I could help. :)

---

### Post by Ateo on 2007-05-18
> **croppyboy said:**
> and create a new folder ~/.kde/env with the following script:
```
export KDEWM=/usr/bin/beryl
```

saved it as kdewm.sh - rebooted - and now everything starts when I want it to.

This is all I did and Beryl starts as part of the KDE desktop. I *do not* have anything in .kde/Autostart to launch Beryl, only Emerald.

Thanks for this tip!!!

---

### Post by Ateo on 2007-05-18
So, with a little testing, here's another formula that works well.

1. Create ~/.kde/env/kdewm.sh

2. Add the following code to ~/.kde/env/kdewm.sh (the name is arbitrary)```
#!bin/bash
export KDEWM=/usr/bin/beryl
emerald --replace&
```

3. Make executable```
chmod +x ~/.kde/env/kdewm.sh
```

4. Remove beryl and emerald scripts from ~/.kde/Autostart

5. Fin.

---

