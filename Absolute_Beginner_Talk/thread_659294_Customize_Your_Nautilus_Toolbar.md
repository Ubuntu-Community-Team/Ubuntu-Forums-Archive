---
title: "Customize Your Nautilus Toolbar"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by greenleaf on 2008-01-05
**Add 'Cut', 'Copy', 'Paste', and 'Delete', buttons to toolbar**.

Here is an easy way to customize your Nautilus toolbar to include 'cut', 'copy', 'paste', and 'delete', buttons.

Open the following file from the terminal

```
sudo gedit /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml
```

**Make a backup of the file first... just in case**

Edit the file as per the following

```
<ui>
<menubar name="MenuBar">
	<menu action="File">
		<placeholder name="New Items Placeholder">
			<menuitem name="New Window" action="New Window"/>
		</placeholder>
		
		<placeholder name="Close Items Placeholder">
			<menuitem name="Close All Windows" action="Close All Windows"/>
		</placeholder>
	</menu>
	<menu action="View">
		<placeholder name="Show Hide Placeholder">
			<menuitem name="Show Hide Toolbar" action="Show Hide Toolbar"/>
			<menuitem name="Show Hide Sidebar" action="Show Hide Sidebar"/>
			<menuitem name="Show Hide Location Bar" action="Show Hide Location Bar"/>
			<menuitem name="Show Hide Statusbar" action="Show Hide Statusbar"/>
		</placeholder>
	</menu>
        <placeholder name="Other Menus">
	        <menu action="Go">
                        <placeholder name="Navigation Items">
			<menuitem name="Up" action="Up"/>
			<menuitem name="Back" action="Back"/>
			<menuitem name="Forward"  action="Forward"/>
	                </placeholder>
	                <separator/>
			<menuitem name="Home" action="Home"/>
			<menuitem name="Computer" action="Go to Computer"/>
			<menuitem name="Go to Templates" action="Go to Templates"/>
			<menuitem name="Go to Trash" action="Go to Trash"/>
			<menuitem name="Go to Burn CD" action="Go to Burn CD"/>
		        <menuitem name="Go to Network" action="Go to Network"/>
			<menuitem name="Go to Location" action="Go to Location"/>
			<menuitem name="Search" action="Search"/>
			<separator/>
			<menuitem name="Clear History" action="Clear History"/>
			<separator/>
			<placeholder name="History Placeholder"/>
		</menu>
		<menu action="Bookmarks">
			<menuitem name="Add Bookmark" action="Add Bookmark"/>
			<menuitem name="Edit Bookmark" action="Edit Bookmarks"/>
			<separator/>
			<placeholder name="Bookmarks Placeholder"/>
		</menu>
        </placeholder>
</menubar>
<toolbar name="Toolbar">
	<toolitem name="Back" action="Back"/>
	<toolitem name="Forward" action="Forward"/>

	<toolitem name="Up" action="Up"/>
	<toolitem name="Stop" action="Stop"/>
	<toolitem name="Reload" action="Reload"/>
	<separator/>
	<toolitem name="Home" action="Home"/>
	<toolitem name="Computer" action="Go to Computer"/>
	<separator/>
	<toolitem name="Cut" action="Cut"/>
	<toolitem name="Copy" action="Copy"/>
	<toolitem name="Paste" action="Paste"/>
        <toolitem name="Trash" action="Trash"/>
        <separator/>
        <toolitem name="Search" action="Search"/>
                <placeholder name="Extra Buttons Placeholder">
	          <placeholder name="Extension Actions"/>
        </placeholder>
</toolbar>
</ui>

```

Save the file and restart the Gnome (i.e. ctrl+alt+backspace)

---

### Post by P4oL1n0 on 2008-01-07
Nice trick :lolflag:

---

### Post by quoderat on 2008-01-20
If you want a Create Folder button on your Nautilus toolbar, which I do, just add this line wherever you want under the Toolbar part:

```
<toolitem name="New Folder" action="New Folder"/>
```

Do you have any documentation, or know where to find it, on what else is possible with this? I just guessed on that one.

---

### Post by greenleaf on 2008-01-26
Thanks.. you liked it.

No, I do not have any documentation..... i was just playing around with the file until i first screwed up my nautilus and finally got it right.... I'm a medical student... I absolutely have no idea why i added those lines. But these actions and also the 'create new folder' option are pretty commonly used options. Its good to have shortcuts on toolbar. But i wish there was a GUI for customizing the toolbar...

---

### Post by davbren on 2008-02-28
is there any way of removing some buttons from the toolbar?

---

### Post by greenleaf on 2008-02-28
Make a back up of the above file and play around with it  :lolflag:

---

### Post by FuturePilot on 2008-02-28
Awesome! Thanks! I've always wondered if there was a way to add buttons in Nautilus.

---

### Post by davbren on 2008-02-28
Yh this is great, I'm trying to get the "finder" look from mac, I'm almost there. One more thing. The arrows on the buttons... can I get rid of those??

---

### Post by davbren on 2008-02-28
[IMG]http://www.learnubuntu.org/images/screenshots/Screenshot.png[/IMG]

---

### Post by davbren on 2008-02-29
I'm not sure what to call this, but here goes, is there a way that we can add multiple "windows" within one window. :S i.e. having sorta newspaper columns that interact with each other. I know I couple of other file managers have this option. is it possible with nautilus via hack or otherwise.

---

### Post by stig on 2008-02-29
> **davbren said:**
> I'm not sure what to call this, but here goes, is there a way that we can add multiple "windows" within one window. :S i.e. having sorta newspaper columns that interact with each other....

I assume by "interact" you mean that when one column of file names reaches the bottom of the window it "wraps" over to begin a second column and then a third column etc. This is one feature that I really miss from my Windows days. Why do Linux applications always seem to lack this very useful feature? I like Nautilus in a number of ways but this is one of two missing features that make Nautilus "unfinished" for me.

The other missing feature is being able to open dual windows, side-by-side. I have the XFE file manager installed for this purpose and like it. The only reason I don't use XFE all the time is that it seems stuck in a grey-blue mode and I can't get the Gnome colours. There is an option in the XFE Preferences for choosing Gnome but the only thing it seem to do on mine is change the title bar to brown!

But if Nautilus could do the column wrap and dual columns I would love it!

---

### Post by uberMongo on 2008-03-21
This is very cool stuff.

I'm trying to get rid of the menu bar. What I want is to replace the menubar items with toolbar buttons. You can see I managed to remove some of the menus and add a few buttons, but it seams that I can't remove "File | Edit | View | Help" no matter what I do.

Do you have a solution for this?

thanks

[IMG]http://rs175tl2.rapidshare.com/files/101343040/screenshot1.png[/IMG]

---

### Post by osliner on 2008-04-09
UBERMONGO:
how could you get rid of the text below the navigation buttons?
and anybody knows where to find the configuration of the location bar?

---

### Post by davbren on 2008-04-29
I too would like to know where the location bar ui stuff is kept. All I want to do is move the location bar, its taking up space there...

---

