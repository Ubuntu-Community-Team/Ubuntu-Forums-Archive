---
title: "Installing program w/ WINE"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by brdmartin on 2007-02-11
Hello
Im trying to install the windows program Digital Photo Professional, using WINE. It seems like Im close to getting it to work. So I type: 
```
cd /media/cdrom/
Then...
wine setup.exe
```
The CD begins to spin, and for a few seconds, the active line in the terminal is blank. but nothing happens. When I attempt to eject the CD, I get an unable to eject media- due to device is busy, even after a couple of minutes. Closing the terminal allows me to eject the CD.

It appears that the artificial C drive is configured correctly, although Im not sure if anything needs to be done though winecfg. I was able to see the wine C drive through the terminal.
```
cd ~/.wine/
ls
```
But when I type ```
cd /drive_c/
``` I get a- no such file or directory

I've allready enabled GIMP to be able to read .cr2 files, but it is quite slow, and half the time the pictures are either completely black, or are pink.

Suggestions??? Thanks again for helping a newbie.

---

### Post by machoo02 on 2007-02-11
Have you installed anything else through WINE yet?  If not, it might be easier to remove you .wine folder and start fresh.```
rm -rf ~/.wine
winecfg
```
This will remove the wine directory in your home folder, recreate it, and open up the WINE configuration.  Click on the 'Drives' tab, and click on the "Autodetect" button.  Now, all of your drives should be detected properly.  Then try reinstalling your program.

Hope this helps.

---

### Post by brdmartin on 2007-02-11
When I try it, I get:
```
rm: cannot remove `.rf': No such file or directory
rm: cannot remove `/home/brian/.wine': Is a directory
```I tried removing the .rf, and I got ```
rm: cannot remove `/home/brian/.wine': Is a directory

```
.
I deleted and recreated the C drive though winecfg, but Im getting the same results as before.

and yes, I've not installed anything with WINE yet, can't seem to get it to work... yet anyway.

---

### Post by machoo02 on 2007-02-11
Sorry...I accidentally typed a '.' instead of '-' in my code.  Try it again, if you would...

---

### Post by brdmartin on 2007-02-11
lol :) , thanks for the fix on that. It worked as far as re-creating the directory, and I can now get into the drive_c, but there is no difference when I attempt to do the ```
wine setup.exe
``` it just spins the CD for a few seconds. I don't know if it means anything, but on the drive_c, I cannot get into the program files folder, I get a no such file or directory.

---

### Post by Aranel on 2007-02-11
You say you enter "cd /drive_c/" to access WINE's fake C: drive? There's the source of the second problem - don't put the slash at the beginning. It's looking for a directory called drive_c in your *root* directory.

As for the more imminent problem, I really don't know what to tell you... in my experience, WINE either works or it doesn't. And since it's not telling you anything via command-line output, there's not a whole lot that can be diagnosed...

---

### Post by brdmartin on 2007-02-11
>  As for the more imminent problem, I really don't know what to tell you... in my experience, WINE either works or it doesn't. And since it's not telling you anything via command-line output, there's not a whole lot that can be diagnosed...

Yeah, I was beginning to think that might be the case. Perhaps I'll look at some of the other software options out there. But any further suggestions on how I might get this to work would be great.

---

### Post by machoo02 on 2007-02-11
You could try changing the windows version that WINE is mimicking...by default it is set to Windows 2000, but most people have better luck getting programs to run with Win98.

---

### Post by brdmartin on 2007-02-11
> **machoo02 said:**
> You could try changing the windows version that WINE is mimicking...by default it is set to Windows 2000, but most people have better luck getting programs to run with Win98.

Tried with the settings at XP, 2000, 98, and 95... darn, still nothing

---

### Post by garybrlow on 2007-02-11
Before anything else try to look up that particular program your trying to install via Wine's AppDB ([http://appdb.winehq.org/]("http://appdb.winehq.org/")) to see if it has been registered and others have tried running it and is actually working/installable. Not all windows programs run on WINE. Some run somewhat ok, quirky and/or incomplete. Some don't even install or run at all but usually WINE does provide errors on screen. Some programs take quite a while to execute on WINE. You may have to wait a bit for an executable to run its course. To installation its easier, open the cdrom via your filemanager, right click on the executable and chose "open with other application", click on "use a custom command", and type "wine" on the space provided, set it to default so that the next time you right click on an exe file the "Open with wine" option will be present. But whatever method you choose to install is fine.

Is this the DPP by Canon? AppDB has currently nothing on it. Its System Requirements ask for a WindowsXP with 512MB of RAM. Other than that its should show something given the simple requirements but then again it just might not install at all.

For future reference on any command line commands, to access help information on usage etc. all commands accept the "--help" option to display syntax and/or usage information. To see extended info use "man x" (replace x with a particular command for example rm).

Cheers!!! :) 

GaryBrlow :D

---

### Post by brdmartin on 2007-02-11
DPP is a Canon product. I found that webpage, and unfortunately, no mention of DPP. I've also tried the "open with other app" in the GUI, and was a deja'vu experience to attempting it with the terminal, in other words, nada. No error messages appear when trying to run the setup.exe, the active terminal line is blank for a few seconds, and then just goes back to the directory I was at (media/cdrom/). I'll try running it again, with just waiting for a while, to see if it will show up. 

Has anyone used any of the other software to run windows programs? I'd like to know what you think of them.

thanks again:popcorn: :guitar: :lolflag: 
EDIT: CD's been spinning for about 20 minutes, with no changes, doesn't look like that will work either. the good news is that the corel installer worked just fine with WINE, now I just got to track down that registration number.


> **garybrlow said:**
> Before anything else try to look up that particular program your trying to install via Wine's AppDB ([http://appdb.winehq.org/]("http://appdb.winehq.org/")) to see if it has been registered and others have tried running it and is actually working/installable. Not all windows programs run on WINE. Some run somewhat ok, quirky and/or incomplete. Some don't even install or run at all but usually WINE does provide errors on screen. Some programs take quite a while to execute on WINE. You may have to wait a bit for an executable to run its course. To installation its easier, open the cdrom via your filemanager, right click on the executable and chose "open with other application", click on "use a custom command", and type "wine" on the space provided, set it to default so that the next time you right click on an exe file the "Open with wine" option will be present. But whatever method you choose to install is fine.

Is this the DPP by Canon? AppDB has currently nothing on it. Its System Requirements ask for a WindowsXP with 512MB of RAM. Other than that its should show something given the simple requirements but then again it just might not install at all.

For future reference on any command line commands, to access help information on usage etc. all commands accept the "--help" option to display syntax and/or usage information. To see extended info use "man x" (replace x with a particular command for example rm).

Cheers!!! :) 

GaryBrlow :D

---

