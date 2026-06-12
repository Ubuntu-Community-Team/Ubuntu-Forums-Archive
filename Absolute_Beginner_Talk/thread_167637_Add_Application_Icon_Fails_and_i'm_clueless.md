---
title: "Add Application Icon Fails and i'm clueless"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by JL_COG on 2006-04-28
When i click on application; Add Application an error window opens:

error
Cannot Launch Entry
Failed to execute child process "/home/jlcog/desktop/setup-en.exe"
No such file or directory

Did my installation become corrupted somehow? Can i correct this easily.
All i know about Linux would fit here: ()

Using Breezy Badger

Thanks from a total newb

---

### Post by matthewv on 2006-04-28
Welcome to ubuntu forums :)

The problem you describe sounds weird... it shouldn't occur and I don't know why it would...

In the meantime, to run add applications, hit Alt-F2 and the type ```
gnome-app-install
``` and hit enter

---

### Post by JL_COG on 2006-04-28
Thanks, Matt. i'm thinking i must have goofed it up in less than two hours! ugh!
looks like a really good time to reinstall before going too far and wasting more time. if i'm wrong, somebody stop me ... fast :)

---

### Post by matthewv on 2006-04-28
A reinstall should fix it... but if it doesn't, I would be stumped... still I don't know how that could have happened...

:)

---

### Post by r4ik on 2006-04-28
Hold on a sec give it some time youre not drowning are you :)

---

### Post by user1397 on 2006-04-28
Just got to System Tools--> Applications Menu Editor and be sure that on the left side, Applications is highlighted, and then on the right side, righ-click on Add Applications-->Properties, and put in this command in the part that says "command": /usr/bin/gksudo /usr/bin/gnome-app-install
That should work!
**Don't** reinstall! That is a very drastic measure!

---

### Post by matthewv on 2006-04-28
sry guys... I'm on dapper and couldn't change that... I should have known....:-# :( :oops:

---

### Post by JL_COG on 2006-04-28
well, thanks but all that did was change the path listed in the error :(

umm ... could someone running breezy badger please tell me what the path is in THEIR Add Application preferences? Cannot seem to figure out how to do a search for that file. (Wierd, an .exe in Linux)

---

### Post by user1397 on 2006-04-28
[quote=JL_COG]well, thanks but all that did was change the path listed in the error :(

umm ... could someone running breezy badger please tell me what the path is in THEIR Add Application preferences? Cannot seem to figure out how to do a search for that file. (Wierd, an .exe in Linux)[/quote] Wow that's really weird because my path is exactly like the one I posted before, *"/usr/bin/gksudo /usr/bin/gnome-app-install"*

---

### Post by JL_COG on 2006-04-28
The winning entry turned out to be:

gksudo gnome-app-install

Add Application works fine now.
Thanks to all who helped, jl

---

