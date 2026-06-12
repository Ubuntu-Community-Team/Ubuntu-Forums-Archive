---
title: "New apps not showing up in the applications menu"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by spazsui on 2006-07-08
Hey folks, this is a two-fold question.  I added some new apps thru synaptic but when I look in my apps menu they aren't showing up.  How do you fix that?  Also, if you wanted to start up an app thru the commandline what exactly would you type?  Yes I am a newb.  I even have Linux for Dummies but to be honest there are some questions that I either can't find the answert to in it or maybe I'm just not asking the right question.  Thanks for the help.

---

### Post by Bossieman on 2006-07-08
Try this:
killall gnome-panel

To start up a program you write down the name of the program.
For gaim just write gaim and hit enter.
You can also start writing the name and hit the tab-key and get hints.
What program is it you want to start from the command line?

---

### Post by tonyr on 2006-07-08
For the Command Line part:

Open a terminal (**Applications->Accessories->Terminal**).
You'll get a Window with a prompt and a blinking cursor.
That's where you type commands.  Try **ls -l**.  Try **date**.

Google **Linux Command Line Interface** for an unbelievable
amount of information about How To Do It.  Some people have
favorites, which will no doubt show up here.

EDIT: maybe this was a little too low level.  Each command has a command line syntax.  
Do **man <program-name>** to get the specifics, eg. **man gedit**.

---

### Post by DSn0wMan on 2006-07-08
At the bottom of the applications menu there is a Add/Remove applications link that lets you add and remove applications from the menu.

To start an application from the terminal just navigate to the directory where it's installed and type the name of the program and hit enter. If that dosn't work you can try it with a "./"

./someprogram

I hope this helps.

---

### Post by ahaslam on 2006-07-08
> **Bossieman said:**
> Try this:
killall gnome-panel

To start up a program you write down the name of the program.
For gaim just write gaim and hit enter.
You can also start writing the name and hit the tab-key and get hints.
What program is it you want to start from the command line?

If it works by the command line you can create a launcher with the same command line. The launcher can then be placed in the menus using the editor.

Tony.

---

### Post by Qrk on 2006-07-08
Right clicking on a package you've installed in synaptic will allow you to see what command to type. It's the name of the file that is listed in /usr/bin

---

### Post by gThree on 2006-07-08
Just to clarify:

```
killall gnome-panel
```
kills processes associated with the program gnome-panel (which contains your menu).  Gnome will immediately restart it so, in effect, you're resetting the menu by doing this.  If a new program is going to automatically appear in the menu, this will do it.

If it still isn't there, you'll need to manually add it.  I suggest the Alacarte Menu Editor, a GUI menu manager.  You still need to know the correct command to run the program you want to add.  As noted, you can find this in Synaptic.  Or try the "whereis" command in a terminal.
```
whereis [myProgramName]
```
will return binary and manual entries for that program.  Example:
```
whereis gedit

returns

/usr/bin/gedit /usr/bin/X11/gedit /usr/share/man/man1/gedit.1.gz
```
Add the following option to just search for binaries:
```
whereis -b [myProgramName]
```

If you see "/usr/bin/gedit", then your command is "gedit".  At this point, you may want to check its manual for useful options.  Run this in a terminal:
```
man [myProgramName]
```
Hit "space" to advance a page, hit "b" to go back a page, hit "q" to quit the manual.

Example of why checking "man" entries can be useful:
```
opera --nomail
```
This option starts Opera without the e-mail/chat/newsfeed features.

Alacarte Menu Editor is easy to use (although slow for some reason in Dapper).  If you right-click a current entry and select "Properties", you can see a completed example.

Hope that's helpful ...

---

### Post by spazsui on 2006-07-08
The program that I installed was Debian menu and gnome photo printer. Neither one shows up in my Applications menu even though they are definitely installed.  I did the killall gnome panel but they didn't show up afterward.

---

### Post by Dr. Nick on 2006-07-08
try this command from a terminal to get menu icons

update-menus -v

Should be necessary though, most apps make icons themselves, which applications are you having that dont? It may be a bug with the program itself if it hasnt been updated in awhile

---

### Post by spazsui on 2006-07-08
Tried your update menu-v but gnome photo printer still isn't showing up.  That's really the only one that I need to appear.  So how can I specifically get that one?  When I was using breezy version and used automatix to install the debian menu it showed up and gnome photo printer showed up in the debian menu.  Now I don't really have a need for the debian menu since updating the gnome menu and killall did get all of the other icons except gnome photo printer.  So what do I need to do to just get that one?  I'm pretty new at this so I'll have to be walked through it step by step.

---

### Post by Dr. Nick on 2006-07-08
have you run this from a terminal?

[SIZE=3]** gnome-photo-printer**

If it launches then adding a menu entry is easy. Click Applications -> Accesories -> Alacarte Menu Editor and you can use the file menu to make a new entry
[/SIZE]

---

### Post by spazsui on 2006-07-10
Nope, haven't tried that with the terminal.  What exactly would I type in the commnadline to get it to launch?  Just want to make sure I do it right.

---

### Post by spazsui on 2006-07-10
Well, after some web searching and some trial and error I figured it out.  Was able to start from the commandline no problem and finally got it added to my applications menu.  Not bad for a newbie!:D

---

### Post by koolkatkiwi on 2007-11-18
> **Dr. Nick said:**
> 

If it launches then adding a menu entry is easy. Click Applications -> Accesories -> Alacarte Menu Editor and you can use the file menu to make a new entry
[/SIZE]

Hi. I found this thread when trying to find/start Lingot, which I had installed. There is nothing to tell you how to open the program. After reading this thread I installed the Alacarte Menu Editor, which did not appear in the Applications > Accessories menu at all - I don't know where to find it - same problem as finding and running Lingot. 

I then right-clicked on a blank space in the top menu bar, clicked on "Add to Panel" and created a Custom Launcher for the Lingot program. Now I can finally start the program by clicking on this icon in the top menu bar. I'd have preferred to put it in the Applications menu, but could find no way of doing this.

Couldn't a clickable menu item be included with programs when they are installed, and be automatically installed with them? Instead of people having to search for the program and then start it via the command line. I even had to Google to find the command to start the program from the command line. Maybe it was just an oversight that the menu item entry wasn't included, though.

Cheers,
Kath.

---

