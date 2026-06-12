---
title: "menu editor question"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by ncappel1 on 2006-04-08
The only way that I can open "Applications menu editor" is through a terminal by typing ```
smeg
```

When I try to click on Applications-->System tools-->Application menu editor, I see a box show up in the bottom panel that says, "Starting Applications Menu Editor" but after 5 or 10 seconds, it just goes away, never loading it. 

I used to have this same problem trying to load firefox in Hoary, but after upgrading to Breezy it never happened again. any thoughts on cause of this problem?

---

### Post by amohanty on 2006-04-08
Does it work if you right click on the Applications and then select Edit Menus?
Does it work if you put smeg in a panel and then click on it?

AM

---

### Post by ncappel1 on 2006-04-08
amohanty, neither works. 

Correction: I actually have to type ```
sudo smeg
``` to get it to work in the terminal.

---

### Post by ncappel1 on 2006-04-08
Hate to reply to my own post, but I think I got it. in the applications menu editor launcher under Applications it was not being launched as sudo, the command was just "smeg" I added sudo right before it, and now it works fine. I don't remember changing that ever. Do these things just happen?

Next time I will think a little more before posting to the forums!
D'oh! #-o

---

### Post by pbaehr on 2006-04-08
Well, the weird thing is you shouldn't have to be a super user to run smeg.

Also, as I understand it you should use gksudo instead if you're running a graphical application. I don't know exactly why, but that's what I've been told.

---

### Post by ncappel1 on 2006-04-08
hmmm....this reminds me of some omnious omen from a bad scary story. so in conclusion, I don't really have a problem....but at the same time, I do?

very strange. Anymore ideas?
:-k

edit: something must be on the fritz, because even after having changed the line in the menu editor and adding sudo, I still have the same problem. running "smeg" into the command line gives this back: > nicola@ithaca:~$ smeg
Traceback (most recent call last):
  File "/usr/bin/smeg", line 562, in ?
    main()
  File "/usr/bin/smeg", line 558, in main
    smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
    self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 56, in __init__
    xdg.MenuEditor.MenuEditor.__init__(self, menu_path, root=options.root_mode)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init__
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 42, in parse
    self.menu = parse()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 853, in __genmenuNotOnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1016, in addMenuEntries
    self.__addFiles(dir, "", prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1022, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 382, in __init__
    self.DesktopEntry = DesktopEntry(os.path.join(dir,filename))
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 25, in __init__
    self.parse(filename)
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 36, in parse    IniFile.parse(self, file, ["Desktop Entry", "KDE Desktop Entry"])
  File "/usr/lib/python2.4/site-packages/xdg/IniFile.py", line 30, in parse
    for line in file(filename,'r'):
IOError: [Errno 13] Permission denied: '/usr/share/applications/opera.desktop'

using "sudo smeg" and "gksudo smeg" in the command line both let it work.:confused:

---

### Post by amohanty on 2006-04-10
Post the output of **ls -alR | grep -v $USERNAME** in your home folder, I bet the .gconf folder which has the apps folder had some bad thing done to its permissions :)

AM

PS: and why are you hitting:
> IOError: [Errno 13] Permission denied: '/usr/share/applications/opera.desktop' 

Post the output of the above and I bet, you will find some root's in there :) 
Disclaimer: I have been known to be wrong about things from time to time

---

### Post by Perfect Storm on 2006-04-10
> IOError: [Errno 13] Permission denied: '/usr/share/applications/opera.desktop

This is the problem. Just remove it:
```
sudo rm -f /usr/share/applications/opera.desktop
```

It's the opera launcher in the application tab. Just make a new one with smeg.
You can now run smeg normally.

---

### Post by nanotube on 2006-04-10
[QUOTE=Artificial Intelligence]This is the problem. Just remove it:
```
sudo rm -f /usr/share/applications/opera.desktop
```

It's the opera launcher in the application tab. Just make a new one with smeg.
You can now run smeg normally.[/QUOTE]

since it is having trouble reading the file, i think all you have to do is chmod it to be readable, with 
```
sudo chmod 755 /usr/share/applications/opera.desktop
```
and then your problem should go away. if that doesnt work, then you can try AI's way and delete it. :)

---

### Post by ncappel1 on 2006-04-10
I removed the file before I thought to try and change the permissions, then Irealized that I never use Opera anyway, I use firefox mainly and keep epiphany for it's lightweightness (of course, nothing is as lightweight as w3m) in case firefox goes bonkers (never happened yet). 

I removed the line, then removed "sudo" from the menu editor command, and everything works great now! I even removed all of opera, but that was after everything worked. 

thank you everyone!
viva ubuntu!

---

