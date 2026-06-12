---
title: "lost workspaces"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by BKK on 2006-07-01
Hi

I was using gdesklets, but I have stopped for now.

I dont have the option to switch between workspaces un less I use a gdesklet. I have tried removing and adding the switcher in the bottom panel. I get the following error:
 
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_1/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_1/prefs/num_rows' stores a non-schema value

where do I change the values?
Thanks

---

### Post by Spleenie on 2006-07-01
[QUOTE=BKK]Hi

I was using gdesklets, but I have stopped for now.

I dont have the option to switch between workspaces un less I use a gdesklet. I have tried removing and adding the switcher in the bottom panel. I get the following error:
 
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_1/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_1/prefs/num_rows' stores a non-schema value

where do I change the values?
Thanks[/QUOTE]

Never seen those errors before, so perhaps somone else can decode them for you :)

One thing you could try is (in a terminal):

```
killall gnome-panel
```

This sort of resets your gnome panels. You could try adding one then.

Another thing to try is 3ddesktop, which is a cool little program which gives you a 3d style desktop switcher. Have a look around [here]("http://ubuntuforums.org/showthread.php?t=100169&highlight=3ddesk") to learn more about that.

Short of that, I have no answers. :)

---

### Post by BKK on 2006-07-01
Thanks, killall doesnt fix it #-o

---

