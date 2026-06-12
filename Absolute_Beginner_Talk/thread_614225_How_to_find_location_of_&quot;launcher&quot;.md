---
title: "How to find location of &quot;launcher&quot;"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by brad1138 on 2007-11-15
How do you find the location of the launcher for a program. I installed Weatherbug Beta. It created a Launcher link in Applications/accessories, but I want to set it to start on boot up, but I can't find the real launcher location. It is not in usr/bin or bin searching for the file name comes up with nothing (actually I don't think I have ever got the Ubuntu file search util to find a file, but that a diff. issue). It would be nice if you could right click on a launcher link and have it give you the location, seams like a kind of obvious thing to be able to do.

But anyway how can I find it?

Thanks,
Brad

---

### Post by kast on 2007-11-15
/usr/local/bin ?

---

### Post by ThrobbingBrain66 on 2007-11-15
Go to System > Preferences > Main Menu

Find the weatherbug entry, right-click it and select Properties

This will show you the command to start the program that you can add to the startup programs.

---

### Post by Paul820 on 2007-11-15
You can use, from the terminal
> whereis name_of_file
or
> locate name_of_file

---

### Post by brad1138 on 2007-11-15
> **kast said:**
> /usr/local/bin ?

Sorry, no thats completely empty

[QUOTE=ThrobbingBrain66]Go to System > Preferences > Main Menu[/QUOTE]

Tried that also, under command it just says "tempest" (which is the name of the beta version)

Thanks,
Brad

---

### Post by ThrobbingBrain66 on 2007-11-15
> **brad1138 said:**
> Sorry, no thats completely empty



Tried that also, under command it just says "tempest" (which is the name of the beta version)

Thanks,
Brad

It says tempest, which is the name of the program.  If you type that into a terminal, the program will run.  Therefore you can just put the program name into the startup programs....you don't need the full location. Don't make things harder than they have to be :)

If you absolutely need the full location, use 'whereis tempest' in a terminal.

---

### Post by brad1138 on 2007-11-15
> **ThrobbingBrain66 said:**
> It says tempest, which is the name of the program.  If you type that into a terminal, the program will run.  Therefore you can just put the program name into the startup programs....you don't need the full location. Don't make things harder than they have to be :)

If you absolutely need the full location, use 'whereis tempest' in a terminal.

Thanks, for the record, "whereis tempest" gave me 3 locations, 2 were folders and the other was a text file I had already seen in usr/bin (if I open it it say at the top "Run Script for Tempest"). So I still don't know where it really is but I wont worry about it.

Thank you,
Brad

---

