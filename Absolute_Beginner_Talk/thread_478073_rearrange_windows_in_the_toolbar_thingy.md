---
title: "rearrange windows in the toolbar thingy"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2007-06-18
is there anyway to change it so you can drag and drop the windows on the bottome when they are minimized to rearrange them?

---

### Post by arvevans on 2007-06-18
Not sure what you are requesting.  If you mean "can you drag applications from one workspace to another", that works just fine on my Ibuntu system.  Hold down the mouse button on the application in the current workspace and drag it to the desired workspace.  Then when you click on that workspace you will find that your application has moved there.  If you are running KDE or XUbuntu then things might be different.

If you cannot drag applications from one workspace to another, try right-clicking on the minimized application and see if an option menu comes up that allows you to move the application to the workspace that is left or right of the one you are using.  That also works in standard Ubuntu.
_._

---

### Post by Fittersman on 2007-06-18
sorry, i mean that if i had on the bottom all my windows unorganized and stuff (like if i had 5 kmess chats open, but i want them to be all beside each other) is there anyway i can drag them to make the order better? (on the same workspace)

cuz, i like to have kmess first, then firefox and if its out of order im always clicking the wrong window

(i know it shouldnt really matter, but i like customization  to the max! :D)

---

### Post by Fittersman on 2007-06-20
bumpp

---

### Post by Sweet Mercury on 2007-06-20
You're referring to the "Windows-like" taskbar that's on the bottom by default?

Not sure exactly how you might do that. The lack of that functionality in Windows used to bug me as well.

While this isn't exactly the solution you want, it might be a way of organizing that is similar in function. You can try grouping windows not together on the taskbar, but in seperate workspaces. Have Firefox on one workspace, Kess windows on another, Gaim on another, etc.

It keeps the desktop from being too "cluttered." You can fast switch between workspaces using Alt+Ctrl+Left/Right/Up/Down.

I've found that, for me, this type of organization is much easier to manage. Give it a shot!

---

### Post by Fittersman on 2007-06-20
thats a good idea, and i was reffering to the windows like thingy thats on the bottom

edit: o, actually that wont work, kmess seems to make a minimized window on the bottom telling me that someone is talking to me anyway, so its just as cluttered now anyway :(

---

### Post by quirks on 2007-06-20
This is an interesting question, which I asked myself, too, some time ago. But I couldn' t find any functionality for reordering the windows in the panel (and I don't think there is any - sorry). What I did instead is, I use multiple workspaces. On one workspace, I am running Firefox, on another one there is Thunderbird and on yet another one a terminal. I use to run all these applications on dedicated workspaces, so that whenever I switch to (let's say) workspace 2, it is certainly Firefox that pops up. This is pretty cool in combination with keyboard shortcuts, because then I can use a simple shortcut to bring up Firefox or Thunderbird or a Terminal etc. .

I know, this is not the answer you wanted, but I hope it can help.

quirks

---

### Post by quirks on 2007-06-20
Ok, this is funny: while I was writing my post, Sweet Mercury posted exactly the same answer. Seems like this is a common solution to your problem. ;-) 

quirks

---

### Post by iqag1060 on 2007-06-20
I'm sorry i don't have a GNOME system open right now to look at this, but isn't there an option to set the threshold at which windows are grouped? In KDE you can right click on the panel (find a little blank spot), choose "Configure Panel", then the "Taskbar" submenu and change the option on "Group similar apps when:" I'm pretty sure there's something similar in GNOME. Of course, this doesn't let you drag and drop them at will, but it does keep them grouped.

---

### Post by MeeMaw on 2007-06-20
Or you can make your panel more narrow, and open them in that order....(at work I have to use XP and I open the browser first, then the work app I have to use, then the company e-mail and they are in the panel in that order)...............at home I use the Workspace method so Firefox is always on workspace 1, OpenOffice on 2, IM on 3...... like the others described.

Some people might call us obsessive!!!!  However, I'm sure you will find a method that works for you.     ;)

---

### Post by Soybean on 2007-06-20
Window grouping isn't exactly what you're looking for, but you could check it out... there should be a small vertical bar on the taskbar just to the left of the window list that you're trying to sort. Right click it and pick "Preferences," then "Always group windows." It makes it so that all windows of the same application appear in a single button down there. It is more organized, although personally I can't stand it.

That's the closest thing that I *know* will work. I'm not sure if there's a way to do exactly what you're asking, but if there is, it could be in the gconf-editor.

Probably one of the following two places:
/apps/panel/default_setup/applets/window_list

or

/schemas/apps/window_list_applet/prefs

You may have to do some searching to find out what the various options in there do, though.

Also, consider that the taskbar you're looking at is just an applet ("Window List") running inside a Gnome panel. If you can't make it do what you want, you may be able to find a different applet or a different panel that does meet your needs. :) Not that I've actually heard of a program that does that -- it just seem like something that *somebody* should have already made. ;)

---

### Post by Sweet Mercury on 2007-06-20
> **Fittersman said:**
> thats a good idea, and i was reffering to the windows like thingy thats on the bottom

edit: o, actually that wont work, kmess seems to make a minimized window on the bottom telling me that someone is talking to me anyway, so its just as cluttered now anyway :(

Are you familiar with how to customize the GNOME panels and what shows up on them?

I ended up ditching the "Taskbar" entirely, partly because I outgrew it in a sense (it's still necessary in a Windows set-up, though) and partly because of that annoyance.

Are you referring to new IM windows popping up on whichever workspace you happen to be working on? If so, you can move them easily. You can right click on the window's title bar and select "Move to workspace ..." Or, the easier way, Shift+Ctrl+Alt+Left/Right/Up/Down will move whichever window is in focus to the "next" window—as well as move your view to the next window with it.

If you're talking about the taskbar button showing up on the panel to alert you of a new IM in a window that's open in another screen, then I'm not so sure. GAIM or Pidgin might have a setting that disables that.

Here's a screenshot of my "work in progress" desktop. The two toolbars in the lower left and right are on auto-hide, but you can see their functionality. The lower right shows what windows are open on what workspaces.

You can obviously put anything wherever it's convenient for you. This is just a suggestion.

---

### Post by sailor2001 on 2007-06-20
are you sure you're not talking about right click/move?

---

