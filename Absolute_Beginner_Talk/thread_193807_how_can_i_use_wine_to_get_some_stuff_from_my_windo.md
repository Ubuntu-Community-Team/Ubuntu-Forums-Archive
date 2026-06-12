---
title: "how can i use wine to get some stuff from my windows drive?"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-10
I tried setting up wine and got this after taking an exe from my windows drive.

i think did something wrong.

> maddbaron@alchemist:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
maddbaron@alchemist:~$ wine PROGRAM /media/hda2/Program Files/WriteItNow3/WriteItNow3.exe 

---

### Post by meng on 2006-06-10
hehe.

Not:
wine PROGRAM /media/hda2/Program Files/WriteItNow3/WriteItNow3.exe

but:
wine /media/hda2/Program Files/WriteItNow3/WriteItNow3.exe

---

### Post by maddbaron on 2006-06-10
ohhhh

thanks!

question if I drag the exe to a folder in linux would it work as well?

---

### Post by maddbaron on 2006-06-10
ok i tried dragging into ubuntu didnt work now i tried from my windows drive. no working neither did i do it right?

here r some linux instructions. I dont get.

where can I get pendrive.exe?

> 
I thought I would take a moment to let you know that yWriter (and probably every other program you have written) can be run on Linux, without requiring an install of Windows or expensive emulators.
The short description of how I got it to work was to install yWriter.exe *and* PenDriveFiles.exe into the same folder, then try running yWriter.exe
Without installing the PenDriveFiles.exe, when I first tried to run yWriter, I was told that Cedega's OLEAUT32.DLL was too old and nothing I tried in the Cedega configuration files would help.
Here's a more detailed set of steps of what worked for me: First, the Linux user should install Wine ([http://www.winehq.org](http://www.winehq.org)) or Cedega ([http://www.transgaming.com](http://www.transgaming.com)) which allow some Windows programs to be run within Linux/Unix systems.
Then, using Wine or Cedega, run yWriter.exe to do the setup as normal, but at the end of the setup, *uncheck* the option to run yWriter after install.
Then, use Wine or Cedega to run PenDriveFiles.exe and tell the installer to put the files in the C:\Program Files\yWriter2 directory.
With that, a Linux/Unix user should be set!

---

