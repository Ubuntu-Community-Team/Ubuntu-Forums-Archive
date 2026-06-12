---
title: "New Menu Design"
date: 2009-11-30
forum: Art &amp; Design
---

### Post by alms66 on 2009-11-30
I wanted to get some feedback on this before brainstorming it.

Please bare with my long writings as I try to convey the ideas as thoroughly as possible, because my artistic skills are not up to showing these things properly.  I'll provide some mock-ups too, but they won't be pretty – you'll have to use your imagination for that.  Hopefully someone with artistic skills will come along and like these ideas enough to do some quality mock-ups of them. ;)

This thread consists of different distinct ideas, which can be implemented separately, but will provide a much better experience if implemented together – IMHO.

[One Menu App]("http://ubuntuforums.org/showpost.php?p=8416945&postcount=2")
[Task Menu]("http://ubuntuforums.org/showpost.php?p=8416954&postcount=3")
[Further Thoughts]("http://ubuntuforums.org/showpost.php?p=8416959&postcount=4")
[See Image #1]("http://ubuntuforums.org/showpost.php?p=8416963&postcount=5")

---

### Post by alms66 on 2009-11-30
**_One Menu App_**
We essentially switch the Menu Bar and Main Menu apps as they stand now for a single new Integrated Menu App, yet we're able to keep the same appearance of both while adding additional functionality which currently doesn't exist in the process.  It's all done with a few simple user-preferences.

The user-preferences are:
Show (Apps, Places, System)
Sub-Menu (Apps, Places, System)
Display (Icon Only, Text Only, Both)
Expansion (Horizontal, Vertical)

Show will allow the user to check or uncheck each of the three options listed above.  If checked, the item is displayed, if not, the item is not displayed at all.  So for example, a user could simply uncheck Show System because he prefers to use a launcher on his desktop for the Control Panel and the system menu will not display at all.

Sub-Menu determines where the menu is displayed - next to the menu icon on the panel or under the menu list.  If checked, it's under the menu list, if not checked, it's on the panel right next to the menu icon (ubuntu logo).  So for example, if a user was on a very small screen, he could check sub-menu for all three options and free up valuable (in this case) panel space.

Display determines whether to display an icon, text or both for each item in the menu list.  You can only select one option at a time here - and one must be checked.

Expansion determines which direction the menu items expand.  Currently, the option is vertical, you click on a menu such as Applications and all the items below fall into a vertical column.  If you'd check Horizontal here, it would move in the other direction - forming a horizontal row.  One and only one option can be checked here.  Note that this really isn't necessary, but I just thought it a neat addition since all menus in all OS's are vertical - something different.

So, for the classic Menu Bar:
Show: All checked
Sub-Menu: None checked
Display: Text-Only checked
Expansion: Vertical

Note that there should probably be a separate Panel Display and Sub-Menu Display option if we wanted to keep the ability to control those separately – though I read that icons are being discarded so it might not be necessary, I don't know.  So for example, you could show only text on the panel and icons and text on the menu items themselves.

And, for the classic Main Menu:
Show: All checked
Sub-Menu: All checked
Display: Both checked
Expansion: Vertical

---

### Post by alms66 on 2009-11-30
**_Task Menu_**
This adds additional options to the preferences above:
Show (Tasks)
Sub-Menu (Tasks)

The task menu will bring ***true*** task-based computing to Ubuntu.  By default, the menu might look something like this:


_Tasks_
Browse Internet
Email
Chat
Photos
Music
Video
Games
--------------------
Task Manager


All of those are tasks except the last, which will always be present on the menu (the others can be edited or deleted or even additional items can be added with the Task Manager).  A task consists of the following:

Name – displayed in the menu
Action(s) – (open program, location or file) – there can be any number of actions in a given task and opening a specific file also requires setting which program to open that file with

Each Action has a workspace associated with it, so that you might open two actions on workspace one, one action on workspace two and one action on workspace three – all with a single task, for example.  Workspaces are automatically added as needed to fulfill a task.  A task with multiple actions also can set the priority of those actions so that if the task is set to open firefox and transmission, a user might put firefox as priority one so that it opens first and he can begin browsing while transmission opens in the background.  There should be some sort of adjustable delay between actions, so that the system doesn't get bogged down trying to do to many things at once, anything can be set from seconds to hours.  Tasks can even be set to launch on start-up, so that a user doesn't even have to launch the task himself, he just logs in and Firefox opens, then Evolution a few seconds later, then Rhythmbox a few more seconds later...
As you can see, there's a lot of potential for automation here...

A location in this context is either a directory or a menu location.  For example, it might either be "/home/username/Documents" or "\Applications\Games" for a "Games" task to show a list of all menu items at that location or "\System\Administration" for a "Administer" task to show a list of all items at that menu location.

Practical Example:
I remember reading somewhere that someone liked to have one workspace for "work" and another for "play".  There you go, define a task with the Task Manager, called Work & Play.  It might consist of the following actions:
Open file 'Work Image.png' with GIMP (on workspace 1 - Work)
Open /home/documents (on workspace 1 - Work)
Open Evolution (on workspace 1 - Work)
Open "my playlist" with Rhythmbox (on workspace 2 - Play)
Open Firefox (on workspace 2 - Play)
Open Mahjongg (on workspace 2 - Play)

...and of course, there would be priority specifications with that, but I'm not going to list here in the example, as that's totally dependent on a user's desires.  In fact, you'd probably want to break that into two tasks honestly (work as one and play as another) so that you could not "play" if you're serious about "work"ing...

More notes on the Task Menu, is that it should learn the user's favorite tasks over time and adjust to that.  So (using the "defaults" above), if a user always starts his computer and Browses Internet, that task rises to the top of the list.  If he also always starts Music, the system might put that second since it's not the first thing he always does, that's Browse Internet.  Then if the trend continues, the user might be asked if he'd like to merge the two tasks into one to ease his computing.  So basically, the list of tasks will order themselves to the ones you use the most being first and the least last.  More than that, the system will ask you to delete tasks you never use, or create tasks for programs/locations/files you use frequently.  It will also ask you to merge tasks if it finds that you always listen to music while browsing (Browse Internet + Music tasks) but rarely start the music task by itself.

...and finally, the concept could be expanded to starting/stopping processes, conditionally doing actions (for example, only open firefox if internet connection is active), and probably more I'm not thinking of.

---

### Post by alms66 on 2009-11-30
**_Further Thoughts_**
These are just some extras...

1.Do away with the Show and Display options and simply show all options and display all options (Apps, Places, System and Tasks) at all times.  It won't take any more or any less clicks or mouse movement than it currently does with the menu bar really and it will take less mouse movement than the main menu does (digging through the submenus) in some cases.  A problem with this is that the menu would be very wide, possibly to the point of not being usable on a small screen.

2.Remove (Desktop, Documents, Music, Pictures, Videos, Downloads) from the places menu and make Home a fly-out menu of all items in the user's home folder (not hidden, of course, but include files and folders – and make those folders listed fly-outs too?).  This allows a user to browse his home folder without having to dig through the file manager.

3.Like #2 above, but with Computer.  Make computer a fly-out menu and delete all items that show up below it (mountable drives) in the Places menu list.  The items under Computer should probably not be fly-outs though, as above in #2.

4.Use "Recent Documents" from the Places menu to fill up the empty space under the Places and System menu – since both of those now have a static list of 5 items each.  Also add a "Favorite Applications" item, similar to it to help fill in the area.  Basically, Recent Docs would stay under places and Favorite Apps would fall under system.  Clear Recent Docs and Clear Favorite Apps would then fall under those on the menu rather than on the fly-out.  One big question remains.  If the application menu expands, what do we do with the left-over space under tasks, places and system?

---

### Post by alms66 on 2009-11-30
I've got a (bad) mock-up below.  You can see how the menus would sit side-by-side all at one press of the menu button (the ubuntu logo).  There should be some vertical seperators between the columns.  There should also be titles to each menu column (Applications/Places/System).  You'll have to use your imagination to put those and the Task Menu in place and do all the little optimisations listed under Further Integration.  Like I said, what you're looking at is the extent of my artistic skills, cut and paste...
I'll try and get something better than this, but it'll take me some time, and it'll be done from MS paint while I'm at work. :D

---

### Post by alms66 on 2009-11-30
Reserved...

---

### Post by Psumi on 2009-11-30
GNOME Shell is basically the task menu thing.

---

### Post by alms66 on 2009-12-01
> **Psumi said:**
> GNOME Shell is basically the task menu thing.
Um... No?
Based on what I see [here]("http://live.gnome.org/GnomeShell") at least, what I describe as the 'task menu' can easily be incorporated into gnome shell and gnome shell has no such 'task' feature.  But I haven't actually tried gnome shell yet, so maybe you're right.

---

### Post by garywilson on 2009-12-02
sounds great .

---

### Post by alms66 on 2009-12-02
added another mock-up

---

### Post by alms66 on 2009-12-07
Can anyone else confirm what Psumi said, that GNOME shell does have tasks as described here?

---

### Post by Merk42 on 2009-12-07
> **alms66 said:**
> Can anyone else confirm what Psumi said, that GNOME shell does have tasks as described here?

As far as I see, currently GNOME Shell does **not** have such a thing.
The overlay lists applications, places, and recent documents.

For more information and pictures see the [GNOME Shell thread](http://ubuntuforums.org/showthread.php?t=1305154) in Lucid Lynx Testing and Discussion

---

### Post by Bumper44 on 2009-12-08
I'm fine with how it is now, but if I used the menu more I might like it.

---

### Post by alms66 on 2009-12-08
Thanks Merk42.
I will get this up as an idea on Brainstorm as soon as I get a chance then.

---

### Post by Merk42 on 2009-12-12
> **AnnaKunto said:**
> Microsoft Publisher is what you want it is about £149 to buy, I believe there are cheaper versions on the market and eBay often advertises them. If you go on Microsoft downloads you can download the whole office suit on a trial basis about 3months then you either pay for it or they take it back.
Did you post in the wrong thread :confused:

---

### Post by alms66 on 2009-12-12
You can now vote on these ideas over at Brainstorm...

[Task Menu]("http://brainstorm.ubuntu.com/idea/22889/")

[One Menu App]("http://brainstorm.ubuntu.com/idea/22888/")

---

