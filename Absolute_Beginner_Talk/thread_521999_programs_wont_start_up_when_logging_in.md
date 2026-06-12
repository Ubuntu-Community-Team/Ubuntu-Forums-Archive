---
title: "programs wont start up when logging in"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by TheOtherLinuxFreak on 2007-08-10
When I log in none of my programs that I have made to start up automatically don't.  this happened after I installed compiz fusion and added the command compiz --replace in my sessions thing. when I open the system monitor it says that gdesklets, compiz, etc are running but there not. When I go to gdesklets through the menu it doesn't work ether.  compiz work fine when I start it up manually using compiz --replace -c emerald &.

thanks for your help!

---

### Post by DSn0wMan on 2007-08-10
It is possible that compiz is just starting so slowly you think it's not working. When I first installed compiz I thought it broke my screenlets, but what was happening was that it was taking so long to load the alot of other things just where not loading. 

Check out this post [http://ubuntuforums.org/showthread.php?t=482776](http://ubuntuforums.org/showthread.php?t=482776)

Basically this fixed my problem ....

"What you need to do is to set metacity as the window manager to start with again. Open up gconf (alt-f2 and run gconf-editor) and navigate to /desktop/gnome/applications/window_manager and change the value of "default" to metacity (or any other fast loading window manager). Then go to your session gui (alt-f2 and run gnome-session-properties) and put in a new startup program. Call it what you want (compiz-fusion possibly?) and use the command `compiz --replace` Make sure it is checked and your done!"

---

### Post by TheOtherLinuxFreak on 2007-08-10
now I reinstalled ubuntu and i'm going to try installing compiz-fusion again.

---

### Post by DSn0wMan on 2007-08-10
good luck!

---

