---
title: "How do I disable &quot;Recent Documents&quot;?"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2005-11-16
I would like to completely disable this feature.

Thanks,

-Doc

---

### Post by MartinG on 2005-11-16
Kubuntu - System Settings -> Panel -> Panels -> Menus. The optional menus listbox has a tickbox for this.

---

### Post by Doc.Caliban on 2005-11-16
Sorry, Gnome.  I should have stated that.

-Doc

---

### Post by audax321 on 2005-11-16
To disable it, first make sure you have something in your Recently Used list right now (so the file '/home/username/.recently-used' exists)

Then, open up /home/username/.recently-used in gedit:
[INDENT]gedit /home/username/.recently-used[/INDENT]
[INDENT]- Delete the contents, save, and exit. [/INDENT]

Then open up a terminal and:

[INDENT]chmod 400 /home/username/.recently-used[/INDENT]
[INDENT]- This will make the file read-only... thus Gnome can no longer write to it and the Recently Used menu will become disabled.[/INDENT]

To re-enable the menu in the future:
[INDENT]chmod 600 /home/username/.recently-used[/INDENT]

:)

---

### Post by audax321 on 2005-11-16
An easier way.... I made a Nautilus Script that you can use:

```

#!/bin/sh

# Enable/Disable Recent Documents Menu in Gnome

if [ ! -f "$HOME/.recently-used" ]; then
	echo "" > "$HOME/.recently-used"
	chmod 600 "$HOME/.recently-used"
fi

if [ -w "$HOME/.recently-used" ]; then
	echo "" > "$HOME/.recently-used"
	chmod 400 "$HOME/.recently-used"
	if [ "$?" = "0" ]; then
		zenity --title="Disabled" --info --text="The 'Recent Documents' menu item has been disabled."
	else
		zenity --title="Error" --error --text="There was an error disabling the 'Recent Documents' menu."
	fi
elif [ -f "$HOME/.recently-used" ]; then
	chmod 600 "$HOME/.recently-used"
	if [ "$?" = "0" ]; then
		zenity --title="Enabled" --info --text="The 'Recent Documents' menu item has been enabled."
	else
		zenity --title="Error" --error --text="There was an error enabling the 'Recent Documents' menu."
	fi
else
	zenity --title="Error" --error --text="It appears the file '$HOME/.recently-used' does not exist and could not be created."
fi

```

Just paste that code into a text file, chmod the file 755 and place in '/home/username/.gnome2/nautilus-scripts' and it will show up in your right click Scripts menu. It'll enable/disable the menu and bring up a nice message box telling you if it succeeded or not.

---

### Post by shof2k on 2005-11-17
A nice how to is here [http://ubuntuforums.org/showthread.php?t=91154](http://ubuntuforums.org/showthread.php?t=91154)

---

