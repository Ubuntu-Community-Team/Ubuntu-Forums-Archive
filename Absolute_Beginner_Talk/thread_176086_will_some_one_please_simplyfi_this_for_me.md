---
title: "will some one please simplyfi this for me"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Napster69 on 2006-05-14
will some one simplyfi this for me 







Quote:
Originally Posted by dare2dreamer
Should be a trivial matter to work this up as a nautilus script, so it appears as an option in your right-click menu.

Call me silly, but an icon on my desktop that opens things as root just makes me nervous.
As and you shall receive. Put the following into ~/.gnome2/nautilus-scripts/Open\ as\ root
Code:

#!/bin/sh gksudo "gnome-open $NAUTILUS_SCRIPT_SELECTED_URIS"

Then make it executable with
Code:

chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root








im running breezy badger

---

### Post by adam.tropics on 2006-05-14
Open nautilus (file browser) and hit <Control>h, this will show hidden files,

~/.gnome2/nautilus-scripts/

you will see .gnome2 (the hidden folder, indicated by . )

It is being suggested you create a file, and then insert the given script into that file. To do that enter in terminal,

sudo gedit ~/.gnome2/nautilus-scripts/Open\ as\ root

It will ask for your password, enter it, and a text editor will open. Cut and paste the text from the above suggesrion and save the file. You already named it when you created it.

Next, in terminal again, enter 

chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root

That alters the permissions of the file and makes it executable.n Now when you right click tou will see an option 'scripts'-->Open as Root

Be careful with it!

---

### Post by AndyCooll on 2006-05-14
Ok, copy and paste the following into a terminal (i.e. a command line):

```
sudo gedit ~/.gnome2/nautilus-scripts/open_as_root

```

That will open a new blank text document. Then copy and paste into that document the following:


```
#!/bin/sh gksudo "gnome-open $NAUTILUS_SCRIPT_SELECTED_URIS"

```

Press return at the end. Save and close the document. Then make it executable by copying and pasting into the command line again:


```
chmod +x ~/.gnome2/nautilus-scripts/open_as_root
```

Now, when you right click any part of the desktop (or in Nautilus) you will see an entry that says "Scripts-->open_as_root"

:cool:

---

### Post by Napster69 on 2006-05-14
thanx

---

