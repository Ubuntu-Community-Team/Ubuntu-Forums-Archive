---
title: "How to open file in gedit from terminal command line"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Opally on 2006-12-14
Hello,

New Ubuntu user here. I've set up Ubuntu Dapper Drake LAMP, and have Ruby on Rails working as well, MANY thanks to all the splendid instructions and dialogue posted on these boards, the wiki, and elsewhere.

However.

While I am somewhat comfortable using a command line (my computer use pre-dates Windows, after all... showing my age...) still, after years of using a graphical environment, I like seeing stuff like a browsable folder schema, etc.

So I followed some instructions to install a lightweight Gnome environment on my little server. 

So far so good. (I even installed Eclipse and RadRails. And Adobe Reader.)

However. Sometimes I need to edit files, and although I've had VI demonstrated to me, I just find it hard to adapt to. 

When I try to open a text file in gedit, I use a command line like this:

```
gedit controller_say.rb
```

Then I get this returned to me:

```
ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:4981): WARNING **: Could not load python module modelines


** (gedit:4981): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:4981): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed
/bin/sh: /usr/bin/esd: No such file or directory

** (gedit:4981): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:4981): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:4981): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:4981): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:4981): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:4981): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:4981): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:4981): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:4981): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

```

However, the document does open.

What is causing this error?

EVEN better... if I see a problem like this, how can I research what it means, and what packages I am missing? Teach a woman to fish, etc. 

Apologies for my n00biness!

---thanks,

---Opally

---

### Post by igknighted on 2006-12-14
I think the issue may lie with the fact that you installed a lightweight GNOME.  Probably not all the available gedit plugins were installed and it is just saying they aren't there.  I get similar messages opening kate from a terminal in KDE so I am kind of used to seeing stuff like that.

---

### Post by taurus on 2006-12-14
```
nano -w controller_say.rb
```

p.s.  That's just a warning so don't worry about it...

---

### Post by annda on 2006-12-14
it looks like the library needed for syntax highlightling (libgtksourceview) is missing. try to install it via Synaptic, or in the terminal
```
sudo aptitude install libgtksourceview
```

---

### Post by Opally on 2006-12-14
you guys are FAST!

Well after I posted I did a search on gedit_plugin_update_ui and found several threads of people reporting the same problem. I did search before I posted, but on vague terms like "gedit terminal"

I did find a solution here:

[http://www.ubuntuforums.org/showthread.php?t=216151&highlight=gedit_plugin_update_ui](http://www.ubuntuforums.org/showthread.php?t=216151&highlight=gedit_plugin_update_ui)

which, to summarize, is to remove /usr/lib/gedit-2/plugins/modelines.gedit-plugin.

That does seem a bit harsh.

Rather than switch to nano, I'll try your suggestion, Annda.

---

### Post by Opally on 2006-12-14
Now I have these libraries installed, but the problem remains: (and I already had libgtksourceview1.0-0 and libgtksourceview-common installed)

libgtksourceview1.0-0
libgtksourceview1-ruby
libgtksourceview-common
libgtksourceview-dev

Back to removing the modelines file.

Modelines seems to have something to do with screen resolution.

A search of Synaptic turns up modeline files for Kate (for Kubuntu) and Emacs, but nothing for gedit. 

Oh well, the workaround works anyhow!.

Thank you for your suggestions. I'll check back to see if more suggestions come in. These issues help me understand Linux just a bit better.

---

