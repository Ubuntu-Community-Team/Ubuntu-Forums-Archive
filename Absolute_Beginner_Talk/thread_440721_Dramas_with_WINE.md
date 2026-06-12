---
title: "Dramas with WINE"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-05-11
Hi,
I've installed WINE - need it to run DAZ Studio, a 3D posing and modeling program with functionality missing in Blender - from the repositories via Synaptic... so I have the most recent version. I'm carefully following the Wineusr-guide.pdf instructions. However, I've run into a snag that is not addressed in the guide. When I try to 'Add Application' in the Applications tab, 'Program Files' and Windows folders are displayed. When I open the 'Program Files' tab, the only folder that I can see is the 'Common Files' folder - none of my other Windows program folders are visible.
What I might be missing, here?

---

### Post by jfinkels on 2007-05-12
> **Robynsveil said:**
> Hi,
I've installed WINE - need it to run DAZ Studio, a 3D posing and modeling program with functionality missing in Blender - from the repositories via Synaptic... so I have the most recent version. I'm carefully following the Wineusr-guide.pdf instructions. However, I've run into a snag that is not addressed in the guide. When I try to 'Add Application' in the Applications tab, 'Program Files' and Windows folders are displayed. When I open the 'Program Files' tab, the only folder that I can see is the 'Common Files' folder - none of my other Windows program folders are visible.
What I might be missing, here?

Maybe it's a permissions problem? Perhaps you installed the program as root or something...

Can you see the files in your ~/.wine/drive_c directory? What are the permissions when you do ```
ls -l
``` in the directory containing the program?

---

### Post by Nythain on 2007-05-12
silly question but you did install DAZ with wine right... you arennt just trying to use it to run a version installed on an xp partition???

---

### Post by Robynsveil on 2007-05-12
First, to answer Nythain:
> silly question but you did install DAZ with wine right... you arennt just trying to use it to run a version installed on an xp partition???
Not a silly question at all - can't assume anything when it comes to me... :(  - I've tried to do both - run it from a WindowsXP partition (after setting permissions for both the folder and the executable to 755)... that didn't work. Then, I tried to install it - the install barely started then quit, no messages or anything.

> **jfinkels said:**
> Maybe it's a permissions problem? Perhaps you installed the program as root or something...
Can you see the files in your ~/.wine/drive_c directory? What are the permissions when you do ```
ls -l
``` in the directory containing the program?
ls gave me:
> total 8
drwxr-xr-x 3 robyn robyn 4096 2007-03-16 23:08 Program Files
drwxr-xr-x 9 robyn robyn 4096 2007-03-16 23:08 windows


I can't help but feel I haven't installed it properly, maybe, because when I issue a
```
wine control
```
a blank form comes up and a dialog telling me it can't load any applets... and then it closes. I did install from Synaptic ... thanks for taking the time to look at this problem.

---

### Post by Enverex on 2007-05-12
It's "winecfg" not "wine control". Also check my sig for some useful info.

---

### Post by Robynsveil on 2007-05-14
I'm afraid I'm creating an amazing mess. To compound the problem, I've installed CodeWeaver's CrossOver Standard Linux. Using that I've managed to install Poser 6 by eFrontier into the:
/robyn/.cxoffice/Poser6/drive_c/Program Files/Curious Labs/Poser 6/
folder. However, there *is* a:
/robyn/.wine/drive_c/Program Files/
folder *as well* which contains only the Common Files folder. I have no idea about why I've got what amounts to 2 instances of WINE installed or if they conflict with each other. In any event, Poser  6 does *not* run: it comes up briefly - as did DAZ Studio, another 3D app, when I tried to install it in WINE - then terminates immediately.

In the winecfg applet I have the following settings in CrossOver:
[IMG]http://www.tightbytes.com/images/ubuntu/winecfgcx01.jpg[/IMG]
[IMG]http://www.tightbytes.com/images/ubuntu/winecfgcx02.jpg[/IMG]
[IMG]http://www.tightbytes.com/images/ubuntu/winecfgcx03.jpg[/IMG]
[IMG]http://www.tightbytes.com/images/ubuntu/winecfgcx04.jpg[/IMG]
[IMG]http://www.tightbytes.com/images/ubuntu/winecfgcx05.jpg[/IMG]

Colour me puzzled... and not at all sure how to proceed... thanks for looking at this mess. :confused:

---

### Post by Enverex on 2007-05-14
I don't quite see the problem. You've pointed out you have Wine and Crossover installed. Crossover stuff is in the crossover fold and Wine stuff is in the Wine folder. You run stuff you installed in Crossover with the crossover program (whatever that is) and the wine programs with wine...

---

### Post by Robynsveil on 2007-05-14
> **Enverex said:**
> I don't quite see the problem. You've pointed out you have Wine and Crossover installed. Crossover stuff is in the crossover fold and Wine stuff is in the Wine folder. You run stuff you installed in Crossover with the crossover program (whatever that is) and the wine programs with wine...
Well, according the the CodeWeavers site, CrossOver is WINE with a bit more functionality... it's WINE extended, and with a GUI. CrossOver uses a metaphor they call 'bottles' in which each app has all the supporting files you'd expect to see in the \windows\system32 folder and such.

In any event, Poser 6 only comes up briefly - basically just starting to load - and then exists. Very frustrating...

---

### Post by Enverex on 2007-05-15
> **Robynsveil said:**
> Well, according the the CodeWeavers site, CrossOver is WINE with a bit more functionality... it's WINE extended, and with a GUI. CrossOver uses a metaphor they call 'bottles' in which each app has all the supporting files you'd expect to see in the \windows\system32 folder and such.

In any event, Poser 6 only comes up briefly - basically just starting to load - and then exists. Very frustrating...

Not really, it's just... different to Wine, tweaked for certain functionality basically (where as Wine doesn't care what currently works and doesn't work as long as it's progressing towards its final goal, Crossover tries to make certain apps work even if it's hacky methods [not a problem for the user, but harder to code upon]). It's still a different thing that goes in a different place.

---

### Post by Robynsveil on 2007-05-15
Crossover does not list Poser 6 (a program very much like DAZ Studio, but more expensive and with more features) as a supported program. However, I was able to install Poser 6 using Crossover. Poser 6 now is accessible as an Applications menu item - and so is Crossover in its own Application menu tier. Poser 6 *had* installed completely - no dramas there. However, when I try to run it from the Applications-> Windows Applications-> Programs-> Curious Labs-> Poser 6-> Poser menu item, it brings up a blank green window, the Poser menu items appear briefly at the top of this menu for a moment, and then the screen goes completely blank again, the the program exists. If I drill down to it in Nautilus, as in:

```
robyn/.cxoffice/Poser6/drive_c/Program Files/Curious Labs/Poser 6
```

it does a virus-scan, then brings up the Codeweaver trial version dialog. When I select Register Later, it displays a full-screen blank window with the Poser menu at the top for about a second, and then exists.
Both of these attempts are done on a Crossover-installed version of Linux. As in, it installed fine. However, it won't run. 
BTW, the version of WINE for Crossover is .9.17... the version I downloaded and installed via Synaptic is .9.37.

Oh, and another thing I tried... just to see if I'd missed something. In the winecfg dialog, I tried to add the Windows-installed Poser 6. I navigated over to it by getting on the /media/NTFS_Programs/Program Files/Curious Labs/Poser 6 folder (this is on the NTFS partition - the Windows install, IOW) and selected Poser.exe. Well, winecfg spat the dummy, and terminal returned the following messages:
> 
winecfg
X Error of failed request:  BadPixmap (invalid Pixmap parameter)
  Major opcode of failed request:  54 (X_FreePixmap)
  Resource id in failed request:  0x3800873
  Serial number of failed request:  12624
  Current serial number in output stream:  12671

Hmmmm... methinks this might be an X-system issue, perhaps? My Window Manager in Ubuntu 7.04 Linux is Metacity, the default Gnome window manager. I do have Beryl installed, but disabled it in the interest of creating as vanilla a graphics environment as possible.

I kinda think it might actually be worth my while to install Edgy Eft again and see if Crossover has a better chance of running. Or, should I just forget Crossover as being an extra layer of complexity and simply try to get this running in WINE alone?

Thanks again for responding...

---

### Post by Enverex on 2007-05-15
Leave crossover alone for now. Also, adding apps to winecfg does nothing, it's not like Cedega where you add things like that. You need to install Poser in Wine and then try and run it, you don't need to add apps in winecfg, that's for using customised DLL overrides per exe.

---

### Post by Robynsveil on 2007-05-15
> **Enverex said:**
> Leave crossover alone for now. Also, adding apps to winecfg does nothing, it's not like Cedega where you add things like that. You need to install Poser in Wine and then try and run it, you don't need to add apps in winecfg, that's for using customised DLL overrides per exe.
Thanks for your patience, Enverex - I'm going to follow the WINE process to the letter.

First off, I've uninstalled Crossover completely, and am studying the WINE documentation in WineHQ. In winecfg, the CDROM is part of the drives group - that's purely for drives, not paths, correct?

So, here are my settings:
[IMG]http://www.tightbytes.com/images/ubuntu/winecfg01.jpg[/IMG]
[IMG]http://www.tightbytes.com/images/ubuntu/winecfg02.jpg[/IMG]
[IMG]http://www.tightbytes.com/images/ubuntu/winecfg03.jpg[/IMG]
[IMG]http://www.tightbytes.com/images/ubuntu/winecfg04.jpg[/IMG]
[IMG]http://www.tightbytes.com/images/ubuntu/winecfg05.jpg[/IMG]

Anyway, going through the Guide, I ran into the regedit section, where it says:
> These files are automatically created by wineprefixcreate the first time you use Wine. [COLOR="Red"]**A set of global settings is stored in the c:\windows\inf\wine.inf and is processed by the rundll32.exe program**[/COLOR]. The first time you run Wine the wine.inf file gets processed to populate the initial registry. For more details, check out the wineprefixcreate script to see how it's all done. After updating Wine, wineprefixcreate  can also be used to update the default registry entries.

I browsed the c:\windows\inf folder - there *is* no wine.inf file. So, no paths are being set in the registry, I would assume. I ran wineprefixcreate manually from Terminal, and got:
> robyn@Flight:~$ wineprefixcreate
/home/robyn/.wine updated successfully.


...and yet, still no wine.inf file in the c:\windows\inf (actually: /media/NTFS_Programs/windows/inf) folder - this is looking for it in gedit...

Can't help but feel I'm missing something crucial... :confused:

Thanks again, Enverex for all your help!

---

### Post by Enverex on 2007-05-16
It's not crucial, ignore it. 

For the drives Tab, remove EVERYTHING other than C. Then add a new one and point it to your CD drive (and set the type to CD drive). Adding lots of drives like that is just going to make life difficult.

---

### Post by Robynsveil on 2007-05-16
Enverex, I've done as you recommended... and thank you for the pointers.

Subsequently, I've entered the following:
> robyn@Flight:~$ wine /media/cdrom0/autorun.exe

which gave me:
> Warning: could not find DOS drive for current working directory '/home/robyn', starting in the Windows directory.
fixme:font:WineEngRemoveFontResourceEx :stub
err:ntdll:RtlpWaitForCriticalSection section 0x7bc833c4 "loader.c: loader_section" wait timed out in thread 0009, blocked by 000e, retrying (60 sec)
fixme:win:LockWindowUpdate (0x9002a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
err:ntdll:RtlpWaitForCriticalSection section 0x7bc833c4 "loader.c: loader_section" wait timed out in thread 0009, blocked by 000e, retrying (60 sec)
wine: Critical section 7bc833c4 wait failed at address 0x7bc303b0 (thread 0009), starting debugger...
Unhandled exception: wait failed on critical section 0x7bc833c4
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc303b0
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
00000011 
        00000012    0
0000000a 
        0000000c    0
        0000000b    0
robyn@Flight:~$ err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink

I must have typed the command in improperly - did I forget the tilde ( ~ )? Anyway, regardless, the install *did* run, but with the above error messages in Terminal.
Then, when I typed in:
> robyn@Flight:~$ wine "c:\\Program Files\\Curious Labs\\Poser 6\\poser.exe"

which according to [http://www.winehq.org/site/docs/wineusr-guide/running-wine]("http://www.winehq.org/site/docs/wineusr-guide/running-wine")
 is the correct way to invoke the program from the command-line... it gave me:
> Warning: could not find DOS drive for current working directory '/home/robyn', starting in the Windows directory.
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\Curious Labs\\Poser 6\\clothlib.dll") not found
err:module:import_dll Library clothlib.dll (which is needed by L"C:\\Program Files\\Curious Labs\\Poser 6\\poser.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\Curious Labs\\Poser 6\\poser.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\Program Files\\Curious Labs\\Poser 6\\poser.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Curious Labs\\Poser 6\\poser.exe" failed, status c0000135
I'm pretty sure I can find these missing .dlls on the NTFS Windows install partition - my questions are:
1) do I copy the .dlls from their original home to a folder in the 
/home/robyn/.wine/drive_c/ <whichever_folder_and_subfolder_corresponds_to_the_original_location>? or do I
2) edit the path - not really clear on how to do this: I understand it has something to do with export - so that the .dlls are exposed to WINE?
Or have I left out another step altogether? I can't, from the Guide, see where I might have, but it wouldn't surprise me.

Thanks again for responding, and for your patience!!

---

### Post by Enverex on 2007-05-16
Put the MSVC* dll files into windows/system32 and then it should work (the poser DLL files fail because it can't find the other DLLs).

On a side note, always run the setup directly, not the autorun.

---

### Post by Robynsveil on 2007-05-17
> **Enverex said:**
> Put the MSVC* dll files into windows/system32 and then it should work (the poser DLL files fail because it can't find the other DLLs).
On a side note, always run the setup directly, not the autorun.

Okay, will do (re: setup.exe).

Now, I assumed that by "windows/system32" you meant the one in my Linux /home/robyn/.wine/ folder... so I drilled down to the actual *Windows* /system32 folder which contained the original files - there were about 8 - but I only copied the two that had been mentioned as missing: MSVCP60.dll and MSVCIRT.dll. Should I copy the other 6?

I went ahead and launched Poser 6 from the Applications-> Wine-> Programs-> Curious Labs-> Poser 6-> Poser menu... and lo and behold, it Worked! Astonished, gratified, amazed and delighted all intermingled... and Enverex, I'm deeply indebted to you! Thank you so much for holding my hand through all this. The last reason for booting to Windows just went down the gurgler  \\:D/ wooHOO!

No question, the program has a few new wrinkles - it's not that well-written a program to begin with, and running it in Linux brings to the surface some of its more annoying foibles, but it's all there is for this sort of thing in my price range, so I'll just have to deal with it.

BTW, my avatar was created in Poser 6, as was this:
[IMG]http://www.tightbytes.com/images/FPsm.jpg[/IMG]

3D art is a thriving business. I was hoping to get back to my original project - and the whole reason I went to Linux in the first place, Blender 3D object development - which was to create fashions for Poser 3D characters, sold on sites like [http://www.renderosity.com]("http://www.renderosity.com") - you've just helped me and a lot of other Poser users tremendously in that regard. 
Thank you from the bottom of my heart!

Cheers,
Robyn

---

### Post by Enverex on 2007-05-17
No problem.

NEVER copy DLLs unless something specifically requests them else you are likely to break Wine.

---

### Post by whitefort on 2007-05-17
Edited out of existence by the author!

---

### Post by Robynsveil on 2007-05-19
> **Robynsveil said:**
> Hi,
I've installed WINE - need it to run DAZ Studio, a 3D posing and modeling program with functionality missing in Blender - from the repositories via Synaptic... so I have the most recent version.

For those of you who *would* like to run DAZ Studio in Linux via WINE, I've still not been able to accomplish that... and to be quite truthful, have kinda cooled off on the idea. My understanding is (from reading the DAZ Studio forums) that DAZ Studio runs a bit dodgy even *if* you do manage to get it installed, so I've kinda given up on trying to make it work, particularly as I do have Poser 6 - a far more capable, flexible program of the same persuasion - working properly.

Well, fairly well, anyway. There are a few quirks, but you'll find that you can work around most of them, really. The biggest challenge is adding runtimes: the software seems to either have a problem with capitalization or NTFS folder structure, but it doesn't see the poser.exe files and therefore won't add an NTFS-based runtime to your directories (or libraries, or whatever ya wanna call 'em).

Other than that, no show-stoppers. I once read that entering values using the keyboard rather that using the scroll-thingies caused Linux to freeze, but they seem to have resolved that: I haven't encountered that issue at all. The other rather annoying issue is that if you happen to be doing anything *else* in addition to Poser, the dialogs or viewports or whatever they're called insist on being on top, so you have to kinda move them to one side.

I'll be using Poser a fair bit, and keep you posted on how I go...

---

### Post by Cannaregio on 2007-09-15
I know that poser 6 is not daz studio, but I just want to point out that I finally managed (after more than seven months attempts) to run poser 6 through wine.

These are the fundamental steps:

Copy some dlls into wine's system 32: msvcp60.dll, msvcirt.dll, and whatever else wine is asking for 

Always run ```
wine Poser.exe
``` from inside wine's  own poser 6 directory, so that you can see all error messages

Alternatively use the more verbose 
```
WINEDEBUG=warn+all wine poser.exe
```

Previously run winecfg and chose "graphic-->emulate a virtual desktop --> 1024*768" (say)

Now I have Poser 6 up and running

Launcher is 

```
env WINEPREFIX="/home/cannaregio/.wine" wine "C:\Program Files\Curious Labs\Poser 6\Poser.exe"
```

Rendering is perfect, but some complex figures seem to be missing some parts (half a face for instance) while pre-viewing inside Poser before rendering. 
I wonder why.
**_Should anyone have a solution I would be grateful. _** 
I'll try installing SP3 later.
-----------------------------------
SOLUTION FOUND (5/10/2007)
Updated graphic card drivers migrating to gutsy beta: new nvidia solved the problem.
Now I have both quick rendering and quich posing :-)
-----------------------------------

A very happy winerposer :-)

---

### Post by Cannaregio on 2007-10-05
See above.
Works flawlessly with Poser 7 as well.
Rendering is extremely quick if compared with windows XP.

:)

---

