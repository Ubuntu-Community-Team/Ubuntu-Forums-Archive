---
title: "Launcher for windows program"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by steven8 on 2007-02-27
I have installed a windows program via wine.  I've used winefile to find and run the program, and it works fine.  Now, I have tried the Create Launcher to make a shortcut to the program, but it fails.  

Can I create a launcher for a program such as this?  If I can, what do I ned to do to make it.

Thanks,

Steve

---

### Post by jpeddicord on 2007-02-27
When you create the shortcut, prefix the command with "wine". For example, to run program.exe in your home folder, use:

```
wine ~/program.exe
```

To run one that Wine installed in the Program Files folder, it would be similar to:```
wine "~/.wine/drive_c/Program Files/program.exe"
``` If there is a space in the filename, you will need to add quotes around it.

---

### Post by drs305 on 2007-02-27
jacobmp92's examples are the standard commands to launch a wine-installed program. However, there are other possibilities as well, depending on how your program was installed. I use Password Vault and it didn't install in the Program Files directory, so it's launcher command is:

wine "C:\Acerose\Acerose.exe" 

When I install something with wine, I always select the option to install a desktop shortcut for two reasons. First, it gives me the icon which I can then 'steal' for my panel launcher. Secondly, I just drag the shortcut up to the panel where it attaches, complete with whatever the launch command is. That launch command can be more complicated than the ones above, but the panel launcher works (   env WINEPREFIX="/home/drs1/.wine" wine "C:\NoteTab\NoteTab.exe"  )

---

### Post by steven8 on 2007-02-27
Well, jacobmp92's commands are probably just what I need, as I did a basic install, choosing all the defaults.  I will check the exe for spaces, but I believe there are none.

I am going to submit this game to the wine database as a working program.  It is based on directx 9, and runs very well.  It has sound effects, but no streaming audio for the background music.  They do a great job over at the wine project!!

Thanks a bunch, guys.  I can't try this until I get home from work in the morning, but I'll post my results.

---

### Post by steven8 on 2007-02-27
I have one more question, as I am always a questioning person.  jacobmp92, you said that if the program name has any spaces, you need quotes.  Do you quotes within the quotes you show, like this:

wine "~/.wine/drive_c/Program Files/"program name.exe""

or just quotes around the whole path, as you showed?

---

### Post by oo-boon-too on 2007-02-27
You just put quotes over the entire thing, to denote it is a string.
wine "~/.wine/drive_c/Program Files/This is a cool program.exe"

---

### Post by steven8 on 2007-02-27
Most excellent.  Thank you.

---

### Post by FlashDragon on 2007-02-27
As another Ubuntu convert, I too have Windows programs I'd like to run. 

I've got a strange situation on my hands though. I've got a client with a proprietary Windws application and the software maker says it won't work on Linux. Of course, they won't say if they've tried it, they just say it won't work.

Will Wine run any Windows app, most of them or just a select few? The reason I ask is my client will have to pay for the software before we can test it (no demo, oh yeah, life's fair...)

Thanks,

Pete

---

### Post by steven8 on 2007-02-27
> **FlashDragon said:**
> As another Ubuntu convert, I too have Windows programs I'd like to run. 

I've got a strange situation on my hands though. I've got a client with a proprietary Windws application and the software maker says it won't work on Linux. Of course, they won't say if they've tried it, they just say it won't work.

Will Wine run any Windows app, most of them or just a select few? The reason I ask is my client will have to pay for the software before we can test it (no demo, oh yeah, life's fair...)

Thanks,

Pete

Wine is a recreation of the windows api, which will allow windows programs to run.  Of course, since wine is not windows itself, but an open attempt to recreate the windows api from scratch, not all programs will run successfully in wine.  It is a work in progress.

First you have to install wine.  In add/remove, click the 'show unsupported applications' button, then find wine, and install it.  After it's installed, follow the next steps.

The way to test your client's software is to put it on a disk, open a terminal, type in winefile.  This will open the wine file browser.  Browse to your disk media>cdrom, and double click the executable.

This is the method I used to install the game I am now running.  Is your client's program a standalone, or will you be running an installer?

---

### Post by FlashDragon on 2007-03-01
Thanks. I'll be visiting the client on Friday or Monday. Let you know how it works out.

---

### Post by steven8 on 2007-03-01
> **oo-boon-too said:**
> You just put quotes over the entire thing, to denote it is a string.
wine "~/.wine/drive_c/Program Files/This is a cool program.exe"

This did not work, I'm afraid.  Did not throw an error, but nothing happened.  My path is:

wine "~/.wine/drive_c/Program Files/Soda Pipes/Soda Pipes.exe

It just sits there, and plays nothing.  Any thoughts?

---

### Post by steven8 on 2007-03-01
Got it!  Got it!!

I have NEVER had success with hand typed in filepaths in Ubuntu.  Windows, no sweat.  Go figger.  Anyway, I used the browse function, selected my executable, then put wine in front of it, put quotations around it, and the dang thing works just fine!!  Well, after I used winecfg to set my proggie to XP, so it would stop crashing. :)

Thanks guys!!

---

