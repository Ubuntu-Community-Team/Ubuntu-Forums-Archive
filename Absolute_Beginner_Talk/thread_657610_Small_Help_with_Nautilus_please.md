---
title: "Small Help with Nautilus please"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by greenleaf on 2008-01-03
Can any of you please post the content of

sudo gedit /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml

Please....

I meddled with it by editing it... and now my toolbar buttons are missing....

I wanted to restore the file to its original state.... please help

---

### Post by compwiz18 on 2008-01-03
Backups are your friend!

Hm, pretty cool though.  Didn't know you could edit the GUI...

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
	<toolitem name="Search" action="Search"/>
	<placeholder name="Extra Buttons Placeholder">
	          <placeholder name="Extension Actions"/>
        </placeholder>
</toolbar>
</ui>
```

---

### Post by Dr Small on 2008-01-03
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
	<toolitem name="Search" action="Search"/>
	<placeholder name="Extra Buttons Placeholder">
	          <placeholder name="Extension Actions"/>
        </placeholder>
</toolbar>
</ui>
```

---

### Post by AndyCooll on 2008-01-03
You can always go to ~/.gconf/apps and delete the nautilus directory from there. Ubuntu will then build a new one.

:cool:

---

### Post by greenleaf on 2008-01-03
Thanks for the quick help.....

Will make backups in the future before taking risks.... THANKS A LOT !!!!

---

