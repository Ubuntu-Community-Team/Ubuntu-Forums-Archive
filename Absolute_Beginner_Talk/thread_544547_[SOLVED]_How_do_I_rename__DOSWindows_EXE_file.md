---
title: "[SOLVED] How do I rename  DOS/Windows EXE file ??"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-06
When I run this program I get this message I have told it to run with WINE and had to use the Custom Command to add WINE - is there no way of getting it to do this automatically??

[IMG]http://i3.tinypic.com/44j7edk.jpg[/IMG]

---

### Post by igknighted on 2007-09-06
In the command line, type "wine filename.exe" to try and run it.

---

### Post by Terl on 2007-09-06
> **chrome307 said:**
> When I run this program I get this message I have told it to run with WINE and had to use the Custom Command to add WINE - is there no way of getting it to do this automatically??

[IMG]http://i3.tinypic.com/44j7edk.jpg[/IMG]

Do what automatically?  If you want to install the windows program on Linux, no.  If you want to install wine and then use it to run your .exe then it may work.  Tons of info on Wine over at:  [Wine HQ]("http://www.winehq.org/")

---

### Post by WebSiteGuru on 2007-09-06
> **Terl said:**
> Do what automatically?  If you want to install the windows program on Linux, no.  If you want to install wine and then use it to run your .exe then it may work.  Tons of info on Wine over at:  [Wine HQ]("http://www.winehq.org/")

My question is: Is there a way to run .exe file automatically? I would like to do that instead of right click and tell it to run with wine.

---

### Post by diatribe on 2007-09-06
you could set up a shell script to execute wine whatever.exe and put that in your bin directory I guess

---

### Post by chrome307 on 2007-09-06
[IMG]http://i1.tinypic.com/66er3op.jpg[/IMG]

---

### Post by Terl on 2007-09-06
> **WebSiteGuru said:**
> My question is: Is there a way to run .exe file automatically? I would like to do that instead of right click and tell it to run with wine.

I do not believe so.  I am not positive, I am at work.  I just use the winefile command and go from there.

I did do some checking into the program you are trying to use.  Have you checked to make sure it runs in Wine?  They have a fairly comprehensive database at the link I had above.

---

### Post by zipperback on 2007-09-06
> **WebSiteGuru said:**
> My question is: Is there a way to run .exe file automatically? I would like to do that instead of right click and tell it to run with wine.

Sure install windows, of course that is no promise that the application will run correctly either.

But seriously.

From command line:   wine filename.exe

Or if you want to just click the icon for filename.exe do this.

Right click filename.exe, select properties, select Open With, then select Wine, then click Close.

You should then be able just click the icon and it should run.

For the record, I didn't test this because I don't use Wine, but it should work.
:popcorn:
- Jack
- zipperback

---

### Post by chrome307 on 2007-09-06
[IMG]http://i13.tinypic.com/4qs6c7s.jpg[/IMG]

---

### Post by vanadium on 2007-09-06
You can configure your system this way that it automatically "opens" an exe with wine in the usual way. Right-click an exe, and on the "Open with" tab, you can specify wine as the "application" to open an exe. Next time, the exe will just run on double click.

You can put Windows programs in the Applications menu as another possibility for conveniently running Windows applications under Linux.

---

### Post by chrome307 on 2007-09-06
If you look at one of the screenshots posted earlier, you will see that I have already tried this but it fails to open so I have do it manually.

---

### Post by WebSiteGuru on 2007-09-06
> **zipperback said:**
> Sure install windows, of course that is no promise that the application will run correctly either.

LMAOL! Now that's funny. ;) :lolflag:

> **zipperback said:**
> But seriously.

From command line:   wine filename.exe

Or if you want to just click the icon for filename.exe do this.

Right click filename.exe, select properties, select Open With, then select Wine, then click Close.

You should then be able just click the icon and it should run.

For the record, I didn't test this because I don't use Wine, but it should work.
:popcorn:
- Jack
- zipperback


Yea! But that is only after you installed the program under wine. (correct me if I am worng on this)

I am talking about having wine reconized .exe file and run it to install the program that had not been installed in wine yet.

---

### Post by chrome307 on 2007-09-06
It's not an application that requires installation - the contents are all included in the folder and just require me to 'double-click' on the EXE to start it.

---

### Post by WebSiteGuru on 2007-09-06
> **vanadium said:**
> You can configure your system this way that it automatically "opens" an exe with wine in the usual way. Right-click an exe, and on the "Open with" tab, you can specify wine as the "application" to open an exe. Next time, the exe will just run on double click.

You can put Windows programs in the Applications menu as another possibility for conveniently running Windows applications under Linux.

Hmm, I did not see that before, maybe I missed look at it. I will look the next time around. ;)

---

### Post by Nythain on 2007-09-06
i dont think you all are understanding the posters question.
the program works, thats not the problem.
they dont like the hassle of havening to use teh right click "open with wine" or whatever its called option.
and aparently everytime they try to, what looks like, assosiate exe's with wine, it doesnt stick... ubuntu still dosnt know to open with wine by default.
so thier question would be more along the lines of

Is there a way / how would one go about getting ubuntu/gnome to open ALL .exe's with wine by default when clicked on... since typing and right clicking is such a waste of 5 seconds and 5 calories.

The answer, i dont know, i dont use gnome, i used to use kde, now i use fluxbox/command line, so i always type my commands. Im sure there's an answer somewhere out there, or a possibility involving shell scripting or whatnot, but seriously, is it really worth the effort to save a few seconds???

---

### Post by WebSiteGuru on 2007-09-06
> **Nythain said:**
> i dont think you all are understanding the posters question.
the program works, thats not the problem.
they dont like the hassle of havening to use teh right click "open with wine" or whatever its called option.
and aparently everytime they try to, what looks like, assosiate exe's with wine, it doesnt stick... ubuntu still dosnt know to open with wine by default.

so thier question would be more along the lines of
Is there a way / how would one go about getting ubuntu/gnome to open ALL .exe's with wine by default when clicked on... since typing and right clicking is such a waste of 5 seconds and 5 calories.

BINGO!

> **Nythain said:**
> The answer, i dont know, i dont use gnome, i used to use kde, now i use fluxbox/command line, so i always type my commands. Im sure there's an answer somewhere out there, or a possibility involving shell scripting or whatnot, but seriously, is it really worth the effort to save a few seconds???

It's not the time saving issue. (at least for me) It's the automated preference, that's all. :D

---

### Post by igknighted on 2007-09-06
Easiest way is to put the terminal command in a script that is executable and double-clicking that to launch the program.  You should be able to set a custom icon for that and everything.  You could probably also right a .desktop file for it, but I think that would be overkill.

---

### Post by chrome307 on 2007-09-06
I think that's most probably a stumbling block for most new users to Ubuntu migrating from a Windows environment.

As I'm unable to do so - I guess I'll have to stick to having to navigate my way through each time.

---

### Post by igknighted on 2007-09-06
> **chrome307 said:**
> I think that's most probably a stumbling block for most new users to Ubuntu migrating from a Windows environment.

As I'm unable to do so - I guess I'll have to stick to having to navigate my way through each time.

```
#!/bin/bash
wine program.exe
```
then save the file as whatever you want, right click it -> properties and set it as executable in the permissions tab.  I think in the properties GUI you can also set the icon as well.  Then you should be able to double-click the file and run the program.

I have to 100% disagree with you though, being able to run windows apps as well as the linux native apps is a luxury.  The fact that they run at all is a bonus, so if it isn't as simple as possible you really don't have any right to complain.

---

### Post by asmoore82 on 2007-09-06
> **chrome307 said:**
> I think that's most probably a stumbling block for most new users to Ubuntu migrating from a Windows environment.

As I'm unable to do so - I guess I'll have to stick to having to navigate my way through each time.

as the error dialog says, it is a **security** precaution.

creating a "custom app lancher" is the proper way to handle the situation ...
these are the desktop icons that launch counter-strike/steam via Wine for me ...

```
**asmoore@asmoore-laptop:~$** cd Desktop/
**asmoore@asmoore-laptop:~/Desktop$** ls *.desktop
Counter Strike 1.6 Non Steam.desktop  Unreal Tournament 2004 Demo.desktop
Steam.desktop                         VirtualBox OSE.desktop
**asmoore@asmoore-laptop:~/Desktop$** cat Counter\ Strike\ 1.6\ Non\ Steam.desktop 
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Counter Strike 1.6 Non Steam
Exec=wine "C:\\Program Files\\Valve\\hl.exe" -nomaster -game cstrike +localinfo mm_gamedll dlls/zbotcz.dll
Type=Application
Comment=Counter Strike 1.6 Non Steam - Cumulative patch V21
Path=/home/asmoore/.wine/dosdevices/c:/Program Files/Valve
Icon=/home/asmoore/games/wine-cstrike/drive_c/Program Files/Valve/cstrike/cstrike.ico
GenericName=
GenericName[en_US]=
**asmoore@asmoore-laptop:~/Desktop$** cat Steam.desktop 
[Desktop Entry]
Name=Steam
Exec=env WINEPREFIX="/home/asmoore/.wine" wine "C:\\Program Files\\Valve\\Steam\\steam.exe" 
Type=Application
Path=/home/asmoore/.wine/dosdevices/c:/Program Files/Valve/Steam
Icon=8cd3_steam.0
**asmoore@asmoore-laptop:~/Desktop$** cat Unreal\ Tournament\ 2004\ Demo.desktop 

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Name[en_US]=Unreal Tournament 2004 Demo
Exec=/home/asmoore/ut2004demo/ut2004-demo
Icon[en_US]=/home/asmoore/ut2004demo/ut2004.xpm
Name=Unreal Tournament 2004 Demo
Icon=/home/asmoore/ut2004demo/ut2004.xpm
**asmoore@asmoore-laptop:~/Desktop$** ls *.desktop
Counter Strike 1.6 Non Steam.desktop  Unreal Tournament 2004 Demo.desktop
Steam.desktop                         VirtualBox OSE.desktop
```

note how they are seamlessly integrated like the native Linux Apps UT2004/VirtualBox

---

