---
title: "Where are the Games I downloaded via Synaptic?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-12
I've downloaded two games listed in Synaptic. Do they automatically show up in Applications -> Games? Or, do I have to do something to make them show up there? :confused::)

---

### Post by igknighted on 2007-02-12
> **kittyhawk63 said:**
> I've downloaded two games listed in Synaptic. Do they automatically show up in Applications -> Games? Or, do I have to do something to make them show up there? :confused:

They should show up automatically... what games did you install?

---

### Post by kittyhawk63 on 2007-02-12
> **igknighted said:**
> They should show up automatically... what games did you install?

3D Chess and ? Can't remember the other. Actually I think it was a file that needed to be downloaded with 3D chess. I've downloaded the 3D chess three times. Nothing has appeared in the Games File.

---

### Post by igknighted on 2007-02-12
> **kittyhawk63 said:**
> 3D Chess and ? Can't remember the other. Actually I think it was a file that needed to be downloaded with 3D chess. I've downloaded the 3D chess three times. Nothing has appeared in the Games File.

What happens if you run '3dchess' (or whatever the package name was) from the command line?

---

### Post by meng on 2007-02-12
Not everything comes with a menu entry. If you can't remember what you installed, you're at a disadvantage - but it's easily fixed. Go to Synaptic and look at History, that will jog your memory as to what's been installed.

---

### Post by kittyhawk63 on 2007-02-12
> **igknighted said:**
> What happens if you run '3dchess' (or whatever the package name was) from the command line?

Haven't tried. I'm a novice. Give me the info I need to do that. Thanks.

---

### Post by igknighted on 2007-02-12
Just open a terminal (applications -> accessories -> terminal) and type '3dchess', <enter> and it should run.

---

### Post by kittyhawk63 on 2007-02-12
Nothing happened. Said it could not find 3dchess.

---

### Post by igknighted on 2007-02-12
> **kittyhawk63 said:**
> Nothing happened. Said it could not find 3dchess.

hmm, are you sure that it installed?  Did it give you any errors?

---

### Post by kittyhawk63 on 2007-02-12
Don't remember seeing any. I will try again to see if any errors show on attempt to reinstall. Be right back if you care to wait.

---

### Post by kittyhawk63 on 2007-02-12
Showed no error. Install a success. Do I need to type in the version number after 3dchess?

---

### Post by igknighted on 2007-02-12
> **kittyhawk63 said:**
> Don't remember seeing any. I will try again to see if any errors show on attempt to reinstall. Be right back if you care to wait.

try this instead: open a terminal as before, and type these commands:
```
sudo apt-get update
sudo apt-get install 3dchess
```

it will give you more feedback as to what's happening.

---

### Post by igknighted on 2007-02-12
> **kittyhawk63 said:**
> Showed no error. Install a success. Do I need to type in the version number after 3dchess?

no, no version number should be necessary.  The issue should be what the command is.  What was the exact package name in synaptic?

---

### Post by RomeReactor on 2007-02-12
Hi. Write in the teminal

```
3Dc
```

---

### Post by kittyhawk63 on 2007-02-12
I downloaded again. Install was successful. Stilll no game. Do I have to enter the version number also in terminal?

---

### Post by kittyhawk63 on 2007-02-12
> **RomeReactor said:**
> Hi. Write in the teminal

```
3Dc
```

nothing

---

### Post by kittyhawk63 on 2007-02-12
3dc did not work
3DC did not work
3Dc did work.
How can I get it to show up in Games?

---

### Post by igknighted on 2007-02-12
Sorry, I'm not running ubuntu ATM otherwise I'd look it up myself, but what is the package's name in synaptic?

EDIT, saw your post now.  Be careful, as linux is case sensitive, ergo 3dc is not the same as 3Dc.  To add it to your menu, right click the applications menu and choose "edit menus"  Here enter the name of the program, the command (3Dc) and you can click the icon button to browse for an icon on your computer you want to use.

---

### Post by kittyhawk63 on 2007-02-12
> **igknighted said:**
> Sorry, I'm not running ubuntu ATM otherwise I'd look it up myself, but what is the package's name in synaptic?

I'll check. Be right back.
Here is your answer.

3dchess 0.8.1-11-1
3D Chess for X11

---

### Post by Maestro23 on 2007-02-12
> **RomeReactor said:**
> Hi. Write in the teminal

```
3Dc
```

Just downloaded this myself.  That is the terminal command to start the game.

---

### Post by abd5hafeeq on 2007-02-12
Hey I had the same problem but it worked when I typed 3Dc 
But it`s not 3D.

Hey maybe your Sypnatic was open when you`re trying to update it

---

### Post by kittyhawk63 on 2007-02-12
3dchess 0.8.1-11-1
3D Chess for X11

---

### Post by RomeReactor on 2007-02-12
As meng said, not every program we install comes with a launcher in Applications (though most do). On the other hand, sometimes a program that **does** have a launcher gets installed, but it won't show up in Applications right away; for cases like this, open the System Monitor (System-->Administration-->System Monitor), look for **gnome-panel**, right click on it and select "Kill Process". It will restart the Panels and (hopefully) the game should show up now in Applications.

If it doesn't, then it's time to make a launcher: Right-Click on **Applications** and select "Edit Menus"; now go to the "Games" entry on the left and it'll show you what you already have there. Now click the "+ New Item" button on the right, and when the new window shows up, write the command to run (in this case, **3Dc**). Add a name for that entry (**3d Chess**), add an Icon if you wish (might have to look for an icon on your own, or select from the ones it offers you), and press "OK".

---

### Post by kittyhawk63 on 2007-02-12
> **igknighted said:**
> Sorry, I'm not running ubuntu ATM otherwise I'd look it up myself, but what is the package's name in synaptic?

EDIT, saw your post now.  Be careful, as linux is case sensitive, ergo 3dc is not the same as 3Dc.  To add it to your menu, right click the applications menu and choose "edit menus"  Here enter the name of the program, the command (3Dc) and you can click the icon button to browse for an icon on your computer you want to use.

Thanks mucho.

---

### Post by kittyhawk63 on 2007-02-12
Got it to work. I can only say, "What a great group of people here on this forum." Thanks for all the assistance. :) :) :)

---

### Post by kvonb on 2007-02-12
What I do in this situation is run Synaptic, search for the application I just installed, (in your case type in "chess", it will give a list of ALL chess related material), then right click on the one you installed and select properties.

There is a tab called "Installed Files", look through that list for the executable, usually listed under /bin/, or /usr/bin/, in this case the executable is /usr/games/3Dc (NOTE it is case sensitive!!).

The other thing I do is re-load the Gnome menu, press <ALT><F2> to bring up the "Run" dialogue, type into it: killall gnome-panel (it's ok, it will pop straight back up), and run that.  Now look through the menus and see if it is there.

If still not there, you can install "debian menus", I can't remember the actual package name, I'm sure somebody else will provide that, but that will give you ALL the standard X stuff that is installed, making it a bit easier with some things.

Also you could just right click on your desktop, select "create launcher", give it a name, in the "command" box, type: 3Dc, select an icon by clicking on the box to the left that displays "no icon", then OK.  That should then run it.

Regards, KEv :)

---

