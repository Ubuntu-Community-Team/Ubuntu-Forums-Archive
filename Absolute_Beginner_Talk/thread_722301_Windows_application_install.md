---
title: "Windows application install"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by mebu99 on 2008-03-12
Hello,
   I am trying to see if I can get one of our applications to work with Ubuntu.  Let me give some background.

The application (eVIN) is for simple data collection.  It is programed in a .net framework.  I have installed Wine and the MS .net framework 1.1 on my Ubuntu workstation and that install went fine.  When I double click on the setup.exe file for eVIN nothing happens.

I have gone into the terminal window to do the wine install, but I having trouble finding the best method of install.  

This is what I have tried in the terminal window:

Code:
wine msiexec '/home/%user%/Desktop/evin1245/Foreman/setup.exe' 

How should I go about doing this install?

Thanks

---

### Post by SunnyRabbiera on 2008-03-12
you might not be able to, if your program is fully windows only then you should tell the developers about making cross platform development.
If this is an app created by people you know good luck, however if this is some big company making it then i am sorry.
you may want to run windows in a virtual machine to solve this

---

### Post by forrestcupp on 2008-03-12
you could try to 'cd' to the correct directory, then just type
```
wine ./setup.exe
```
Sometimes wine doesn't work right if you aren't already in the correct directory.

And you may need to install the Windows version of Mono, if the .NET program still doesn't work.

---

### Post by mebu99 on 2008-03-12
It did not work with doing the ```
wine /.setup.exe 
```  

I would like to stay with the Ubuntu O/S instead of running a V/M.

I will see about getting mono to work on the system.

THX.

---

### Post by mebu99 on 2008-03-12
I installed Mono -- no dice.

---

### Post by NorthernLights on 2008-03-12
I never had any luck with wine and .NET applications...

---

### Post by petercoh7 on 2008-03-12
When you run a VM you are staying within the ubuntu O/S.  That's why they call it a "virtual" machine.  I'm doing that now with my install.  There's a couple of Win apps that I want to run native to WinXP.  Try VirtualBox.

---

### Post by mebu99 on 2008-03-12
After messing with the wine install in Terminal I was able to get it to at least get the icon to show up on the desktop.  The application itself does not work, but slowing things are merging.  

I was to stay away from using a virtual machine and keep a pure ubuntu, so that way I stay with one pure O/S.  

VirtualBox looks to be a great application and I will probably use it for another box I have planned in the works.

---

