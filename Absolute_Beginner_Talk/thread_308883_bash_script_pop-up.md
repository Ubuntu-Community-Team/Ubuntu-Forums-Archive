---
title: "bash script pop-up"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by Sunborn on 2006-11-28
I have made a simple bash script (are they the same as shell scripts?) to run a program that doesn't like running from the launcher menu. 

The script works fine, permissions are set to execute. However, when I double click on the script, which is on my desktop, a dialog box pops up:

```
Do you want to run "smacx", or display its contents?
"suchandsuch" is an executable text file.

(Run in terminal) (Display) (Cancel) (Run)
```

Clicking on "Run in terminal" or "Run" does what I want it to do. Is there any way to bypass this prompt. The machine knows it is a script, the icon is different. Why can't I expect it to automatically run it?

I have searched over the bash scripting guides, but few even tell you how to even make the file. Most only cover syntax. 

Thanks

---

### Post by bodhi.zazen on 2006-11-28
In the gnome menu editor, in the command box, enter

```
bash /full/path_to/smacx
```

(In the box that currently has "emacs")

[img]http://www.linuxselfhelp.com/gnome/users-guide/figures/menueditor.png[/img]

---

### Post by Sunborn on 2006-11-28
Thanks, that was probably the ideal solution. I used alacarte but it worked the same.

---

### Post by taisao on 2006-12-09
nice, I use alacarte too, with that you can just browse to the script file and save the settings

---

