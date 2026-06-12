---
title: "PyGTK Help"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by wile_e8 on 2006-02-26
Ok, I was messing around trying to get gDesklets installed on my computer as described in [post=692118]this[/post] post, but the step to update PyGTK seems to have broken PyGTK for other applications.  For example, here are the errors I get when trying to run smeg and gmail-notify
```
wile_e8:~$ smeg
Traceback (most recent call last):
  File "/usr/bin/smeg", line 31, in ?
    from DialogHandler import DialogHandler
  File "/usr/lib/smeg/DialogHandler.py", line 30, in ?
    import gtk, gtk.glade
  File "/usr/local/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 33, in ?
    import gobject as _gobject
ImportError: /usr/local/lib/python2.4/site-packages/gtk-2.0/gobject.so: undefined symbol: PyUnicodeUCS2_FromUnicode
wile_e8:~$ gmail-notify
Traceback (most recent call last):
  File "./notifier.py", line 9, in ?
    from egg.trayicon import TrayIcon
ImportError: No module named egg.trayicon

```

I've tried reinstalling python2.4-gtk2 through synaptic, but that doesn't help.  What would I need to do to fix these errors that seem to be occurring whenever I run an application that uses PyGTK?

---

### Post by Xian on 2006-02-26
[QUOTE=wile_e8]I've tried reinstalling python2.4-gtk2 through synaptic, but that doesn't help.  What would I need to do to fix these errors that seem to be occurring whenever I run an application that uses PyGTK?[/QUOTE]

Did you remove the python app(s) you installed from source?

---

### Post by wile_e8 on 2006-02-26
Actually, I never got around to installing gDesklets (the last step in the original link) because I noticed the problem before I did.  I haven't even installed the app I made the changes for but I have screwed up other ones. Quality, I know....

---

### Post by Xian on 2006-02-26
[QUOTE=wile_e8]Actually, I never got around to installing gDesklets (the last step in the original link) because I noticed the problem before I did. [/QUOTE]

Right, but did you install any of the other python apps?? You said, "the step to update PyGTK seems to have broken PyGTK for other applications", so how far did you get into that step and did you actually install anything? If you did then reinstalling an older binary version on top of that will have little useful effect.

---

### Post by wile_e8 on 2006-02-26
Oh, I finished all of the steps (apparently successfully, at least that's what the output said, although I'll disagree with the results).  Do I need to delete the current version I installed before I try the synaptic install?  How would I do that?

---

### Post by Xian on 2006-02-26
[QUOTE=wile_e8]Do I need to delete the current version I installed before I try the synaptic install?  How would I do that?[/QUOTE]

Yeah, if you finished the source install (that's the method described in the link you provided) of those python applications, then it remains on your system even if you reinstall an older version of the same library using APT or Synaptic. That is because Synaptic can't keep track of source packages and has absolutely no idea they even exist on your system. Having different versions of the same package installed can cause issues.

To remove them you need to go back into the build directory, which is the folder that you issued the 'make' and 'make install' commands in, and run another command to (hopefully) remove it permanently. The command is listed below:

$ sudo make uninstall

---

### Post by wile_e8 on 2006-02-26
OK, that worked.  Now I'm getting new errors, probably because the terminal can't find gtk or pygtk.  Here are the exact errors I get
```
wile_e8:~$ smeg
Traceback (most recent call last):
  File "/usr/bin/smeg", line 31, in ?
    from DialogHandler import DialogHandler
  File "/usr/lib/smeg/DialogHandler.py", line 30, in ?
    import gtk, gtk.glade
ImportError: No module named gtk
wile_e8:~$ gmail-notify
Traceback (most recent call last):
  File "./notifier.py", line 4, in ?
    import pygtk
ImportError: No module named pygtk
```
I tried reinstalling from synaptic (again) thinking that now that the old source was gone, this would reinstall fine.  But it looks like wherever my Ubuntu is looking for these files is now gone (from the unintall) and hasn't been changed to the versions from synaptic.  Is this right?  How would I fix this?

---

### Post by Xian on 2006-02-26
[QUOTE=wile_e8]Is this right?  How would I fix this?[/QUOTE]

Well, the basic idea here in hopes of recovering your system is to (1) remove the source packages that you installed, and (2) reinstall their counterparts in Synaptic. This is in an effort to get everything back to where it was before you started. If you have verified that you have performed these actions completely, and are still encountering problems, then it may not be fixable.

---

### Post by wile_e8 on 2006-02-26
[QUOTE=Xian]If you have verified that you have performed these actions completely, and are still encountering problems, then it may not be fixable.[/QUOTE]

Oh, sweet.  So I went through synaptic, searched for "python gtk", and reinstalled all the packages that were already installed, but I kept getting the same errors.  Anything else I should try to reinstall/remove then install again?  Or have a pretty much verified that I'm in trouble?

---

### Post by Xian on 2006-02-26
If it were my box I'd be out of ideas for what that's worth.
But I'm no expert....
I have no other suggestions to get you back to the original state.

The two pkgs you are interested in are python and pygtk.
Which probably goes by the name python-gtk in Ubuntu.

Edit: Oh, you might be sure and install the dev files (python-gtk2-dev).
When you install from source those libs are often included.

---

### Post by wile_e8 on 2006-02-26
OK Thanks for the help

---

### Post by wile_e8 on 2006-02-27
FWIW I searched the forums and found someone with a similar problem.  Although my initial cause is different, the guy in [thread=123415]this[/thread] thread gets all the same errors as me, right up to the error at the end that they can't fix either.  Maybe that will help, I don't know, worth a try.

---

### Post by wile_e8 on 2006-02-28
OK, fixed it.  The instruction post put a version of python at /usr/local/bin/python, and this was running instead of /usr/bin/python.  Once I deleted the new version, the ubuntu version ran, and everything is working correctly.  Thanks again for the help.

---

