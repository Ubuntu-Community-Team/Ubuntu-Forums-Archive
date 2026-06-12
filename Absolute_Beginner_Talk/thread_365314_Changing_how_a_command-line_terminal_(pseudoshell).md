---
title: "Changing how a command-line terminal (pseudoshell) opens."
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by OldDogNewTricks on 2007-02-19
When I open a pseudoterminal in Edgy Eft, it is smaller than I like.  I want to set the COLUMNS variable to 89, so the pseudoterminal uses more of the screen width.  If I do:

        set COLUMNS=89

it lasts for the duration of that pseudoterminal only.
 

If I do

        export COLUMNS=89

it works for child terminals.


But I can't figure out how to make it stick!  I tried putting 

        export COLUMNS=89

in my .bashrc file, thinking a user variable might override the system's.  It didn't.


I'm convinced there is a configuration file somewhere that I can change this in, but I have no clue which.

All application windows that open in the GUI have default sizes, most of which are tiny and annoying to work in, in my opinion.  I'd like to find out how to permanently resize all these windows.  I've tried the Gnome configuration editor, but it seems to never list window- size options.
 

Any enlightenment would be appreciated.  I'm sure it is simple; I just haven't been steered in the right direction.  And I bet loads of other newbies would like to be able to set the window size for each application that opens.

---

### Post by nereid on 2007-02-19
Do you use the gnome terminal emulator? There should be an option about the size of the terminal available.

---

### Post by OldDogNewTricks on 2007-02-19
Yes, the pseudoterminal is gnome-terminal.  I have looked at the GConf editor, and cannot find the appropriate config file to edit.  It has to be there somewhere, but it is like searching for a needle in a haystack if one does not know the name of the file.

Still need help.

---

### Post by nereid on 2007-02-20
I think that this option is in the gnome-terminal itself (can't say for sure, because I use Konsole).

---

### Post by OldDogNewTricks on 2007-02-20
Thanks for your help.  I found the way to do it.  It was not in the configuration files  -- which surprised me very much.

Anyway, for those who want to resize your gnome-terminal window permanently, here is the fix:

Right click on the gnome-terminal icon, and select "properties."  Then go to the "Command:" line and change the entry to something like this:

     gnome-terminal --working-directory=%f --geometry 90x45+76+429 --tab

You'll need to play around with the dimensions (90x45) of the window to make it suit your personal tastes.  Then, play around with the locators (+76+429) until the window opens exactly where you would like it to.  (The numbers I give here are for a 1280x1024 screen, and it puts the window over to the left side of the screen when it opens.  Just a personal preference.  The numbers are remarkably different for an 800x600 screen, and the numbers I have used might not even be on screen.)

The "--tab" opens a second tab in the gnome-terminal.  If you want two extra tabs, just add a second "--tab", and so on.  When you have multiple tabs open, you will get an annoying reminder every time you try to close the gnome-terminal.  You can shut this reminder off in the gconf-editor.  I don't remember the exact sequence, but can provide it if anyone can't find it on their own.

---

### Post by Zahrad on 2007-12-01
Folks,

I think this thread provides an alternative answer, (editing /usr/share/vte/termcap/xterm)  That's the way I do it, but hey, changing the default is not always preferable.

[http://ubuntuforums.org/showthread.php?t=15471](http://ubuntuforums.org/showthread.php?t=15471)

-Z

*post posting edit*
Noticed a little late it was for Edgy, and I'm using Gutsy, so... may not be relevant.  YMMV.

---

