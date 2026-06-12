---
title: "Skencil"
date: 2007-09-03
forum: Art &amp; Design
---

### Post by melfindlay on 2007-09-03
I installed Skencil throught the Synaptic Package Manager, but when I clicked on it through 'Graphics' it didn't load. So, then I went to run it through the terminal but I got this message:

Segmentation fault (core dumped)


I take it that's not a good thing. Can someone help me out?

Thanks a ton!

---

### Post by David Valentine on 2007-10-17
<bump>

I am getting the same error.  This bug has apparently been around a while--it's a shame that stuff from the repos sometimes just doesn't work, and no answers are forthcoming about how to deal with it.

---

### Post by elsaturnino on 2007-10-23
Same problem here... 'tis a real shame...

---

### Post by hasinasi on 2007-10-26
Same problem here on a recent, fresh install of Kubuntu 7.10 (Gutsy).
In some other forums (see URL below) I have found that it may be related to the version of python: v2.4 seems to work, v2.5 not. I have v.2.5.1 installed (test it with "python -V").

That's one of the links:
[http://www.nabble.com/seg-fault-t3973055.html](http://www.nabble.com/seg-fault-t3973055.html)

Any idea anyone?
--hasi.

---

### Post by n2dabloo on 2009-01-11
I've downloaded Skencil throught the Synaptics Package Manager.  I'm using Ubuntu 8.10.  Mine won't start either.  I went to the Skencil site ( [http://www.skencil.org/faq.html#FAQ2.1](http://www.skencil.org/faq.html#FAQ2.1) ) and saw that I needed the Python Imaging Library.  I checked the "Manager" and saw that I already have that installed, it's version 1.1.6-3  Rats, I really wanted to experiment with another graphics program.  One look at the gallery: [http://www.skencil.org/gallery.html](http://www.skencil.org/gallery.html) and I really wanna get my hands on it.

---

### Post by InfernalNeutrino on 2009-01-29
I am also having issues getting it to work on an Xubuntu 8.10 install... I installed it via synaptic and get the following when I attempt to run it:

> 
skencil
shared memory images supported
Traceback (most recent call last):
  File "/usr/bin/skencil", line 34, in <module>
    Sketch.main.main()
  File "/usr/lib/skencil/Sketch/Base/main.py", line 148, in main
    run_script = options.run_script)
  File "/usr/lib/skencil/Sketch/UI/skapp.py", line 183, in __init__
    self.build_window()
  File "/usr/lib/skencil/Sketch/UI/skapp.py", line 223, in build_window
    self.run_script)
  File "/usr/lib/skencil/Sketch/UI/mainwindow.py", line 98, in __init__
    self.build_menu()
  File "/usr/lib/skencil/Sketch/UI/mainwindow.py", line 901, in build_menu
    self.update_mru_files()
  File "/usr/lib/skencil/Sketch/UI/mainwindow.py", line 380, in update_mru_files
    self.file_menu.RebuildMenu()
  File "/usr/lib/skencil/Sketch/UI/tkext.py", line 367, in RebuildMenu
    self.menu.delete(0, END)
  File "/usr/lib/python2.5/lib-tk/Tkinter.py", line 2683, in delete
    if c in self._tclCommands:
TypeError: argument of type 'NoneType' is not iterable


I'm not much of an expert, but it seems that its the interface between python and tk that is at issue. Perhaps the version of either one affects it. If and when I get some free time I'll try playing around with it, but for now I'm stuck. Of course if anyone has insight into the problem it would be most welcome :)

---

### Post by hasinasi on 2009-01-29
@InfernalNeutrino: 

from looking at the project's web page, it looks like it has been inactive for several years. Last time I tried installing it, I ran into some serious issues with libraries, as well. (Some libs on my machine were too new to be compatible with the program.) 

Is there a particular reason you want to use skencil? I have become an extremely happy user of inkscape, which is a quite advanced program, in my opinion.

---

### Post by InfernalNeutrino on 2009-01-31
Not particularly. The short story is that I'm a grad student who recently had the sudden need to create some figures, so I just went through the repository looking for something to do it. Skencil was the first interesting one I ran across, so I downloaded it and promptly got those errors. Since then I've tried out Xara and inkscape, but haven't settled on anything yet. You did raise a good point regarding the lack of activity on the project, so I think I'll just decide between xara and inkscape and be done with it. Cheers!

---

### Post by srilyk on 2009-03-08
Good news for anyone trying out Skencil (as far as I've tried):

You can at least get it to start up (I haven't tried any further fun yet) by altering one single line of code.

If you installed via apt-get you should be able to type

```
cd /usr/lib/skencil/Sketch/UI/
```

then (replacing vi with your editor of choice, i.e. gedit/emacs/etc)

```
sudo vi tktext.py
```

Now jump to line 367 (or search for self.menu.delete and that /should/ take you there. The bit of code you want to edit is this:

```
365     def RebuildMenu(self):
366     if self.entries is not None:
367         self.menu.delete(0, END)

```

Change it to this:

```
365     def RebuildMenu(self):
366     if self.entries is not None:
367         pass#self.menu.delete(0, END)

```

save, and quit. Actually, you should probably just save and see if it runs. If you run from terminal, you may get an error message that looks like this:

```
wayne@sir-arthur:~$ skencil 
Traceback (most recent call last):
  File "/usr/bin/skencil", line 34, in <module>
    Sketch.main.main()
  File "/usr/lib/skencil/Sketch/Base/main.py", line 142, in main
    Sketch.init_ui()
  File "/usr/lib/skencil/Sketch/__init__.py", line 187, in init_ui
    __import__(name)
  File "/usr/lib/skencil/Script/export_raster.py", line 47, in <module>
    from Sketch.UI.sketchdlg import SKModal
  File "/usr/lib/skencil/Sketch/UI/sketchdlg.py", line 69, in <module>
    from tkext import UpdatedButton
  File "/usr/lib/skencil/Sketch/UI/tkext.py", line 367
    pass
       ^
IndentationError: expected an indented block

```

Which means your indention level is not what python expects (search wikipedia for dynamic whitespace if you care to learn more)

The best way to edit that line is to put your cursor in front of the 's' in "self" and type "pass#" - the # is a comment character which tells python to ignore the delete part. This might give you weird errors when skencil tries to redraw a menu (such as not removing all the menu elements), but I'm not sure how often that occurs.

Anyway, hope this helps!

---

### Post by PlaidRadish on 2009-04-16
Works!  For anyone with the...

[INDENT]***TypeError: argument of type 'NoneType' is not iterable***[/INDENT]

...error, this is a SCORE!  (I posted the quote, hoping this would help people find this solution, as there are several guesswork solutions on the web, and this is the only one that actually does work, so far.)


*Note: Make sure you have the 

[INDENT]***TypeError: argument of type 'NoneType' is not iterable***[/INDENT]

...error, and nothing else, as this is the only error that is solved by this solution.

Thanks a million, srilyk!!!

---

### Post by chaanakya_chiraag on 2009-05-12
Thanks srilyk!  By the way, it also works if you get the ```
TclError: can't delete Tcl command
``` error.  Thanks again :)

---

### Post by celiapgt on 2009-08-04
Thank you very much, srilyk
It worked for me in Ubuntu 9.04 Jaunty Jackalope

---

### Post by drefooty on 2009-09-15
Thank you!
The solution in this string resolved my problem with Skencil as well.
Ubuntu 9.04 Jaunty Jackalop

---

