---
title: "Where are my downloads?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by keval on 2007-07-07
Greetings.
Really basic question: I'm using the Synaptic Package Manager to download some applications, but I have no idea where they might now be located, or how to fire 'em up.  How can I find where these files are installed?  How can I determine the commands necessary to run them?
Thanks,
Kevin

---

### Post by mytwobears on 2007-07-07
After Synaptic has downloaded and installed applications, you should check under the Applications, or Systems links on your top panel.  Depending on the type of program (Internet, Sounds, Video etc.  ) it will be organized by these categories under the Applications link.  Under the Systems link just look through the lists for the program.

If these programs are not listed, then you can open the terminal and type the name of the application and that should start it.

---

### Post by robertc36 on 2007-07-07
Alt + F2 will bring up a list of apps.
You can put the name in terminal to run.
Or you can add custom items  in menu.
In synpatic if you right click on the app just installed you will get a list of included files and you can work out from there where everything is .
Sometimes things appear in the menu after a reboot or logging out and in.

---

### Post by keval on 2007-07-07
Thanks for the quick replies.  I'd never have found the alt-F2 trick on my own.
I find that apps downloaded via Synaptic more often than not don't find their way to the "Applications" list.  Maybe it's because some of them don't map easily onto the list of applications there, but I find that using "applications" to locate or start my Synaptic-downloaded stuff is always an iffy proposition.  Is there something I'm doing wrong?
Thanks,
Kevin

---

### Post by 3rdalbum on 2007-07-07
It depends what you're downloading. There are quite a few packages which are command-line or console-based programs, so naturally they don't put anything into your menu.

But yes, there are many GUI programs where the packager has not bothered to put a .desktop file in the correct place. To my own thinking, that is not the correct way to package a program, but until all packagers see the light here's what you can do.

Go into Synaptic, and find the package that you just installed. Right-click it, and go to Properties and then the Installed Files tab. Any files under the directories "/bin/" or "/usr/bin" are executables. You can just type the name (what's after the last slash in the path) in a terminal to run the program. You can add a menu item by going into the Main Menu editor, and then adding a new item with the command that you just typed in the terminal.

Not too difficult, thankfully, but I suggest you learn how to compile programs and package them as .debs so we can change the situation :-)

---

### Post by RomeReactor on 2007-07-07
Hi. It's true that not all applications you install come with menu entries; most do, however, and sometimes all it's needed for them to show up on the menus is to restart the panels: Go to "System->Administration->System Monitor" (If you're on Gnome), right-click on **gnome-panel**, and select "Kill Process" (it will actually restart the panels; just make sure you don't have an application that uses an icon in the Notification Area running while doing this, since restarting the panels will close some of those applications, if not all of them). Once the panels restart, look in the menus for the programs you installed. If they still don't show up, it means (logically) that they didn't generate a menu entry. 

To correct that, open Synaptic and search for the application you want to add to the menu (and that's already installed). Upon finding it, highlight it and press the **Properties** button next to "Search. select the **Installed Files** tab, and look for entries in **/usr/bin** or **/usr/local/bin**. More likely than not, one of the entries (if there's more than one) will read **/usr/bin/PROGRAM_NAME**. Try entering that into the terminal (Applications->Accessories->Terminal). If the program starts up, then close Synaptic, right-click on the menus (top panel, left) and select "Edit Menus". Now you'll have to highlight the section on the left pane you want to put the launcher in (Accessories, Games, Graphics, Internet, etc.) and press the **New Item** button. You fill it out like this:

* Type: Application
* Name: (self explanatory)
* Command: (what you entered in the terminal)
* Comment: (not necessary, you may leave it blank)

Finding the icon is done the same way as finding in Synaptic the command to launch the application, but instead of looking for entries in **/usr/bin** or **/usr/local/bin**, you look for an entry in **/usr/share/pixmaps**. Once you find it, you can add it to the launcher by editing the menus.

Sorry for the long post. Hope this helps.

---

