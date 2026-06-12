---
title: "[SOLVED] Gedit: can it open text files in separate windows?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by gobuntu on 2008-03-10
Dear friends, I would like to have Gedit open a text file that I click in a separate window, rather than in tabs, as it now does.

Reasons are:

1. It's more convenient for cut and paste.

2. I am often moved from the current workspace to another when there I click on a text file. That is the case when I have, in onother workspace, another text file open under Gedit.

Due to that switching of workspaces, at times it was hard to find out where the pending text file went to, but of course, it had gone into a tab.

In other words, It's not natural to open a text file in the current workspace and be instantly transfered to another workspace because Gedit wants to   work where it is, not in the workspace I am and want to be.

If it's not possible now, perhaps this option should be added.

Of course, Tabs are nice if one is working in only one workspace, and more so on a small screen.

Thanks!

---

### Post by neurostu on 2008-03-10
If you right click on a tab there is a "move to another window" option

try that ;-)

---

### Post by munkyeetr on 2008-03-10
Same as above, plus one more option explained [here]("http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg116371.html")

---

### Post by gobuntu on 2008-03-11
Thanks for the replies, friends, which imply that the functionality I am after is not there yet.

The options mentioned still flip me back from    the current workspace (where I want to be) to the workspace that Gedit happens to be with another file open, which is a common case in what I am doing (Documenting  various folders and files with short text files).

I think that I will probably try another editor as default that does open an instance of itself where I happen to be, while a pending open text file stays open as needed, for quick interacting with it).

---

### Post by rahearn on 2008-03-11
Try this:

Right click on your menu bar and select "Edit Menus" and follow these steps:
1) Click "Accessories" from the Menus selector on the left
2) Right-click "Text Editor" from the "Items:" pane and click "Properties"
3) Change the entry in Command from gedit %U to gedit --new-window %U

Now double clicking text files in nautilus should open documents in a new window on your current workspace.  Opening files from the terminal will still require calling gedit with the --new-window flag to avoid opening in a tab.

---

### Post by handydan918 on 2008-03-11
Or you could dump Gnome and use KDE. Kate and kwrite both do this with no issue...

---

### Post by gobuntu on 2008-03-11
> **rahearn said:**
> Try this:

Right click on your menu bar and select "Edit Menus" and follow these steps:
1) Click "Accessories" from the Menus selector on the left
2) Right-click "Text Editor" from the "Items:" pane and click "Properties"
3) Change the entry in Command from gedit %U to gedit --new-window %U

Now double clicking text files in nautilus should open documents in a new window on your current workspace.  Opening files from the terminal will still require calling gedit with the --new-window flag to avoid opening in a tab.

Hi rahearn,

THANKS A LOT!

This works just perfect, with the added bonus that Gedit WARNS very nicely when one wants to edit a document that is ALREADY OPEN.
..............

This instruction needed, though, a little clarification, as follows:
Right click on your menu bar [COLOR="SandyBrown"][OVER Applications][/COLOR] etc.
because at other places of the menu bar I got a different dropdown menu.
.................

I had already set up the SCite text editor to do exactly what I wanted (quite a bit of work), but I went ahead and reverted that so I do exactly as you said and now the default is again Gedit.

One good reason for keeping Gedit is that it's kind of part of Gnome, plus a lot of the "How To's" in the web, which involve setups, etc, do refer to using Gedit, and so one can just copy and paste (most of the times), without having to replace "Gedit" for another editor.

.......
I kept the SCite editor, though, for other uses. That one has a nice feature that it actually responds to the mouse wheel increasing/decreasing text size very nicely, plus I had set it to mono text, which is also nicel, for other things I do.

Thanks to everyone who had replies, none of which was ignored.

:)

---

