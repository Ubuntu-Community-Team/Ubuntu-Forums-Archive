---
title: "Applications Menu Doesn't Work."
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by nbeerbower on 2007-09-03
I can't get my applications menu to open it just gets highlighted but it doesn't open and display the programs. :( 

Is there some sort of fix for this?

-nBeerbower

---

### Post by aitorcalero on 2007-09-03
Thy this. Restart gnome-panel, in terminal write
```

sudo killall -HUP gnome-panel

```

PS.: -HUP stands for HUP (Hang UP)

---

### Post by nbeerbower on 2007-09-03
That didn't work. It restarted everything but the app menu still won't come work. :(

I get a little box (Like 5 pixels big) that can be highlighted but that's it. I tried editing the menus but the it won't load up... :(

---

### Post by nbeerbower on 2007-09-03
Should I just reinstall Ubuntu? :(

---

### Post by Deaf_Dog on 2007-09-03
I had that happen to me once. Try removing it from the panel and then adding it back again. That worked for me.

---

### Post by nbeerbower on 2007-09-03
That didn't work. :(

---

### Post by philinux on 2007-09-03
What happens when you right click and select edit menu's?

---

### Post by nbeerbower on 2007-09-04
Ubuntu hangs. It says Starting Main Menu or whatever and then... it stops. :(

---

### Post by NewJack on 2007-09-05
I am having the same problem, but with all of the menu items.  In addition, I can't use the drop down menus in Firefox nor can I use right click (It does nothing).  I tried aitorcalero's suggestion, but no luck.

---

### Post by philinux on 2007-09-05
The menu editor is a package called alacarte.

Two things to try. open a terminal and just type alacarte.

if that dont work go to synaptic find alacarte and mark it for reinstallation.

---

### Post by NewJack on 2007-09-05
Well I got everything to work again after 2 restarts.  Don't know why it took 2 restarts, but hey it works.

---

### Post by nbeerbower on 2007-09-05
Here are the results of Alacarte:

```
nicholas@nicholas-desktop:~$ alacarte
GTK Accessibility Module initialized
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

```

How do I access synaptic? EDIT: Never Mind I found it but I can't apply it because I don't have admin rights.

EDIT: Never Mind again I just used the sudo command. And..... Menu still doesn't work...

---

### Post by rhutton on 2007-09-07
Hi,

My first post on the forum (take warning!)

I think I understand your problem.

I found this post whilst trying to resolve exactly the same problem on Ubuntu Gutsy with Ubuntu-Studio,  After upgrading from Feisty to Gutsy my Miro podcast program stopped working, so I downloaded and installed gpodder, and after this my Applications menu disappeared, Places and System were OK.  After some searching I found that ma applications.menu file was missing.  At the command prompt type

cd $XDG_CONFIG_DIRS
cd menus
ls

I had preferences.menu  and settings.menu but not applications.menu.

I found a 'blank' applications.menu file as follows:

<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">
<Menu>
  <Name>Applications</Name>
  <Directory>Applications.directory</Directory>

  <!-- Read standard .directory and .desktop file locations -->
  <DefaultAppDirs/>
  <DefaultDirectoryDirs/>

  <!-- Accessories submenu -->
  <Menu>
    <Name>Accessories</Name>
    <Directory>Accessories.directory</Directory>
    <Include>
      <And>
        <Category>Utility</Category>
        <Not>
          <Category>System</Category>
        </Not>
      </And>
    </Include>
  </Menu> <!-- End Accessories -->

  <!-- possibly more submenus -->

</Menu> <!-- End Applications -->

I ran sudo gedit, pasted this file in, and then saved is as applications.menu in the appropriate place.  This got the applications menu bar working again, but obviously without all the correct applications listed.  They could be added again manually but that's not ideal.  I did get all the icons I had installed only under my own user profile such as Quake 4, UT2004 etc, but not the all user menu, as that's the one that went missing.

Can anyone reply with a cut and paste of /usr/share/ubuntustudio-menu/menus/applications.menu from Ubuntu Studio Gutsy Gibbon?

You could try the same for whatever version of Ubuntu you are using.

Robert

(Ubuntu Rookie)

---

### Post by rhutton on 2007-09-07
Quick update:

$XDG_CONFIG_DIRS on my machine resolved to 

/usr/share/ubuntustudio-menu/menus

but the menu files in there were actually just link files to 

/etc/xdg/menus

The correct applications.menu was in the /etc/xdg/menus, I just deleted my blank applications.menu and created a link file called applications.menu pointing to /etc/xdg/menus/applications.menu.

Now the menu works fully again!

I can only thing the gpodder install script didn't work well with the Ubuntu Studio version of Gutsy.

Robert

---

### Post by Brandel Valico on 2007-10-01
Just had this happen to me. My Applications menu stopped working. To fix it I Copied the information from the Applications menu found at /etc/xdg/applications.menu

To the one found in the Home Folder/.config/Menus/applications.menu

It completely restored my application menu to working order and so it shows all my installed applications as well.

Hope this helps those still having issues with this

---

### Post by xtemplarx on 2007-10-02
> **NewJack said:**
> I am having the same problem, but with all of the menu items.  In addition, I can't use the drop down menus in Firefox nor can I use right click (It does nothing).  I tried aitorcalero's suggestion, but no luck.

Newjack:

I was having the EXACT symptoms you are referring to.  It's a relatively new thing and seems to be a result of the latest compiz updates (at least in my case).  

What I did to solve it:

Opened a terminal.  I did a ```
ps aux | grep compiz
``` to see if compiz was acting normally, and saw that there were 4 instances of it running somehow!  Strange, but oh well.  I killed them all, then restarted Compiz and I've been back to normal ever since.

xTx

---

### Post by nbeerbower on 2007-10-14
Geez, I have no idea what's wrong. I have two applications.menu files but they look identical. (I did a search because I couldn't find the one in Home folder) I believe it started acting up after I started using the Desktop Effects, or maybe it was when I changed my theme. (No, changing it back doesn't resolve anything.) 

Any more ideas guys?

---

### Post by cometyz on 2007-10-22
Home Folder/.config/Menus/applications.menu

you delete this applications.menu ,and ubuntu will uses /etc/xdg/menus/applications.menu for default.

---

