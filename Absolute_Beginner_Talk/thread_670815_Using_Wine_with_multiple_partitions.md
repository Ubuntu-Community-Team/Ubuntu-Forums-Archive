---
title: "Using Wine with multiple partitions"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by The Realms of Gold on 2008-01-17
Here's an interesting newbie question for you.  I'm running Ubuntu and just installed Wine via the Package Manager.  It doesn't like my partitions.

My hard drive is partitioned in three parts:  the first (C:) for all my data and most Windows programs, the second (D:) for Windows itself, and the third (E:) for Linux.  Wine apparently isn't happy with the fact that Windows isn't installed on the C drive, nor that the programs I'm trying to access with it are installed on the D drive.

Can anyone tell me how to configure Wine so it can access programs on the C drive?

---

### Post by The Realms of Gold on 2008-01-17
I guess I should clarify:  when drive C in the Wine configuration is set to /media/sda1 (which is the proper partition), Wine can't find the executable I'm trying to run.  I also came across the error message that Wine couldn't find the C:\Windows\System32 directory, though I don't remember how I got that.  Probably when D: was set to /media/sda5, which is the D: partition.

What I really need is a way to get Wine to believe Windows isn't on C:.  Wine programmers, are you listening?  :-)

---

### Post by peitschie on 2008-01-17
What do you mean by "wine isn't very happy..."?  

Just to clarify (as it confused me for ages too), applications you want to run on wine often need to be installed under wine.  Wine has no access to the windows registry, and so many programs will have issues unless they were able to set up all their registry keys etc.

---

### Post by Rhubarb on 2008-01-17
wine doesn't work like that.
wine allows you to run programs that are typically installed at ~/.wine/drive_c/
You can run some programs that are outside this directory.

Can you please explain in more detail what you are trying to achieve?

---

### Post by The Realms of Gold on 2008-01-18
Sorry.  I'm trying to run a program located on the C: partition (the one Windows is not on).  The file location is C:\Finale 2007\FINALE.EXE .

In Terminal, when I type

```
wine "c:\finale 2007\finale.exe"
```

I get this error:

```
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\finale 2007\\icuuc36.dll") not found
err:module:import_dll Library icuuc36.dll (which is needed by L"C:\\finale 2007\\finale.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\finale 2007\\finale.exe" failed, status c0000135
```

---

### Post by peitschie on 2008-01-18
It sounds like you don't really understand what wine is yet :)

Have a read through these links (just the intro parts mainly) and see if that helps you a bit:
[http://www.winehq.org/site/about](http://www.winehq.org/site/about)
[http://www.winehq.org/site/myths](http://www.winehq.org/site/myths)

Setup instructions for wine can be found here:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Basically, you can't use wine to run an existing install of windows!  Wine puts its own version of several very important libraries in place, and trying to run from a currently install of Windows will often not work!

Your best bet is to move reconfigure the Wine C drive to somewhere else, and then install finale on wine under linux.  This will give you your best chance of making it work

---

### Post by The Realms of Gold on 2008-01-19
*reads a lot of stuff*

So let me get this straight -- Wine isn't designed to run applications that have already been installed under Windows?  You **have to** install them through Wine under Linux?  The answer to that question isn't directly answered anywhere that I saw.

If that is the case, why can't Wine handle the program when it's already installed?  Even if Wine uses its own resources instead of those of Windows, the program files themselves are the same.  Seems kind of silly :-)

Furthermore, is there any workaround for Wine's expectation that Windows is on Drive C?  If I have to go repartition and reinstall Windows, I'll do it, but ugh.

---

### Post by asmoore82 on 2008-01-19
Also there are no "Drive Letters" in Linux;
so the earlier example of wine "C:\..." could never work "out-of-the-box."

But exactly the same thing *will* work after for stuff that has been installed
through WINE to its "fake c drive"

---

### Post by asmoore82 on 2008-01-19
forgive me if this seems rude; but this is also an excellent read:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

In a nutshell, your Operating System is a means to an end(programs);
and If you simply must run a multitude of Windows apps most of the time,
Windows should be your Operating System. If you can replace those functionalities
with native Linux apps except for one or two that also happen to work well with WINE,
then Linux could serve you well as your Operating System.

---

### Post by bethebunny on 2008-01-19
The program files are not the only thing required by windows to run them. Windows isn't as user friendly in this way as linux, one of the many reasons I prefer linux. Most windows programs install several registries to keep track of specific information, and sometimes will install other small pieces of code that Windows runs in the background all the time or when the program runs to make it work. Most of these measures are designed for security, some of them are designed so that multiple programs using the same code can store that code in one place to be referenced by all, saving space.

Regardless of the how or why, almost all windows programs require that the program actually be installed using the regular installation process in that particular API in order to run it. There is always the chance that your version of Wine has the correct registries, etc. already installed for a program on another hard drive, in which case it is likely that you could run it straight out of a windows install without ever installing it through wine, but this is rarely true. What you *can* do is set your C drive in Wine to be another partition or another drive, in which case all program data will be stored to that drive.

Also, Linux doesn't support Windows drive lettering, or spaces in the path. In order to get windows spaces into a path, you need to cancel them. Backslashes also don't work, you need to use forward slashes. The path would be:

wine [mountpoint]/finale\ 2007/finale.exe

Good luck!

---

### Post by Sinkingships7 on 2008-01-19
my opinion: install windows xp using VirtualBox (search for it in the Add/Remove Programs under Applications). of course, you can only do this if you have a CD or ISO image of windows. i just got mine set up about an hour ago, and it's flawless.

if you don't know what a virtual machine is, google it and read up.

---

### Post by The Realms of Gold on 2008-01-23
Well, after reading a whole lot of very helpful stuff, I went and installed Finale through Wine and, lo and behold, it works.  Incredible.  One step closer to completely replacing Windows!  :-)  Thanks everyone.

---

### Post by The Realms of Gold on 2008-01-23
> **Sinkingships7 said:**
> my opinion: install windows xp using VirtualBox (search for it in the Add/Remove Programs under Applications).

I didn't want to use a virtual machine or an emulator because of the system resources required.  Finale is huge and very poorly programmed, and it uses immense amounts of memory and processing power.  So Wine is really the best option.  Thanks for the suggestion though!

---

