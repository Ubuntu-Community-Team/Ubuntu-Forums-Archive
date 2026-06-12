---
title: "[SOLVED] Gnome applications menu has dissappeared?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by drazgo on 2008-03-16
Hello,
I just got a problem, suddenly there is no content in the Applications menu.
When I click the menu or hover to open, just a square of ~2x2px appears - as if it where empty. It was there just before. I have multiple user accounts on my pc, but it only seems to be happened with one account...

Anyone got an idea? Where is the menu stored? (I guess it is a text file or something)
And another thing, the Menu Editor doesn't start after right clicking at the menu,:confused:

thanks in advance!

---

### Post by corney91 on 2008-03-16
What happens if you type the following command in to the terminal?:```
alacarte
```
It's the menu editor so if there's a problem opening it, the error would be shown here.

---

### Post by sandysandy on 2008-03-16
right click on upper panel.

select---> add to panel

window will open. in it select *menu bar* or *main menu*.

u will get new one.

the old one can be removed from panel thereafter.

regards

---

### Post by drazgo on 2008-03-16
@corney: this is the error i get in the terminal: 

> papa@thuis-desktop:~$ alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 926, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0


@sandysandy: the solution you gave didn't work, too bad :(

---

### Post by corney91 on 2008-03-16
Hmmmm, I'm not the best at understanding these errors but try reinstalling gnome-menus and alacarte, in case one of them is causing the problem:```
sudo apt-get install --reinstall gnome-menus alacarte
```
If not I'd guess it's a dependecy error, but first see if this works.

Actually looking at it again, it's more likely that you are missing a dependency, but try the above, while I look around for what you might be missing.

---

### Post by corney91 on 2008-03-16
If it doesn't work try:
```
sudo apt-get install python-libxml2
```
It looks like a python problem, so I'm looking at gnome-menus dependencies for something related to python.

---

### Post by eoshicute on 2008-03-16
press right click on your mouse, and click add to panel :)

---

### Post by corney91 on 2008-03-16
> **eoshicute said:**
> press right click on your mouse, and click add to panel :)
I think the menu's there, it's just empty ;)

---

### Post by drazgo on 2008-03-16
just tried reinstalling all packages mentioned up above, but nothing changed my problem :( you know, the strange thing is (if it would be a package problem), my other users on my pc CAN see the applications menu and the menu editor IS working...

---

### Post by drazgo on 2008-03-16
oooh wait, i just found the solution :D seems there was a problem with this file: 

/home/user/.config/menus/applications.menu

i just replaced the file with the one from an other account and the menu is back! xD

thanks anyway for helping so much!

---

### Post by corney91 on 2008-03-16
> **drazgo said:**
> just tried reinstalling all packages mentioned up above, but nothing changed my problem :( you know, the strange thing is (if it would be a package problem), my other users on my pc CAN see the applications menu and the menu editor IS working...
Woops, I didn't think of that:oops:
That makes things more confusing, I'm afraid I can't think of anything...
If no-one else has any ideas, as a last-ditch attempt, you could make a new user and copy over the /home folder...
Sorry I couldn't be of more use:(

---

