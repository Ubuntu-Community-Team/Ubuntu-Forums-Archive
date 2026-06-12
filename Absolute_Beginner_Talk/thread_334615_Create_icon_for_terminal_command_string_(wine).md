---
title: "Create icon for terminal command string (wine)?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by az_s_za on 2007-01-09
I have a windows program (cis.exe) that I run with wine.  The big problem is that it must be run from inside the directory in which it is housed.  Just steering to the directory while invoking wine does not work.

The quickest way I have found to run it so far, is, I have created an alias that does this:
[FONT="Courier New"][B]cd /home/aaron/.wine/drive_c/rcis/cisapp ; wine cis.exe
[/B][/FONT]
So I have to open a terminal and run the alias that runs the above command string.

How can I create a desktop (or panel) icon that will run this command string?

N.B. Adding a custom application launcher to a panel and trying to run this command does not work.

---

### Post by energiya on 2007-01-09
> **az_s_za said:**
> 
How can I create a desktop (or panel) icon that will run this command string?
N.B. Adding a custom application launcher to a panel and trying to run this command does not work.

if it doesn't work, try making a script that will do all the stuff for you. Make a new file <name>.sh and paste
```

#!/bin/bash
cd /home/aaron/.wine/drive_c/rcis/cisapp
wine cis.exe

```
and then write in the terminal
```
chmod +x <name>.sh
```

Now you can make an application launcher to the script file. It should work.
(Have you tried "wine /home/aaron/.wine/drive_c/rcis/cisapp/cis.exe" ? Becouse it usualy works)

---

### Post by orb9220 on 2007-01-09
Right-click panel and create a launcher.

in command for me to launch dvdshrink I use:   wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"  the quotes are needed since wine directory has spaces in folders or file names.

Yours would be **wine /home/aaron/.wine/drive_c/rcis/cisapp/cis.exe** if that doesn't work sorry. 

And did you use wine to install it? The folder rcis should have been installed to "C:\Program Files\

Always use wine to install an application then run winecfg to add it to wine.

---

### Post by az_s_za on 2007-01-11
> Make a new file <name>.sh and paste
Code:

#!/bin/bash cd /home/aaron/.wine/drive_c/rcis/cisapp wine cis.exe

and then write in the terminal
Code:

chmod +x <name>.sh

Now you can make an application launcher to the script file. It should work.

This worked!  Thank you VERY much.


For orb9220:
using "wine /home/aaron/.wine/drive_c/rcis/cisapp/cis.exe", the application starts, but stalls when looking for another windows application that it requires.  That is why it has to be run from inside the directory in which it is installed... it always looks for the other application in the current working directory.

No, it wasn't installed using wine.  That doesn't work.  This is a very simple, but extremely odd application.  It took a few of us some time to work out how to run it.

Now that I have an icon for it, I have the icing on the cake!

Thanks for replying to my post.

---

