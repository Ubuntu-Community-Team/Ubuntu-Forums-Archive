---
title: "Can't get flight gear to work"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-07-09
When I click on it in the menu it pops up in the task bar for a second, then disappears without opening. Does anyone know how to fix this. Thanks

---

### Post by KIAaze on 2007-07-10
Run it from a terminal and post all its output here.

To find out the command used to launch it, do this:
-right-click on applications
-select "edit menus"
-search for the shortcut to flightgear in games
-right-click->properties

The command should be listed in the properties window.

edit:
This seems to be the command used to launch the game:
```
/usr/games/fgfs
```
Run it from a terminal and you should get some rather explicit error messages hopefully.

---

### Post by swoll1980 on 2007-07-10
> **KIAaze said:**
> Run it from a terminal and post all its output here.

To find out the command used to launch it, do this:
-right-click on applications
-select "edit menus"
-search for the shortcut to flightgear in games
-right-click->properties

The command should be listed in the properties window.

edit:
This seems to be the command used to launch the game:
```
/usr/games/fgfs
```
Run it from a terminal and you should get some rather explicit error messages hopefully.

Error reading properties: 
Failed to open file
 at /home/nolan/.fgfs/autosave.xml
 (reported by SimGear XML Parser)
DRM_I830_CMDBUFFER: -22
DRM_I830_CMDBUFFER: -22
DRM_I830_CMDBUFFER: -22

---

### Post by KIAaze on 2007-07-10
Can you check if that file "/home/nolan/.fgfs/autosave.xml" exists and has the necessary permissions?

You can either try to find it and open it (it's an XML file, so it should be readable in Firefox) through the file manager or run this command:
```
ls -l /home/nolan/.fgfs/autosave.xml
```

It should list the file if it exists and display its permissions in an "rwxrwxrwx user group" format.

I found this by googling for parts of your error message:
[http://ubuntuforums.org/showthread.php?t=307143]("http://ubuntuforums.org/showthread.php?t=307143")
[http://forums.pcbsd.org/viewtopic.php?p=53901&sid=b0d869d20e50b037df3eabe7c4fd6558]("http://forums.pcbsd.org/viewtopic.php?p=53901&sid=b0d869d20e50b037df3eabe7c4fd6558")

No clear solution right now, but it seems that it's looking for the file in the wrong place.
Try to find the autosave.xml file in /usr/games if it isn't in your home directory.

---

### Post by swoll1980 on 2007-07-10
> **KIAaze said:**
> Can you check if that file "/home/nolan/.fgfs/autosave.xml" exists and has the necessary permissions?

You can either try to find it and open it (it's an XML file, so it should be readable in Firefox) through the file manager or run this command:
```
ls -l /home/nolan/.fgfs/autosave.xml
```

It should list the file if it exists and display its permissions in an "rwxrwxrwx user group" format.

IT does not exist. is there any way do fix this iv tried reinstalling it twice so I no that not going to work

---

### Post by KIAaze on 2007-07-10
I edited my previous post and added two links I found.
I'm still investigating...

---

### Post by swoll1980 on 2007-07-10
Thanks for your help I'v been doing some research my self, but don't understand half the crap there saying. the files not in usr/games either so i'll google with ya

---

### Post by KIAaze on 2007-07-10
Oh, and before I forget, try this:
```
mkdir -p /home/nolan/.fgfs/
touch /home/nolan/.fgfs/autosave.xml
```

It will just create an empty autosave file, but it might work...
Unfortunately, I'm not on my PC now, so I can't even try installing the game to see for myself.

---

### Post by swoll1980 on 2007-07-10
Tried that. No luck. Good idea though.

---

### Post by KIAaze on 2007-07-11
Sory if I can't really help you on this one.
Maybe you should try [contacting the flightgear people directly]("http://www.flightgear.org/mail.html").

A few ideas that probably won't be the solution, but might help...:

[LIST]
[*]I noticed that installing flightgear creates all those binaries (I just looked at the contents of the .deb package):
> al-info  est-epsilon  fgfs  fgjs  gl-info  js_demo  metar  terrasync  yasim
Maybe one of them is for initialization, altough I doubt it. (otherwise, it should be written somewhere)

[*]Try running these two commands and see if they return any errors:
```
al-info
gl-info

```

[*]You could try installing from source too, altough I doubt it will solve the problem...

The source code is available here:
[http://www.flightgear.org/Downloads/source.shtml]("http://www.flightgear.org/Downloads/source.shtml")
You'll need the source code and data package.

The libraries can be installed through Synaptic.
If you have already installed flightgear through synaptic, that won't probably even be necessary and you could use only the source code release, since data and libraries should already be installed.

Here's the simplified installation procedure:
```
tar -xzvf FlightGear-0.9.11-pre1.tar.gz
./configure
make
sudo make install

```

Full installation instructions (including library installations from source):
[http://www.flightgear.org/Docs/getstart/getstartap2.html#x17-158000B.4]("http://www.flightgear.org/Docs/getstart/getstartap2.html#x17-158000B.4")

Info on installing from source:
[http://www.tuxfiles.org/linuxhelp/softinstall.html]("http://www.tuxfiles.org/linuxhelp/softinstall.html")
(In Ubuntu you have to use "sudo make install" instead of "su; make install")
[/LIST]

---

### Post by ushills on 2007-07-11
I had this problem after editing the joystick xml file, I don't know if you have done this but if you have programmed the same key twice the programme will run then quit after the splash screen.

The way to correct way to run the programme is 

```
fgfs -timeofday=noon
```

Note I add the time of day flag to avoid night flight.

---

### Post by swoll1980 on 2007-07-14
thanks no luck though

---

### Post by KIAaze on 2007-07-14
What about installing it from source? Did it help or not?

---

### Post by swoll1980 on 2007-07-14
> **KIAaze said:**
> What about installing it from source? Did it help or not?

Thats a little out of my league. I couldn't get past "make" kept getting a no rules error

---

### Post by KIAaze on 2007-07-27
Problem solved or not?

I finally installed flightgear on my PC. I didn't have enough space free before. ^^'
I first tried compiling it from source and also ran into some compilation errors.

But now I installed from the repositories and it worked without any problems.
However there wasn't any ~/.fgfs/autosave.xml file...

The game should be able to launch without it.
I really have no idea what your problem could be now. :(

I'll try finishing compiling from source later so I can better help you with eventual errors you might encounter.

What errors did you get so far? (copy-paste the exact output)

Did you install the build-essential package before?
> sudo apt-get build-essential
Also do this:
> sudo apt-get build-dep flightgear

---

### Post by KIAaze on 2007-07-28
Yay, great, now when I launched it a second time:

```
>fgfs
Error reading properties:
Failed to open file
 at /home/mike/.fgfs/autosave.xml
 (reported by SimGear XML Parser)
  Model Author:  Unknown
  Creation Date: 2002-01-01
  Version:       $Id: c172p.xml,v 1.17 2006-03-13 15:27:14 ehofman Exp $
  Description:   Cessna C-172
freeglut (fgfs): Failed to create cursor
freeglut  ERROR:  Function <glutSetCursor> called without first calling 'glutInit'.

```

...

---

