---
title: "Workspaces on toolbar"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-02-28
Is there a easy way to get the workspace blocks to show up on my toolbar again?

---

### Post by Adramelech on 2007-02-28
Rightclick on panel-> add to panel -> workspace switcher

I guess is what you are refering to.

---

### Post by xyz on 2007-02-28
Do you mean right click on panel > Add to Panel > Workspace Switcher > Add > Close?

---

### Post by TwistesdTexan on 2007-02-28
That's right!!

---

### Post by J11Gyro on 2007-02-28
tried that and it does no give me a choice of showing all workspaces, just one. not sure what I did to get rid of it in first place.

---

### Post by petersjm on 2007-02-28
Once you've added it, right click the workspace icon and click "properties". There should be an option of how many workspaces you want...

---

### Post by J11Gyro on 2007-02-28
That option is not highlighted so I can change it, that is the problem. is there any way of returning toolbar to default?

---

### Post by petersjm on 2007-02-28
Um, just a question - do you have Beryl installed and running? I *think* that overrides the default workspace areas with it's own. In either event, if you press CTRL+ALT+left/right arrow, does your workspace change?

---

### Post by J11Gyro on 2007-02-28
Yes the quick keys worked great, duh didn't think of that. would still like to get them up on tool bar, but will deal with it for now till i can repair it.:popcorn: here is the error it shows  not sure what beryl is or whether i installed it. didn't do alot of adding except to desktop set up for all family members.

Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_1/prefs/display_all_workspaces' stores a non-schema value

---

### Post by petersjm on 2007-02-28
LOL, if you don't know what Beryl is, you haven't installed it :D
As for getting the panel switcher to work, I'm afriad I'm at a loss. But at least you've got the key-method for now...

---

### Post by J11Gyro on 2007-02-28
I thank you for that. wonder if a gnome desklet has changed something. I can get all the spaces to show up in it  just not on the toolbar :lolflag:

---

### Post by crossedout on 2007-02-28
Try this:
Navigate to System Tools->Configuration Editor->apps->panel->applet_3 (this may be different in your case, highlight each applet_# until you see OAFIID:GNOME_WorkspaceSwitcherApplet)

Navigate down to prefs and choose display_all_workspaces. num_rows should equal 1 (for default look)

SideNote: If you don't have Configuration Editor, Navigate to Accessories->Alacarte Menu Editor and Select System Tools, then select Configuration Editor.

-Xout

---

### Post by J11Gyro on 2007-02-28
Fixed it by going to System-Preferences-Menus and Toolbars. Clicked all 3 boxes and it let me add them back, I knew it was something I did but couldn't remember what :lolflag:

---

