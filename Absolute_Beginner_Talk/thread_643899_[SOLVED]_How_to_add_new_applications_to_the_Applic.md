---
title: "[SOLVED] How to add new applications to the Applications Menu?"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by brett611 on 2007-12-18
New post as I don't believe other 'related' posts have been fully answered.

I'm loving Ubuntu(7.10), speed is fantastic, easy to use vs easy to spend hrs maintaining XP environment...however I have made extensive use of Synaptics(sp?) and have found every app I could need.

Yet none of these new apps gets added to the Applications menu.  The Applications menu now looks the exact same as when I did a fresh install.  I am able to launch apps via a terminal command but I want to have either a shortcut/launch or added to the Applications menu.  The problem is that I don't know how to do either, and prefer the latter.  

I'll give 2 examples: beagle and 7zip

Thanks!

---

### Post by Malta paul on 2007-12-18
May be a bit over simplified but you can add items to Applications Go to System>Preferences>Main Menu. Then add to 'Menu' and the add To Items.
Hope this may help:)

---

### Post by vishzilla on 2007-12-18
Over the menu bar (Applications/Places/System) right click on the bar...and select 'Edit menus'
Go to the appropriate section and add your Program by clicking on 'New Item'
Enter the description and enter the same terminal command you usually enter into the command box and click on OK and you are done

---

### Post by philinux on 2007-12-18
Or just right click the menu and select edit menus. Add in whatever you need.

---

### Post by RomeReactor on 2007-12-18
Hi. You can right-click on the menus and select "Edit Menus"; there you can select in which sub-menu you want to place the launcher. To fill out the **Command** section, open Synaptic, search for the program you want to create a launcher for, right-click on it and select "Properties", go to the "Installed files" tab and look for an entry in **/bin** or **/usr/bin**. As far as I know, 7zip is a command line program, though, so there wouldn't be any need to make an entry for it in the menus.

Hope this  helps.

EDIT: Too slow...

---

### Post by thelatinist on 2007-12-18
Exactly what packages have you installed that didn't create menu shortcuts?  Only GUI apps get shortcuts...packages for libraries or command line utilities don't.

---

### Post by brett611 on 2007-12-18
Thanks all.  I'll try your suggestions tonight.  I guess what I'm trying to avoid is having to launch the Add/Remove Applications tool, select "Installed Applications" only and then figuring out what the launch commands are.  Just seems like there has to be an easy way to 'find' an application that is installed on the machine.  I'm a bit of an apps junkie so I like to try a bunch of different things

W/R/T which applications aren't in the menu bar - aside from the 7Zip and Beagle apps previously mentioned, I'll snap a screenshot tonight and post it

Thanks again

---

### Post by thelatinist on 2007-12-18
The beagle installer doesn't create a link to the gnome-based GUI.  Beagle searches can be done a number of ways, including through the terminal.  If you want to make a launcher for  the GUI, its command is beagle-search.

As for 7zip, you don't need a separate GUI.  Once you install the 7zip libraries you can create and unpack 7zip archives using any standard archiving tool.  I use Xarchiver.

---

### Post by brett611 on 2007-12-18
Thanks!  Re: 7zip.  I'm used to Windows where 7zip is the actual application that archives the file.  It sounds like in Linuxland I need an additional app that relies on 7zip libs?  I'll give xarchiver a shot.

---

### Post by forestpixie on 2007-12-18
> Just seems like there has to be an easy way to 'find' an application that is installed on the machine

you can use ```
whereis
``` to find something, then do any of the above and paste in the 'found' command

---

### Post by brett611 on 2007-12-18
> **forestpixie said:**
> you can use ```
whereis
``` to find something, then do any of the above and paste in the 'found' command

Thanks Pixie - that'll be a big help

---

### Post by brett611 on 2007-12-18
Thanks All!
I have to say, these help forums are amazingly helpful.  I get faster, more accurate & more insightful answers, and suggestions, than anything I've ever come across in the last 15 yrs of MSFT land.

The right click/edit Applications solved 90% of my issues and 'whereis' solved the remainder.

Thanks again

---

### Post by niceguy123 on 2008-01-06
I just installed Pidgin manually with the help of this [https://help.ubuntu.com/community Pidgin Internet Messenger]("https://help.ubuntu.com/community/Pidgin?action=show&redirect=InstallPidgin2.0")

When through all of the stages in terminal and it seemed to take the time needed etc.

But, when the process was finished I don't see Pidgin in the applications menu and can't figure out how to get it there.

Thanks for the help. :)

---

