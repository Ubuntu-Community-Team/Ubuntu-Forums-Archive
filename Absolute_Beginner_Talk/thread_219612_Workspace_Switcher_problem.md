---
title: "Workspace Switcher problem"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Uncle Spellbinder on 2006-07-20
I noticed that on starting Ubuntu Dapper this morning that the workspace switcher on one of my panels was only showing one workspace (I had it set to the default of 4). I clicked properties to see what the problem might be and got this error message:

> An error occurred while loading or saving configuration information for gnome-panel. Some of your configuration settings may not work properly.

Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names' specified for `/apps/panel/applets/applet_1/prefs/display_workspace_names' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_1/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_1/prefs/num_rows' stores a non-schema value


I'm still rather new to Linux. So needless to say, I'm at a loss.:-k

**EDIT**:
Closed out of the error box and now when I open workspace switcher properties, all three options ("Show Only The Current Workspace", "Show All Workspaces" and "Show Workspace Names In Switcher") are greyed out.

---

### Post by adam.tropics on 2006-07-20
Have you tried restarting the panel (killall gnome-panel)

---

### Post by adam.tropics on 2006-07-20
Also, you wouldn't happen to use xgl/compiz. as that will only show in settings as one workspace, but behave as 4.

---

### Post by Uncle Spellbinder on 2006-07-20
No xgl/compiz. 

I did killall gnome-panel, it went back to only one workspace. I clicked properties and was able to change it back to four. But instead of showing 4 across, they were vertical (and very small). I removed it from the panel and put it back and the same error message appeared.

---

### Post by adam.tropics on 2006-07-20
Well, ok, if you look in configuration editor (gconf-editor) and go

apps>>panel>>applets>>workspace_switcher_screen0>>prefs

You should find a few options, one of which is number of rows. Presumably setting that to 1, would solve at least the newer problem.

---

### Post by Uncle Spellbinder on 2006-07-20
Yeah, I got the prefs fixed. Missed that one somehow. 

Very strange. I got it working, but If I remove it then put it back, I get the same error message. I have to then *killall gnome-panel* to get access to properties and change it back to 4.

---

### Post by adam.tropics on 2006-07-20
That's bizarre!

---

### Post by Uncle Spellbinder on 2006-07-20
My wife just informed me that while I was at work yesterday the power went out twice. Though the computer was off, could that have borked something causing this message? If so, does anyone know how I migh correct the Schema issues in the error message?

> An error occurred while loading or saving configuration information for gnome-panel. Some of your configuration settings may not work properly.

Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names' specified for `/apps/panel/applets/applet_1/prefs/display_workspace_names' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_1/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_1/prefs/num_rows' stores a non-schema value


---

### Post by adam.tropics on 2006-07-20
Ok, so running late will check back tommorrow, but no, I don't see how a power outage could have any effect if the computer was turned off. As for the errors, it looks rather like somehow, the entries you have in those keys is either invalid (have a check, it will tell you your options), or gconf has totally lost the schema and so can't tell what is valid. Restoring th schema can 'sometimes' be as simple as starting gconf-editor as sudo, then starting it again as <user>.

---

### Post by hard_i on 2006-07-26
ok, i'm having the same problem over here.
It only happens when using XGL/compiz.
I can move windows to other desktops but can't switch to them.

---

### Post by shnazzle on 2006-08-01
Ok. I have the same problem as of today. Strangely enough, I've also had a few power-outages here #-o   I don't run XGL/Compiz, never have on this install.

I can't go to gconf-editor  apps>>panel>>applets>>workspace_switcher_screen0>> prefs  simply cus it doesn't exist.

Whenever I add the workspace switcher to my panel, it adds a key under apps>>panel>>applets  called "applet_3" or "applet_4"... 

Now all of a sudden (as I write this) I did it again (remove from panel, add to panel) and now all of a sudden I have an entry apps>>panel>>applets>>applet_3, which contains all the entries that the workspace switcher would have. It had incompatible Integer values for the top two preferences. I switched those to boolean... and it works now :confused:

...now to try removing it and adding again...


yup, problem is back.
Now I have apps>>panel>>applets>>applet_4, had to change things back too boolean again. And now apps>>panel>>applets>>applet_3 is filled with crap.

Now ...applet_3 is gone.


I hope this little storyline while I tried this out sheds some light on some issues to come to a solution

---

### Post by johnfarrow on 2007-08-28
how to go to "gconf:)-editor"?

---

### Post by notwen on 2007-08-28
> **johnfarrow said:**
> how to go to "gconf:)-editor"?

Press ALT+F2, then type the following in the textbox and hit enter.

```
gconf-editor
```

---

### Post by asmoore82 on 2007-08-28
> **Uncle Spellbinder said:**
> My wife just informed me that while I was at work yesterday **the power went out twice**. Though **the computer was off**, could that have borked something causing this message? If so, does anyone know how I migh correct the Schema issues in the error message?

If your BIOS was/is set to automatically recover from power failures or "Auto On,"
the first power outage would have made the computer turn itself ON,
then the second power outage could have done the damage.

the schemas seem to be owned by the 'gnome-panel-data' package ...
```
~$ dpkg -S /usr/share/gconf/schemas/panel-object.schemas 
**gnome-panel-data:** /usr/share/gconf/schemas/panel-object.schemas
```

I would try force re-installing that package, 'gnome-panel-data'

---

