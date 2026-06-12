---
title: "Gedit plugin"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by ncappel1 on 2007-05-31
Hi everyone, I am trying to install the gedit plugin, html tidy:[http://www.eng.tau.ac.il/~atavory/gedit-plugins/html-tidy/#download_inst](http://www.eng.tau.ac.il/~atavory/gedit-plugins/html-tidy/#download_inst)

but when I select it in the plugins window it goes grey (like html unfocus). I can't check the little box necessary to install it. Anyone have any ideas what I could be doing wrong? The directions seemed easy enough, (only three steps), so i know it has to be something simple, that's just slipping through my mind.

---

### Post by schwascore on 2007-06-13
I have the same problem. Here is the traceback source from the terminal, which might help solve this problem:

```
Traceback (most recent call last):
  File "/home/josh/.gnome2/gedit/plugins/html-tidy/__init__.py", line 26, in <module>
    import plugin
  File "/home/josh/.gnome2/gedit/plugins/html-tidy/plugin.py", line 33, in <module>
    import output_pane
  File "/home/josh/.gnome2/gedit/plugins/html-tidy/output_pane.py", line 33, in <module>
    import tidy_utils
  File "/home/josh/.gnome2/gedit/plugins/html-tidy/tidy_utils.py", line 30, in <module>
    import tidy_opt_utils
  File "/home/josh/.gnome2/gedit/plugins/html-tidy/tidy_opt_utils.py", line 27, in <module>
    import tidy
ImportError: No module named tidy

** (gedit:9892): WARNING **: Cannot load Python plugin 'HTML Tidy' since file 'html-tidy' cannot be read.

** (gedit:9892): WARNING **: Error activating plugin 'HTML Tidy'

```

---

### Post by mcduck on 2007-06-13
I think that plugin also needs you to install Tidy. It's in repositories, so 'sudo apt-get install tidy' might help.

---

### Post by schwascore on 2007-06-13
I already have tidy installed and I still get the same error.  Tidy works just fine when I run Quanta, but I have the same gedit plugin install problems as the original poster.

---

### Post by atavory on 2007-07-02
Hello,

  Short answer: Please retry now - I corrected this.
  Longer answer: The plugin was trying to import a python tidy *library* which wasn't installed on your system. This library was not really needed, and the fact that the plugin was trying to import it - is a bug.

  By the way: I wrote this plugin, but ran into your bug report by accident (and much after you posted it). In the future, you might perhaps try to file a bug report for gedit, or write this mailing list: [http://www.nabble.com/Gnome---Gedit-f1420.html](http://www.nabble.com/Gnome---Gedit-f1420.html)

  Bye,

  Ami

---

### Post by stanley45 on 2008-01-20
I can't find the command that lets me run the script from the console panel.  All it seems to do is run single line python commands, or multiline with \ .  I've tried F5 Ctrl-F5 and a few other guesses, but I haven't found it.

---

### Post by oxman on 2008-01-29
> **atavory said:**
> Hello,

  Short answer: Please retry now - I corrected this.
  Longer answer: The plugin was trying to import a python tidy *library* which wasn't installed on your system. This library was not really needed, and the fact that the plugin was trying to import it - is a bug.

  By the way: I wrote this plugin, but ran into your bug report by accident (and much after you posted it). In the future, you might perhaps try to file a bug report for gedit, or write this mailing list: [http://www.nabble.com/Gnome---Gedit-f1420.html](http://www.nabble.com/Gnome---Gedit-f1420.html)

  Bye,

  Ami

Shalom,

I also have attempted to use this fine utility but it fails to appear in my plugin preferences. I have even tried to install it as root in the main plugin file for gedit to no avail. Am I doing something wrong?

---

### Post by budx on 2008-05-03
> **atavory said:**
> Hello,

  Short answer: Please retry now - I corrected this.
  Longer answer: The plugin was trying to import a python tidy *library* which wasn't installed on your system. This library was not really needed, and the fact that the plugin was trying to import it - is a bug.

  By the way: I wrote this plugin, but ran into your bug report by accident (and much after you posted it). In the future, you might perhaps try to file a bug report for gedit, or write this mailing list: [http://www.nabble.com/Gnome---Gedit-f1420.html](http://www.nabble.com/Gnome---Gedit-f1420.html)

  Bye,

  Ami

Hello, i have tried to install the Plugin, and i have the same problems mentioned before and i have download the newest version.

So, where is my mistake.

Thanks in advance.
budx

---

### Post by King Louie on 2008-06-04
I am having the same problem. Tidy is installed. HTML-Tidy is in the gedit plugins directory. It appears in the plugins list in gedit prefs, but grays out as soon as I try to select it. I am running the latest version of Hardy.

---

