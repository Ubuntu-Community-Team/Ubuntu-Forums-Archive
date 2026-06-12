---
title: "Applications menu not working."
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by doyler78 on 2007-06-02
Originally posted in Desktops however got no replies and really having no menu access to my apps is a disaster for a beginner and does nothing to make linux an appealing alternative to windows so hoping somebody here can help.

I was going to edit my applications menu to show some of my missing apps however I didn't even get that far.

I right clicked on application and choose edit menus. In the panel it shows "starting main menu" then it just disappears and nothing comes up. Now when I press the applications button nothing pops up. My places and system are fully functional. I have rebooted however this didn't make the slightest bit of difference.

I went to system -> preferences -> main menu and it does exactly the same things as right clicking on apps as described above.

I then tried alt-F2 and typed alacarte and this just does nothing.

Any ideas how I can get my apps menu working again and then how I can edit without killing it again.

Thanks

---

### Post by bobbocanfly on 2007-06-02
The only thing i can think of is to remove the menus (Left Click -> Remove from Menu) then add it in again (Left click any free space on the toolbar -> Add to Panel -> Menu Bar). Might do the trick but i have never had any problem with this sort of thing....

---

### Post by lambros on 2007-06-02
Looks like something went wrong with the Menu Editor, and may have left your menus in a broken state.  You could perhaps try removing (or renaming) your .config/menus folder (in your home directory).  Then log out and back in again - that should restore your menus back to the system defaults.

If you want to do this from the command-line, the command is
```
rm -rf ~/.config/menus
```
to delete your menus folder, or
```
mv ~/.config/menus ~/.config/menus-backup
```
to rename the folder out of the way (so you could restore it if needs be).

If you want to do this from the GUI, you would need to browse your home folder, then hit Ctrl-H to show the hidden files (because the .config folder would normally be hidden from the list).  Then browse into the .config folder, and delete (or move) the "menus" folder.

Don't know if this will help, but at least it's worth a try.  Please let us know if it works or if you have any questions.

Edit: Sorry, forgot to ask - it might be useful for us to see any error-messages from alacarte.  If you still have problems, please could you open a Terminal window (one way is to press Alt-F2 and enter "gnome-terminal" - without the quotes).  Then try to run the alacarte command from the Terminal window and post here any error-messages it spits out.

Lambros

---

### Post by doyler78 on 2007-06-02
Thanks for the help. That's a huge relief. I thought I was going to have remove gnome desktop and reinstall. Renaming the config file worked a treat. I have gone into the menu editor and it didn't cause any probs this time so all is well again.

Thanks a lot

---

### Post by lambros on 2007-06-02
You're welcome!  I'm glad you got it working again without a full re-install, that would have been a waste :-)  I find that most of these kinds of problems are fixable simply by deleting files and letting them get recreated again.

Lambros

---

### Post by nbussiere on 2007-07-09
You helped me too ! Thanks a lot !! :)

---

### Post by tenchu77491 on 2008-02-11
I finally fixed this problem as well!

rm -rf ~/.config/menus 

WORKED FOR ME! Then, delete old menu and add a new main menu and it worked. Thanks a lot. 

I searched google for an hour looking for "ubuntu main menu won't work, applications will not run" and came up with squat. I hope more people get directed here by their search hits....

---

