---
title: "Installing Windows Software"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by th1bill on 2007-11-09
I have installed Wine and I am just lost.  I tried to install Serif's Photo Plus 11 but got nowhere byond seeing the folser contents.  I need the answer.

---

### Post by steve.horsley on 2007-11-09
Try and find the installer executable (often called SETUP.EXE). Double-click that, and it should open in wine automatically.

---

### Post by Matthew521 on 2007-11-09
You could try using crossover

---

### Post by atomkarinca on 2007-11-09
according to the [wine application database]("http://ubuntuforums.org/showthread.php?t=608058") it should be installed without a glitch. are you sure you have run the setup till the end? if so, you should see a link to the program under applications > wine > programs

---

### Post by th1bill on 2007-11-09
What I did was to use the Adept Manager to select the install aqnd then I clicked on the check-mark button and it said that it had done several things and at the end of it all it returned me to the Adept Manager.

The only new Wine Icon is in Applications>System Tool>Wine Software Uninstaller.

The oters were already there under Applications>Accessories>Wine Help & Wine Help Browser & Wine Notepad.

Did I do bad?  And thank you for your time.

---

### Post by SoulPatch on 2007-11-09
Some programs just won't run with Wine.  But try this:

Put the .exe in your Home folder.  Open a terminal window and enter: wine setup.exe or whatever the name of the exe is. Wine should launch the executable.

---

### Post by SunnyRabbiera on 2007-11-09
you might have to configure wine to suit your needs.
in the wine menu just click on "configure wine"

just remember not all windows apps run in wine

---

### Post by HermanAB on 2007-11-09
Well, you can always install VMware Server then install WinXP or Win98SE inside of that.  Provided that you block all network access, Windows 98SE is quite reliable and fast and you won't need any anti-virus and other crapware.

---

### Post by th1bill on 2007-11-09
> **SoulPatch said:**
> Some programs just won't run with Wine.  But try this:

Put the .exe in your Home folder.  Open a terminal window and enter: wine setup.exe or whatever the name of the exe is. Wine should launch the executable.

I opened the CD and copied the Setup.exe.  I then opened the Home Folser and pasted it there.  In the Terminal I used the command line Wine Setup.exe and received the following;
err: modual: import_dll Library MSVBM60.dll (which is needed by L:Z:\\Home\\<my name>l\\Setup.exe) not found
err:modual:LdrInitializeThunk Main exe initalization for L"Z:\\Home\\<my name>l\\Setup.exe" failed, status c0000135

and all I can think is "Oops."

---

### Post by th1bill on 2007-11-09
> **HermanAB said:**
> Well, you can always install VMware Server then install WinXP or Win98SE inside of that.  Provided that you block all network access, Windows 98SE is quite reliable and fast and you won't need any anti-virus and other crapware.

That sounds like an emulator and I am seeking to avoi that.  My pyrpose in taking this on in my sixties is to turn on the next generation to Linux the way I have excited them with Windows and save them the cost of MS software.

---

### Post by Orbital75 on 2007-11-09
I found that I had to install my windows programs from a command line.

```
wine /path/to/program.exe
```

---

### Post by th1bill on 2007-11-09
I opened the CD and found the .dll.  It fired right up but could not find the files to do the install.  Next I am going to copy the files into my home folder with the .dll and Setup.exe, I believe that is the answer.  Then I'll delete the files.

---

### Post by th1bill on 2007-11-09
I copied the files and Setup started and informed me that I need IE5.  I'll have to install that in the morning although it's a shame because I hate that browser and will never use it.

Thanks once more for helping an old Veitnam vet get out of a hole of my own digging.

---

