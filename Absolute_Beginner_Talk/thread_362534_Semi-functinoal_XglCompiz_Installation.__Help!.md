---
title: "Semi-functinoal Xgl/Compiz Installation.  Help!"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by caecusum on 2007-02-15
Let me note, I've read the stickies.  I know this is considered "off-topic".  But it's still a beginner question, I don't know where else to ask it.

I followed the installation instructions to the letter from the Unofficial 6.10 Starter Guide, I even copy/pasted much of the text to make sure typos weren't going to be an issue.  I rebooted the system and everything launched normally.

Here's the weird part.  I get some fancy effects when I alt/tab to switch windows, and a nice fade when I change workspaces by clicking the icons on the toolbar using the mouse.  What I don't get, is anything else.  It even seems to have destroyed some of my keyboard shortcuts.  I used to be able to switch workspaces with ctrl-alt-arrowkeys, which doesn't work anymore.  Furthermore, I went back into system->preferences->keyboard shortcuts and the option to reset that shortcut is gone alltogether.  Switching workspaces just isn't on the list.  What's going on?  None of the listed commands on xgl/compiz tip sheets online do anything, except for alt-tab.  Where's the fancy cube of workspaces?  Where are the shimmering windows when I move them around?  I can't even find a preferences (GUI or non) for any of the xgl/compiz settings.  Help me.  Did something not install correctly?

---

### Post by chuckyp on 2007-02-15
Basically you need to play with the compiz settings.  There are compiz managers that will give you a nice fancy GUI to do this but their names escape me atm.

To fix it now you can alt+f2 and run gconf-editor.  gconf-editor lets you configure a meriad of things on all your programs installed.  If you navigate in there to Apps> Compiz > plugins.   You will be able to define keys for each feature you are looking for.  If you need more help there are plenty of people on irc hanging out in #ubuntu-effects on the irc.freenode.net server.

---

