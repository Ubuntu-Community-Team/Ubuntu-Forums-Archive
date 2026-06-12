---
title: "Anyone using a dark GTK theme that WORKS?!"
date: 2007-04-26
forum: Art &amp; Design
---

### Post by RAdams on 2007-04-26
How do I exclude an application from a GTK theme I've set in the Themes control panel? Or, better yet, how can I fix the fact that EVERY dark gtk theme makes my firefox and evolution menus illegible, makes the text in some input boxes on web sites impossible to see, makes mail displayed in evolution illegible, etc., etc., etc.?

Is anyone using a dark GTK theme that works?

---

### Post by kpolice on 2007-04-26
Firefox is the buggy application not the theme.

About evolution could you post a screenshot?

---

### Post by klepas on 2007-04-26
You can specify a GTK application to use a specific GTK theme/gtkrc file as follows (eg. gimp-2.3):
```
GTK2_RC_FILES=$HOME/.themes/Darkilouche/gtk-2.0/gtkrc gimp-2.3
```

As for a dark theme, have you tried [Darkilouche]("http://jimmac.musichall.cz/weblog.php//Artwork/Darkilouche.php")?

---

### Post by wh0rd on 2007-04-26
Check this thread out, it deals with the dark theming issues in Gnome: 
[http://ubuntuforums.org/showthread.php?t=411351&highlight=black+theme+font+gnome](http://ubuntuforums.org/showthread.php?t=411351&highlight=black+theme+font+gnome)

---

### Post by kpolice on 2007-04-27
To fix firefox, e.g. text areas, input boxes, buttons, etc. inside web pages like these forums you don't have to mess with system files, just edit your userContent.css file and inside paste:
```
input,textarea{
	background: #fff !important;
	color: #000 !important;
	border: 1px solid #aaa;
}
```

The border part isn't really needed but it looks better :P

If the file doesn't exist just create it in:
```
$HOME/.mozilla/firefox/yourProfile/chrome
```

---

### Post by RAdams on 2007-05-01
> **kpolice said:**
> To fix firefox, e.g. text areas, input boxes, buttons, etc. inside web pages like these forums you don't have to mess with system files, just edit your userContent.css file and inside paste:
```
input,textarea{
	background: #fff !important;
	color: #000 !important;
	border: 1px solid #aaa;
}
```

The border part isn't really needed but it looks better :P

If the file doesn't exist just create it in:
```
$HOME/.mozilla/firefox/yourProfile/chrome
```

That worked great! Now, is there a way to fix the menubar at top and the right-click menu? :)

---

### Post by RAdams on 2007-05-01
> **kpolice said:**
> Firefox is the buggy application not the theme.

About evolution could you post a screenshot?

After messing around I found that some other people's email clients format text message as HTML, turning already black text to... black text! :(

Why, why, why. Oh well; I can fix that by forcing incoming messages to be text only, I suppose.

---

### Post by RAdams on 2007-05-01
> **wh0rd said:**
> Check this thread out, it deals with the dark theming issues in Gnome: 
[http://ubuntuforums.org/showthread.php?t=411351&highlight=black+theme+font+gnome](http://ubuntuforums.org/showthread.php?t=411351&highlight=black+theme+font+gnome)

That works fine for me from terminal, but not from a launcher... I get "no such file or directory". :(

---

