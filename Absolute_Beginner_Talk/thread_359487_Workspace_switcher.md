---
title: "Workspace switcher"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2007-02-12
Hello you,

My workspace switcher shows only one workspace but the number of workspaces is 2! 
If I remove it from panel and add it again I get this error message: 
> An error occurred while loading or saving configuration information for gnome-panel. Some of your configuration settings may not work properly.
> Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names' specified for `/apps/panel/applets/applet_1/prefs/display_workspace_names' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_1/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_1/prefs/num_rows' stores a non-schema value

Could you guide me how I can fix it?

Thanks,

---

### Post by linux-beginner on 2007-02-12
It's solved by command: "killall gnome-panel"

---

