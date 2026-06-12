---
title: "Installed Programs?"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by Genius314 on 2006-12-22
I need to know where Ubuntu installs program files.
I looked all over but can't find anything.
Mainly what I'm looking for is where to find the logs and smilies for Gaim, since I had a bunch from Windows, and now I want to move them to this OS.
Thanks.

---

### Post by goatflyer on 2006-12-22
Most programs are installed in /usr/bin  but there are other places too.
If you know the name of the program, and it is installed on your system, you could type in terminal:

```

which gaim

```


You add new smiley themes in gaim by dragging and dropping onto the Smiley Theme List.  Open Preferences on the login pane, under Interface>Conversations>Smiley Themes.

---

### Post by taurus on 2006-12-22
And your personal settings will be in ~/.gaim...

---

### Post by jem7v on 2006-12-22
Additionally, many programs that log things will save them in a hidden folder in your Home folder. For example, Gaim is probably in ~/.gaim or something like that. Go View->Show Hidden Files in your file browser or Ctrl+H to show the hidden folders in your home folder. Lots of program settings and custom icons and things like that just get saved in hidden folders.

(Edit: And apparently I type slowly.)

---

### Post by Genius314 on 2006-12-22
Ah, ok. Now I see it. Thanks.
Now I have to rename all of these log files to match the new name format. Luckily there's a tool for that... (But it seems to be beta. Hopefully it won't mess anything up. But if it does, I have two more copies of these logs. Heh.)

---

