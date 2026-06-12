---
title: "Using Wine"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by mike6789 on 2007-03-24
Hello, 

I'm new to linux and of course wine.  I installed the program in the add/remove program option under the applications.  My first program attempt to install was Xfire.  The majority of my contacts are on that list so I need to use it.  Well the install shield pops up and I install it, and choose to run when finished, then it puts this little application box up on the screen as seen below:

[img]http://img462.imageshack.us/img462/5851/screenshotfx2.png[/img]

So I restarted the computer and here I am now, the app box is gone but still no xfire.

Can someone tell me how to properly access the program?

---

### Post by freebird54 on 2007-03-24
Did you make a launcher for it?  Can you run it from the terminal?

To make a launcher, just right click on your desktop, and choose 'create a launcher'.

Here is an example of a wine 'launcher' for a little Bridge playing prog I run..

```
wine "/home/freebird/.wine/drive_c/Games/Easy Bridge/EasyBridge.exe"
```

I don't know where your program went on install, but I would think something like

```
wine "/home/yourname/.wine/drive_c/Program Files/programnamedir/progname.exe"
```

should do the trick - replacing yourname with user name, programnamedir with the install directory, and progname.exe with the actual run name of your program.

Hope that isn't TOO confusing - but if your program appeared to install OK then that's all you need to run it easily..

---

### Post by mike6789 on 2007-03-24
Alright so I typed in the path to the program, and it launched that little box, seen in the screenshot.  And in the terminal it just repeated:

```
fixme:ole:OleCreate 
        {8856f961-340a-11d0-a96b-00c04fd705a2}
        {00000112-0000-0000-c000-000000000046} semi-stub!
```

I'm not exactly sure what to make of that. :(

---

### Post by freebird54 on 2007-03-24
Sounds like a Windows dependency problem to me.  Do you have the .dll files that it uses installed in wine?  I don't know xfire, so I am not sure what it is/does - but I suspect was written in either VB or a .net language, and requires a support library.

Are there any 'docs' for xfire?   It might suggest that an .ocx or a .dll is required and not supplied by the installer...

Sorry can't be more specific - cruise through .wine/drive_c/windows/system32 and see what ole*.dll there are for example....

---

