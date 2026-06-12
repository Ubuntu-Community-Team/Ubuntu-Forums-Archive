---
title: "Wine installed but not in menu"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-11-18
While I understand Wine has some issues with behaving inside the Applications dropdown menu, I'm having a quirky problem not answered anywhere. It should be simple.
Wine is installed. I had icons in the Applications menu. But then I followed these directions to install IE in Linux from here: 

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

which, I didn't realize until too late, was made for Edgy. In the process, I messed up something and now Wine does not appear in the Apps menu BUT does appear when you right click Apps>Edit Menus. What bewilders me is that when I highlight Wine in the Edit Menus window, the "show" check box is empty. Naturally I try to click it to activate it but NOTHING happens. I try to edit the Wine Menu options but still nothing happens.
I've installed and uninstalled the Wine listed in synaptic but the menu problem persists. What did I do? How do I fix it?

Thanks!

---

### Post by mc4man on 2007-11-18
One simple thing you could try is to delete the wine entry in edit menus and then choose revert  - it may allow you to check the box. If that doesn't work post back and I'll try something on my test box

---

### Post by Protagonistics on 2007-11-18
Yes, I've now tried that and it did nothing, though the box occasionally can be checked and occasionally cannot, nothing happens, even when I revert and try to check it... etc. I played around with it for 2 minutes and no difference. Even when it was checked, no difference. any ideas?

thanks for your help.

---

### Post by mc4man on 2007-11-18
I found something else you may try, it worked fine on my test box but be aware that I didn't have the intial problem of yours. No matter how completely you uninstall wine the 'menu entries" stay behind - that's why when you reinstall they're still there or when you click revert they come back.
what i'm thinking is if you can get a new entry written during the install it may work right.
First I'd do a complete removal from synaptic, you may also want to delete your .wine directory (i would, but you'll lose your progs.). Also delete wine from your apps. menu. What your aiming for is when you click revert wine does _not_ come back. If you go to places...file system (view hidden files)/home/<user name>/.config/menus you should find a file - applications.menu . Inside should   be similar to this
```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>wine-wine</Name>
		<Deleted/>
	</Menu>
</Menu>
```
if so delete the file. (if there's more than the wine entry I'd try just removing the wine ref.) There may be other wine related .menus in the applications-merged folder but I don't think they matter. (can be deleted) If going back to edit menus and clicking revert doesn't bring back wine you should get a new menu item after reinstalling wine and running winecfg
Note: there is some other leftover stuff from uninstalling in the .local/share folder but again I don't think they matter (again can be deleted )
I hope I made sense and there may be a better approach

---

### Post by wolfvorkian1 on 2007-11-19
<snip> 
empty. Naturally I try to click it to activate it but NOTHING happens. I try to edit the Wine Menu options but still nothing happens.
I've installed and uninstalled the Wine listed in synaptic but the menu problem persists. What did I do? How do I fix it?

Thanks![/quote]

Do you have the program called locate installed? If not you might try installing it and I forget if it automatically creates a search database  or if you have to tell it to. Anynow, the command that will do it is...

```
sudo updatedb
```

Then try this:

```
locate wine
```

Any file that has a mention of wine will probably be discovered and you can then delete them individually. Hopefully this will solve your problem but no guarantees. ;-) Synaptic doesn't get rid of everything I've found out.

---

### Post by Hozza on 2008-05-24
I am using Ubuntu Hardy and i am having the same problem after trying to install quick time with wine.

i still havent sorted it out yet but when i do i'll post another comment on how to do it.

thax for the help BTW :)

---

### Post by Hozza on 2008-05-26
Hi,

At fist I used the "locate wine" method from wolfvorkian1 and deleted all of the entry's, but that didn't work. So then I took the advice from mc4man, Put them together and then poof it worked.

So here it is in detail;

Go into add/remove programs which is in the applications menu, type wine into the search box, Wine Windows Emulator should appear, make sure that is unticked(uninstalled), if it is ticked then untick it and click Apply Changes.

Go to "/home/<user name>/.config/menus/" in that folder there should be a file called "applications.menu" open it up and if it looks like this;

```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>wine-wine</Name>
		<Deleted/>
	</Menu>
</Menu>
```

......then Delete the whole file "applications.menu" if there is more than this in the file then just remove the wine section.

Then go into "/home/<user name>/.config/menus/applications-merged/" if there are files in that folder with wine in their names, delete them. (in my case there were two)

Then delete the following files;

/usr/share/app-install/desktop/wine.desktop
/usr/share/app-install/desktop/wineconfig.desktop
/usr/share/app-install/desktop/winefish.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_winefish-icon.png
/usr/share/python-support/guidance-backends/wineread.py
/usr/share/python-support/guidance-backends/winewrite.py
/var/lib/python-support/python2.5/wineread.py
/var/lib/python-support/python2.5/wineread.pyc
/var/lib/python-support/python2.5/winewrite.py
/var/lib/python-support/python2.5/winewrite.pyc

The way to remove/delete files that are not in your home folder is through terminal, 

First open terminal and then type

"sudo rm /usr/share/app-install/desktop/wine.desktop"

Then you will be prompted to enter your root password, do so then click enter, your file should then be removed :)
Repeat this with all of the files (you will only be prompted for your password once)

Now restart your computer (type restart and click enter in terminal)

Then reinstall wine, through add/remove programs or terminal

---

### Post by Hozza on 2008-06-29
hi, this is an update to my old howto

use mc4man's method and if it still dont work go into synaptic package manager and do a complete removal (right click on the package and click full removal)

if it still wont work after that use the locate method

---

### Post by zenithdave on 2008-07-16
Thanks for that worked a treat, all gone  :)

---

