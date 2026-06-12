---
title: "Linux OCR solution (Lios)"
date: 2023-07-29
forum: Assistive Technology &amp; Accessibility
---

### Post by stondcyborg-x on 2023-07-29
Ubuntu 22.04.2 LTS


I install Lios with the Software Center, whisout any Problems and i try sudo apt-get install lios. 
All dependencies are installed[COLOR=#1F2328][FONT=-apple-system]: python3, python3-imaging-sane|python3-sane, python3-speechd, tesseract-ocr, imagemagick, cuneiform, espeak,poppler-utils, python3-enchant,aspell-en, gir1.2-gst-plugins-base-1.0, gir1.2-gstreamer-1.0[/FONT][/COLOR]

When i try to start Lios i get :

 $ lios

Traceback (most recent call last):
  File "/usr/bin/lios", line 3, in <module>
    from lios.main import *
  File "/usr/local/lib/python3.10/dist-packages/lios/main.py", line 27, in <module>
    from lios import scanner, editor, imageview, cam, ocr, preferences, speech
  File "/usr/local/lib/python3.10/dist-packages/lios/editor.py", line 20, in <module>
    from lios.ui.gtk import text_view, tree_view, widget, dialog, file_chooser, containers, window
  File "/usr/local/lib/python3.10/dist-packages/lios/ui/gtk/text_view.py", line 21, in <module>
    import gi
  File "/usr/lib/python3/dist-packages/gi/__init__.py", line 102
    repository = Repository.get_default()
                                         ^
IndentationError: unindent does not match any outer indentation level

any idea???

---

### Post by TheFu on 2023-07-29
Python, as a language, is indentation sensitive.  Appears that at least 1 file was either corrupted locally or incorrectly modified by the project team.  If you didn't modify the file, then report that issue as a bug to the **lios** project. Hopefully, they will know the 'gi' project team and can get line 102 fixed.

Of course, you could try to see if the indentation for 
```
File "/usr/lib/python3/dist-packages/gi/__init__.py", line 102
```
is correct or not.

BTW, whenever posting terminal output to these forums, it would really help if you wrapped that output in forum code tags.

---

### Post by stondcyborg-x on 2023-07-30
> **TheFu said:**
> Python, as a language, is indentation sensitive.  Appears that at least 1 file was either corrupted locally or incorrectly modified by the project team. 


.

ok i see that there is a lot more wrong,the project team has to work on it

and thank you for your answer

---

### Post by TheFu on 2023-07-30
> **stondcyborg-x said:**
> ok i see that there is a lot more wrong,the project team has to work on it

and thank you for your answer

I doubt it really is that big of an issue.  Just 1 space character in the wrong place could be sufficient to make python refuse to work. It is probably just that. Tiny, trivial, issue and not in the Lios project, but in one of the dependent modules.  That's my guess.

I hate indentation-sensitive languages.

---

