---
title: "error message- nautilus has shut down...help"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by jonynuckles on 2006-11-26
I'm as beginer as it gets but this is my first problem, any advise would be awesome:)

i switched to ubuntu in early oct and it's been perfect until i did the update download for 6.10. the update seemed to go great but now when i start the system after i login the first thing that happens is this error message "the application nautilus has quit unexpectedly... i could choose to restart, close, or inform developers, none of those options wk, if i close it or anything else it just comes back. the only thing i could figure out was to move it to a different window then everything seems to wk except "places" or anything on that list...

i hope this ? has not been asked a thousand times already, i appoligise if so, but would really appreciate any help

thanks!

jonathan

---

### Post by Ecthelion on 2006-11-27
Did you tried to reinstall nautilus?

---

### Post by jonynuckles on 2006-11-27
not yet... i know this will sound a little dumb but how do u do that? with the package manager by any chance? i'm so new at all this, and really computer challanged in the first place:) my friend that got me on linux won't answer my calls and i recently moved to another town and i never see them any more to ask...and i think my question was so dumb that no one but u offered a clue (and i know there is a sticky note that says something about it, but i could't get the bug report too through)...please help! i love this system and i even want to change my mac laptop over too once i get my desktop problem fixed..

thanks in advance for any help!!
joathan

---

### Post by 56phil on 2006-11-27
Go into synaptic System->Administration->Synaptic Package Manager. Then do a search for nautilus and reinstall all the packages that are currently installed. Good luck.

---

### Post by jonynuckles on 2006-11-27
Thank u sooo much i think thats the simple plan i needed!!!!8)

---

### Post by jonynuckles on 2006-11-27
one last question...i hope...do i have to go on the package manager and use the remove it option first? the reinstall option is not available yet but i'm afraid to remove it without asking because it warns that it will remove the desktop, and that may push me over the edge if i screw that up. i don't need to bck over anymore computers with my car:)

---

### Post by Ecthelion on 2006-11-28
> the reinstall option is not available yet
Strange, I do have that option.

You can uninstall and install it again in terminal if you want...
But I'm afraid that won't be the simpel plan you wanted...

What you could do is looking in your system logs to see if you find an error...
Or, maybe easier, type ```
nautilus
``` in terminal and post the error's you get under your command.

If it's an easy fix maybe someone can help you then...

Otherwise, the command-line reinstall of nautilus and your ubuntu-desktop etc will be the easiest possible option...

---

