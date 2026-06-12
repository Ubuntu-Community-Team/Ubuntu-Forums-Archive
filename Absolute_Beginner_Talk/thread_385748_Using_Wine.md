---
title: "Using Wine"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Campingman on 2007-03-16
Could anybody point me in the right direction for instructions for using Wine, I can usually sort out most things but this is a complete mystery to me.  I have installed the latest version but cannot get it to do anything.  It shows up in the right click menu as run application with wine but when you click on it for a .exe file it does nothing.  I get no program icon in the applications list, if i try to run the wine program via the executable nothing happens.  I have looked on the Wine hq site and I am still non the wiser.  I am trying to get a newsreader program "Newsleecher" running.  
Any pointers would be great.
:confused: :confused:

---

### Post by eljalill on 2007-03-16
What happens if you navigate to the folder were your Newleecher_setup.exe (or  ehateve else it is called) is in in the terminal,
and then type
```
wine Newsleecher_setup.exe 
``` ?
Any error messages?

---

### Post by Campingman on 2007-03-16
I know this is really stupid of me but I cannot navigate to any directory using the terminal, I can get to home directory but the terminal is either on home or desktop, I have tried cd filesystem (where the folder is), no joy and I have tried to go to other directories with no joy.  keeps coming up with no such directory/file.  I have tried cd .. to move up one directory and that works fine.  
I need to get to where I can search all files / directories on pc, but cannot seem to get there, do I need to be logged on as root?

---

### Post by eljalill on 2007-03-16
For cd you do not need to be root.
Are you sure you typed the directory names correctly?
If you type cd and then start typing any folder name, and hit the tab-key after a few letters, the terminal will autocomplete. If nothing happens there are either many files that start that way, or no file that starts that way.

If you are looking for files or directories, you can use the "locate" command, which look for any (part of) a file/folder name.

---

### Post by jhenager on 2007-03-16
> **Campingman said:**
> I have tried cd filesystem (where the folder is), no joy and I have tried to go to other directories with no joy.  keeps coming up with no such directory/file.

Try cd /filesystem.

A space is required between cd and the folder, unlike DOS where you can type cd.. or cd/windows.

---

### Post by Campingman on 2007-03-16
This is hard work, probably easier to log into windows I reckon!  
I managed to navigate the right folder (thanks for the advice) using locate to find the path, I had to write in the full path and could not go to one folder and then find a new folder in that folder (if you see what I mean).  I can still not get Wine to run and get the following error, I know the file is in there but wine cannot find it
bob@bob-desktop:/stuff/windows$ wine nl_setup_betanew.exe
wine: could not load L"c:\\windows\\system32\\nl_setup_betanew.exe": Module not found
bob@bob-desktop:/stuff/windows$ wineserver: could not save registry branch to /home/bob/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/bob/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/bob/.wine/user.reg : Permission denied

Thanks

---

### Post by eljalill on 2007-03-16
I always get annoyed with rebooting, which is why I use wine.

If you want to knwo the content of any specific folder you are in, "ls" is a lot better than "locate". "ls -a" (mind the space) also pronts hidden files and folders.

If you are sure the file is there, and wine doesn't find it, there is most likely some spelling or so mistake. Maybe check with ls, what is actually there!

Also [http://frankscorner.org](http://frankscorner.org) goves additional information, on which programs run under wine, and you need to know when installing.

And finally here:
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
I found this useful list of commands. In case you need that... Someone here has the signature "the command line is your friend" or something like that. And it's true!

Does that help?

---

### Post by Campingman on 2007-03-16
The list of commands will be a great help, Thanks.  
It is a steep learning curve coming from Windows. 
As for Wine I think it may be a bad install, If i try to run the control centre I get an applet not found message, 
I will try to uninstall and reinstall the latest version (I did install one on top of the other which may not have been a good thing). I will have  a good read of Franks Corner later to see if I can sort it out.

Thanks

---

### Post by Campingman on 2007-03-16
I gave up and removed Wine in the end (life is just too short).  I could get a few programs to work but not the one I wanted.
Could somebody remind me why this is better than Windows?
After four hours I need some encouragement!
:confused:

---

### Post by Hero of Time on 2007-05-20
I know this topic is 2 months old, but it is something I'm working on aswell.

Campingman:
When you use Wine on a file, make sure you point to the current folder, else it will try to load files in the bin folder. So for starting Newsleecher setup, you type "wine ./nlsetup.exe" without quotes and the setup will start.

Now my problem is that I got 3.7 final working, only no supersearch. Upon start, I get a bug report about OLE error 80040154 (probably activex). I did enter my registration number, so that works. But when I try the latest version, or higher than 3.7 (all 3.8 and 3.9 versions) the installer won't start (I did get it working before, now it won't, stopping with a memory address fail or something). When I copied the newer version from my windows install folder to the .wine folder, I can run it (it hangs on the spash screen, ctrl+c a few times and it works) but I cannot enter my new serial. It will hang, using 100% cpu on one core and once it came out of it saying the serial couldn't be entered.

I want to enter my serial, because I bought it and want to use it to the fullest, I don't want to stay at trial version. If someone has any idea how to fix this, it's greatly appriciated. Also to get SS working. SS has a higher priority though, because I can use 3.7 final just fine.

---

### Post by Campingman on 2007-05-22
Thanks for the reply Hero In Time,
I had forgotten all about trying to get newsleecher to run in wine, I sort of gave up and went searching for a good linux newsreader to use.  I now use Klibido which IMHO is a pretty impressive newsreader.  Just as quick as newsleecher.  I do miss the search function every now and again but if it is desperate I can quickly boot into windows do a search then back to Klibido to download.(I have only had to do this once in three months)

---

