---
title: "gedit import error"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by RRS on 2006-06-08
FOr quite some time now, can't really remember how long, whenever I open an /etc/ file with gedit I've gotten; 

```
ImportError: could not import gtksourceview
```
Since the file always opens and I'm able to edit, save, etc. I've just sort of ignored it.

However the last time I also got this;

```
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:5188): WARNING **: Could not load python module modelines


** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

```

The file still opened in gedit and I was able to make my changes with no problem as usual.

I guess maybe with this extra info someone can help point me in the right direction to research what, if any, problem I might have. 

My gut warns me that eventually whatever's the source of these error messages will actually create a problem rather then just the current bit of annoyance.

Thanks for any advice.

---

### Post by nanotube on 2006-06-09
[QUOTE=RRS]FOr quite some time now, can't really remember how long, whenever I open an /etc/ file with gedit I've gotten; 

```
ImportError: could not import gtksourceview
```
Since the file always opens and I'm able to edit, save, etc. I've just sort of ignored it.

However the last time I also got this;

```
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:5188): WARNING **: Could not load python module modelines


** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5188): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

```

The file still opened in gedit and I was able to make my changes with no problem as usual.

I guess maybe with this extra info someone can help point me in the right direction to research what, if any, problem I might have. 

My gut warns me that eventually whatever's the source of these error messages will actually create a problem rather then just the current bit of annoyance.

Thanks for any advice.[/QUOTE]
well, my first try would be to uninstall and reinstall gedit, and see if that does anything. ..

---

### Post by jasonwjones on 2006-06-19
I finally figured this out.  I have Xubuntu installed and it doesn't have all of the gnome python files installed by default.  By installing python2.4-gnome2-desktop from synaptic, it cleared up the root gedit error (not having gtksourceview as a python module).  Hope this helps!

---

### Post by RRS on 2006-06-19
Thanks, had sort of forgotten I'd posted on this.

Checked synaptic and python2.4-gnome2-desktop wasn't installed, it is now though.

Unfortunately all it semed to do was change the error message. Now I get:
```
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
```
But gedit still opens the file properly so it remains only an annoyance instead of a problem.

BTW, I'm running gnome (Ubuntu) rather then Xubuntu so that's probably why the fix worked for you.

Thanks anyway :)

---

