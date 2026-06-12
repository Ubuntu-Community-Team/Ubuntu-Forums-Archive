---
title: "How do I make a screenshot?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by pdxuser on 2007-03-18
I want to make a screenshot.  I'm using Xubuntu.  Do I need to download a new application for that?

---

### Post by Hortinstein on 2007-03-18
Applications->Accessories->Take Screenshot

---

### Post by fjf314 on 2007-03-18
Pressing the Print Screen key should also do the trick.

---

### Post by pdxuser on 2007-03-18
I think this may be a difference between Xubuntu and Ubuntu.  There's no Take Screenshot command in the Accessories menu, and there's no set keyboard shortcut for Print Screen.

---

### Post by chuckyp on 2007-03-18
Pressing Alt+Print Screen will take a screenshot of the current application in focus.  Just print screen will take a screen shot of the entire desktop.

---

### Post by pdxuser on 2007-03-18
Ok, I see that there's a Take Screenshot package in the Add/Remove Applications list.  I'll just download that.

BTW, Is it perfectly ok to download GNOME or KDE packages in Xubuntu?

---

### Post by fusiachi on 2007-03-18
It will work, but in some ways it negates the purpose of using xfce.

---

### Post by pdxuser on 2007-03-18
Hm, Take Screenshot is bundled with Dictionary, Disk Usage Analyzer, and Floppy Formatter.  I don't really want those.  Can I target those for removal later, or will I just have to take the whole collection?

---

### Post by pdxuser on 2007-03-18
> **fusiachi said:**
> It will work, but in some ways it negates the purpose of using xfce.

Xfce's main selling point is that it's more resource-efficient, right?  But if there's no Xfce analog to a GNOME package I want, it seems like installing that GNOME package is my only choice, no?  And wouldn't it affect my system resources only at those times when I'm actually running the application?  Other than storage space, I don't really see how such a package would be taxing on my machine when it's dormant.  Am I getting this right?

---

### Post by yabbadabbadont on 2007-03-18
If you want something small and don't mind a command line tool, scrot will do what you need.  You could setup a keyboard shortcut for it too.  If you don't like scrot, imagemagick includes the "import" utility that can take either full screenshots or just the selected window.

---

### Post by pdxuser on 2007-03-18
Wait, I found the following:

/usr/lib/xfce4-screenshooter-plugin/xfce4/panel-plugins/xfce4-screenshooter-plugin

But when I run it, nothing is copied to the clipboard....

---

### Post by yabbadabbadont on 2007-03-18
Look in your home directory.  It probably created a file there with the screenshot.

---

### Post by pdxuser on 2007-03-18
There's nothing new in my home directory, but I realized from the directory "panel-plugins" that it was something I could add to a panel.  I did that, and now I have a little camera icon on my panel that will take a screenshot when I click it and then ask me where to save it.  I don't really want another thing on my panel, though, and I would prefer it just put the screenshot in my clipboard. :-(  I'll go look at this scrot thing.

---

### Post by yabbadabbadont on 2007-03-18
I don't know of any linux screenshot program that puts the image in the "clipboard".  Especially since there are different clipboards depending on what you are doing.  :)  There is the one used when selecting text on the console.  Then there is the X selection.  Then there is usually another one provided by the desktop environment you are currently using (if any).  KDE provides one, so does Gnome, and I assume that XFCE does too.  I use Fluxbox and it doesn't.  Remember, this isn't Windows.  ;)

---

### Post by pdxuser on 2007-03-18
Isn't having an X selection and a DE selection redundant?  How do they differ in function?  What I would like to do, I suppose, is make Print Screen the shortcut for my screen capture utility, then make the result of that screen capture the X (or DE?) selection, turning this:

- Click screen capture icon
- Save as file x
- (Alt-Tab) Switch to image editor
- (Ctrl-O) Open
- Select file x
- Click OK
- (Ctrl-A) Select all
- (Ctrl-C) Copy
- (Ctrl-Tab) Switch to previously open window
- (Ctrl-V) Paste

...into this:

- PrtScr (Capture screen as X/DE selection)
- Alt-Tab (Switch to image editor)
- Ctrl-V (Paste into previously open window)

---

### Post by yabbadabbadont on 2007-03-18
> **pdxuser said:**
> Isn't having an X selection and a DE selection redundant?

No, because you can have X without a DE.  In fact, that is how I run it.

There may exist a program that does what you wish, but I've never heard of one in Linux.  Good luck on your search though.  :)

---

### Post by pdxuser on 2007-03-18
Does the DE selection supersede the X selection, so that copy-and-paste in X/K/Ubuntu always uses the DE selection, leaving the X selection unused?

---

### Post by yabbadabbadont on 2007-03-18
No idea.  Sorry.

---

### Post by tommie74 on 2007-04-08
If you want to take a screeenshot in Xubuntu, right click the panel, choose add new item and then choose screenshot from the available list. Answer the settingsquestion for the item. There should be a button on the panel now which looks like a camera.

---

