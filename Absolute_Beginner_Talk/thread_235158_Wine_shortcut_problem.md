---
title: "Wine shortcut problem"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by magicKA5 on 2006-08-12
I have installed wine and can run Svenska Spel poker game from it nicely....from console, but not from the shortcut icon.

The laucher has command "wine ~/.wine/drive_c/Casino/Poker/poker.exe"

That doesn't work, but if I go into the Poker folder and run "wine poker.exe" it works very well.

Why doesn't the laucher works?

I even tried "/usr/bin/wine ~/.wine/drive_c/Casino/Poker/poker.exe" but that doesn't work either.

Please help! :roll:

---

### Post by kebes on 2006-08-12
Shouldn't make a difference, but try:
wine /home/user/.wine/drive_c/Casino/Poker/poker.exe
or
wine $HOME/.wine/drive_c/Casino/Poker/poker.exe

Also, are you sure it's located in that folder, and not:
~/.wine/drive_c/Program Files/Casino/Poker/poker.exe

Maybe in the Application Link set the "working directory" to:
~/.wine/drive_c/Program Files/Casino/Poker/

Hope that helps.

---

### Post by magicKA5 on 2006-08-12
> **kebes said:**
> Shouldn't make a difference, but try:
wine /home/user/.wine/drive_c/Casino/Poker/poker.exe
or
wine $HOME/.wine/drive_c/Casino/Poker/poker.exe

Also, are you sure it's located in that folder, and not:
~/.wine/drive_c/Program Files/Casino/Poker/poker.exe

Maybe in the Application Link set the "working directory" to:
~/.wine/drive_c/Program Files/Casino/Poker/

Hope that helps.

Yea it's in that path. I changed that during the installation. I tried the other one also, but same result.

wine $HOME/.wine/drive_c/Casino/Poker/poker.exe just does nothing like other commands I tried. I just get a new row. ](*,) 

if I type "cd ~/.wine/drive_c/Casino/Poker/poker.exe;wine poker.exe" I can at least run it from console without having to be in the same folder, but I can't use that command in the launcher.

---

### Post by kebes on 2006-08-12
When you set up a shortcut icon ("Application Link") in KDE under the "Application" tab there is an "Advanced Options" button. There you can specify "run in console" and decide whether it should remain open after the program closes.

This might make the program work properly. It may also output some errors to the commandline to help you figure out why the shortcut is not working.

If you're using Gnome I assume there are similar options available.

---

### Post by magicKA5 on 2006-08-12
> **kebes said:**
> When you set up a shortcut icon ("Application Link") in KDE under the "Application" tab there is an "Advanced Options" button. There you can specify "run in console" and decide whether it should remain open after the program closes.

This might make the program work properly. It may also output some errors to the commandline to help you figure out why the shortcut is not working.

If you're using Gnome I assume there are similar options available.

yup...using gnome and there aren't any options like that.

Why won't the damn program run as a launcher?? When I am in the same folder I can start it without any problems. I am getting very confused

---

### Post by orb9220 on 2006-08-12
Its wine "C:\Program Files\Casino\Poker\poker.exe" ?

Since this is mine for running dvdshrink.

wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"

---

### Post by kebes on 2006-08-12
Sorry I'm not a Gnome user so it's hard for me to make any other suggestions.

Are you sure there is no "run in terminal" option. Looking at screenshots for setting up a "Gnome Launcher":
[http://icb.olin.edu/fall_03/mc/instructions/GNOME%20Panel%20Customization_files/dialog_createLauncher.jpg](http://icb.olin.edu/fall_03/mc/instructions/GNOME%20Panel%20Customization_files/dialog_createLauncher.jpg)
[http://linux.techteam.gr/docs/mandrake/9.2/images/gnome-launcher.png](http://linux.techteam.gr/docs/mandrake/9.2/images/gnome-launcher.png)

I see a "Run in terminal" option. Does setting this make it work. Also what happens if you change the "Type"? Is there a setting for "commandline" or "script" or something?

I hope I have not misunderstood the nature of your question.

---

### Post by kerry_s on 2006-08-12
I see that option and i use gnome. How did you create your launcher?
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=14227&stc=1&d=1155416362[/IMG]

---

### Post by magicKA5 on 2006-08-12
> **kerry_s said:**
> I see that option and i use gnome. How did you create your launcher?
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=14227&stc=1&d=1155416362[/IMG]

ok tried that, but don't work. The terminal window just flicker 1 time and disappears. Program doesn't start.

---

### Post by magicKA5 on 2006-08-12
> **kebes said:**
> Sorry I'm not a Gnome user so it's hard for me to make any other suggestions.

Are you sure there is no "run in terminal" option. Looking at screenshots for setting up a "Gnome Launcher":
[http://icb.olin.edu/fall_03/mc/instructions/GNOME%20Panel%20Customization_files/dialog_createLauncher.jpg](http://icb.olin.edu/fall_03/mc/instructions/GNOME%20Panel%20Customization_files/dialog_createLauncher.jpg)
[http://linux.techteam.gr/docs/mandrake/9.2/images/gnome-launcher.png](http://linux.techteam.gr/docs/mandrake/9.2/images/gnome-launcher.png)

I see a "Run in terminal" option. Does setting this make it work. Also what happens if you change the "Type"? Is there a setting for "commandline" or "script" or something?

I hope I have not misunderstood the nature of your question.

yea I found it =) it's so small. Still doesn't work though. Terminal window just flickers 1 time and disappears.

---

### Post by magicKA5 on 2006-08-12
> **orb9220 said:**
> Its wine "C:\Program Files\Casino\Poker\poker.exe" ?

Since this is mine for running dvdshrink.

wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"

no cause I changed the installation path, and the default path is C:\Casino\Svenska Spels Poker\

this problem feels a bit unreal. This isn't supposed to happen. Wine is goin against linux logic on this one ](*,)

try the program yourself: [http://download.poker.svenskaspel.se/svenskaspelpoker.exe](http://download.poker.svenskaspel.se/svenskaspelpoker.exe)

---

### Post by kebes on 2006-08-12
With the "run in terminal" option selected, is there an option (probably under the "Advanced" tab) like "Keep terminal open".

Or perhaps it is something you can set in "Gnome Terminal" itself. I think it's located at:

Edit > Current Profile > Title and Command > When command exists: Hold the terminal open

With this set, instead of opening for <1 second, hopefully you will see the output of the terminal and this will give you some hints?

---

### Post by kebes on 2006-08-12
> **magicKA5 said:**
> Wine is goin against linux logic on this one

According to the wine manual page:
[http://www.winehq.com/site/docs/wine](http://www.winehq.com/site/docs/wine)

You can specify the program in unix-style or windows-style. Thus you should be able to use the command:
wine C:\\Casino\\Poker\\poker.exe

---

### Post by magicKA5 on 2006-08-12
> **kebes said:**
> With the "run in terminal" option selected, is there an option (probably under the "Advanced" tab) like "Keep terminal open".

Or perhaps it is something you can set in "Gnome Terminal" itself. I think it's located at:

Edit > Current Profile > Title and Command > When command exists: Hold the terminal open

With this set, instead of opening for <1 second, hopefully you will see the output of the terminal and this will give you some hints?

no there isn't. try the program yourself and see. I am as stuck as you can be.

---

### Post by magicKA5 on 2006-08-12
> **kebes said:**
> According to the wine manual page:
[http://www.winehq.com/site/docs/wine](http://www.winehq.com/site/docs/wine)

You can specify the program in unix-style or windows-style. Thus you should be able to use the command:
wine C:\\Casino\\Poker\\poker.exe

tried that too. don't work. It gives same result as the others

---

### Post by diilbert on 2006-08-12
How about a shell script in your HOME directory with the following

```

#!/bin/bash
wine "c:/Casino/Poker/poker.exe"

```

That should do it... then symlink to the desktop

```

ln -s ~/SCRIPT_NAME ~/Desktop/Poker.desktop

```

That is what I would do anyway. ;)

---

### Post by magicKA5 on 2006-08-12
> **diilbert said:**
> How about a shell script in your HOME directory with the following

```

#!/bin/bash
wine "c:/Casino/Poker/poker.exe"

```

That should do it... then symlink to the desktop

```

ln -s ~/SCRIPT_NAME ~/Desktop/Poker.desktop

```

That is what I would do anyway. ;)

How do I do the shell script? It does only open up a texteditor. Please try the file yourself and install the program. Then you'll see that it simply won't start no matter what ya try

---

### Post by sup on 2006-09-28
this is not a gnome problem, it is a wine problem (it can run the program only if the executable is in working directory), but i do not know haw to fix it...

---

### Post by CatKiller on 2006-09-28
> **magicKA5 said:**
> I have installed wine and can run Svenska Spel poker game from it nicely....from console, but not from the shortcut icon.

The laucher has command "wine ~/.wine/drive_c/Casino/Poker/poker.exe"

That doesn't work, but if I go into the Poker folder and run "wine poker.exe" it works very well.

Why doesn't the laucher works?

I even tried "/usr/bin/wine ~/.wine/drive_c/Casino/Poker/poker.exe" but that doesn't work either.

Please help! :roll:

The command is wrong. I was running a Python script at startup, and I discovered this. The launcher doesn't understand that ~ means your Home directory. Change it to ```
wine /home/magicka5/.wine/drive_c/Casino/Poker/poker.exe
``` changing "magicka5" for whatever your actual user name is, and it should work fine.

---

### Post by apienk01 on 2007-11-11
I found a solution. Look here:
[http://ubuntuforums.org/showthread.php?t=609634]("http://ubuntuforums.org/showthread.php?t=609634")

---

### Post by sup on 2007-11-11
as I said in the linked thread, for me the solution was to create a script that frst changed directory to the the directory where the exe file is and then launch the windows application

---

