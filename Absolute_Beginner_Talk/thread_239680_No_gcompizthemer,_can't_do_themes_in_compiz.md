---
title: "No gcompizthemer, can't do themes in compiz"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by raggit on 2006-08-19
I really want to be able to install themes for my compiz installation.
I have a few weird things going on though, when i try to add gcompizthemer via the package manager it's not there, when i add the repositories for it, well it's still not there.  Also when I goto gset-compiz in the sys tray and then to preferences & try to add shortcuts the shortcuts don't stay.  The cube effect doesn't quite work either, most screenshots I see of the cube show the entire cube, I can't get that look on mine.  
any help on these matters greatly appreciated

---

### Post by bulldog on 2006-08-19
Well it's not compiz themer anymore,you should look for cgwd and cgwd-themes
in your pakket manager.
And you have to change something in your compiz-start script,otherwise you can't use it.

About the cube,it's all depending on your settings.
You can see the cube from the outside or from the inside.
Start Gset-compiz ->plugins and select cube.
In the top-left corner unselect in the cube to see the outside off the cube.

You can rotate the cube with CTRL-ALT-leftmouse  and move your mouse to rotate.

---

### Post by raggit on 2006-08-19
where can i find the compis-start script?  I'll go dig around in there. Do you know what I need to change?

I also went and changed the selection in gset-compiz cube plugin but it's like I don't see an entire cube at all, the screen just looks normal.  Am I suppose zoom out somehow?  After all I have a thinkpad and there is no magic/superkey so to speak.

---

### Post by bulldog on 2006-08-19
It's in /usr/bin
But what tutorial did you use?

I used a python script and here is a part of it you should change like mine.

def start_compiz():
	os.system("killall gnome-window-decorator")
	gobject.spawn_async(['cgwd'], \
			     flags=gobject.SPAWN_SEARCH_PATH)
	gobject.spawn_async(['compiz', '--replace', 'gconf'], \
			  flags=gobject.SPAWN_SEARCH_PATH)

If you used another script like "the future" or Compiz-start
it's a little different.
You can find all info and eventually ask help on the compiz forum.

[http://www.compiz.net/index.html](http://www.compiz.net/index.html)

---

### Post by raggit on 2006-08-19
Going to give this a try
[http://jaganath.wordpress.com/2006/07/23/making-compiz-themes-work/](http://jaganath.wordpress.com/2006/07/23/making-compiz-themes-work/)

---

### Post by digby on 2006-08-19
> **raggit said:**
> where can i find the compis-start script?  I'll go dig around in there. Do you know what I need to change?

I also went and changed the selection in gset-compiz cube plugin but it's like I don't see an entire cube at all, the screen just looks normal.  Am I suppose zoom out somehow?  After all I have a thinkpad and there is no magic/superkey so to speak.

I've attached a copy of my compiz-start.py  - You'll have to rename it to the original extension (.py) because the forum doesn't accept that sort of upload.  I had this placed in /usr/bin and started it automatically when the session began.  It may need some slight modifications for your system, but we need to know which tutorial you used to install xgl/compiz to help you with that.

---

