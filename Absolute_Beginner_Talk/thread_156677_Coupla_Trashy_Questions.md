---
title: "Coupla Trashy Questions"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by Max Roswell on 2006-04-07
Hey, all...

Still head over heels for Ubuntu.  Got a couple of quick trash/delete releated questions.

1.  I don't have any sort of Trash icon on my desktop.  Am I supposed to?

2.  I have a USB Flash memory reader that I use for my phone's MP3 player.  It mounts fine - all I do is copy MP3's over to the right directory, and everything works great.  However, when I want to change MP3's on the flash memory, I've been highlighting them and choosing "send to trash."  Eventually, I noticed that the card seemed to have much less memory available than I thought it should.  Through trial and error, I found it that a .Trash directory was created on the flash memory, and that's where all my files were going, and that's why the space was still used up.  So - what's a way to remove those files without creating a .Trash folder?  I'm comfortable on the command line; I'm just not sure what commands to use.

Thanks in advance!

---

### Post by aysiu on 2006-04-07
[QUOTE=Max Roswell]
1.  I don't have any sort of Trash icon on my desktop.  Am I supposed to?[/quote] No. It's on the panel. If it isn't, right-click on the panel and select "Add to Panel" and then find the trash.

> 
- what's a way to remove those files without creating a .Trash folder?  I'm comfortable on the command line; I'm just not sure what commands to use. In Nautilus' preferences, you can choose to have a delete command that bypasses the trash. If you set that and use it, files will be completely deleted instead of just sent to the trash.

---

### Post by jasay on 2006-04-07
[QUOTE=Max Roswell]Hey, all...
1.  I don't have any sort of Trash icon on my desktop.  Am I supposed to?
[/QUOTE]If you *want* one, start up gconf-editor in a terminal (it might in application > system tools I forget) and browse to apps > nautilus > desktop and enable "trash_icon_visible"

---

### Post by Heretic Monkey on 2006-04-07
You could also right click on a panel (any panel on the desktop) and click **Add to panel**.  There should be a Trashcan object in that menu.  
*EDIT* Sorry, just repeated what aysiu said earlier, didn't catch that until after i posted...

Either that, or you could use the " $ rm <filename.ext> " command from the command line.

---

### Post by Max Roswell on 2006-04-07
[QUOTE=aysiu]No. It's on the panel. If it isn't, right-click on the panel and select "Add to Panel" and then find the trash.

 In Nautilus' preferences, you can choose to have a delete command that bypasses the trash. If you set that and use it, files will be completely deleted instead of just sent to the trash.[/QUOTE]

Wow!  That thing's a trash can?  I don't know what I thought it was, but...well, thanks for pointing it out to me.

And the preference change in Nautilus worked like a charm.

Thanks -  you rule.

---

