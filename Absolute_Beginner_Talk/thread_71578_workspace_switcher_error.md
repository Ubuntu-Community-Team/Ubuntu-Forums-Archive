---
title: "workspace switcher error"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by kzinti on 2005-10-03
I am getting this error when I am trying to change the workspace swicher preferances. How do I fix it? 
```

Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names' specified for `/apps/panel/applets/applet_10/prefs/display_workspace_names' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_10/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_10/prefs/num_rows' stores a non-schema value
```
Right now the switcher will only show the curent desktop so I cant change to the other desktops.
Thanks
Ryan

---

### Post by Mustard on 2005-10-03
Hmmmm..have you tried removing the applet from the panel completely then adding it again?

This would be my clumsy approach.  I've not seen this issue before.

---

### Post by kzinti on 2005-10-03
I tried that it didn't help.

---

### Post by Mustard on 2005-10-03
Hmm...sorry, that was my best shot. :D

Hopefully someone has experienced this issue before.  Do you have any idea how it might have come about?

---

### Post by Ampersand on 2005-10-04
If you open Configuration editor (from System tools), then browse to the folder in the error (schemas - apps - workspace_switcher_applet) and click on 'prefs', what do you get in the name and value columns?

Does it look anything like this? [http://i16.photobucket.com/albums/b3/ampersand84/gconf.jpg](http://i16.photobucket.com/albums/b3/ampersand84/gconf.jpg)

---

### Post by kzinti on 2005-10-04
It looks like that but when I click on any of the values this error shows up
```
Type mismatch: Expected `UNKNOWN, 5' got `Boolean' for key /schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces
```

The gdesklets switcher works just fine so I am using that right now but I would like this one to work also.

---

### Post by RikBlankestijn on 2005-10-18
I got the exact same issue after installing gdesklets.
My image doesn't look like the gconf.jpg Ampersand added, because the value of display_all_workspaces is a selection box.

---

### Post by RikBlankestijn on 2005-10-19
Please take a look at the last message in this thread: [http://ubuntuforums.org/showthread.php?t=38724](http://ubuntuforums.org/showthread.php?t=38724)
he changed the value of this integer to 1, I preferred changing the key to a boolean type and set it to true. 

So the problem is solved.

---

### Post by drconex on 2006-06-24
[QUOTE=Mustard]Hmmmm..have you tried removing the applet from the panel completely then adding it again?

This would be my clumsy approach.  I've not seen this issue before.[/QUOTE]
I got the same problem. 
I want to remove the Space Switcher Desklet, 
Could any body instruct me the way to do it. 

drconex

---

