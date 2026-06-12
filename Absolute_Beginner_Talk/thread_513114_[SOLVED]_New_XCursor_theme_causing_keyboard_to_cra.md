---
title: "[SOLVED] New XCursor theme causing keyboard to crash apps"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Shadow ZERO on 2007-07-30
Hi,

I installed a new XCursor theme from gnome-look.org.

[http://gnome-look.org/content/show.php/Silver+XCursors+3D?content=5533]("http://gnome-look.org/content/show.php/Silver+XCursors+3D?content=5533")

Here's the installation steps:
______________________________________________________________________________
Installation:

Copy the two folders 'Silver' and 'default' to your ~/.icons directory and
restart your X-Server.
______________________________________________________________________________

I had to do something different to make it work though.  I had to put the main folder "Silver" in my usr/share/icons directory.  I also had to take the index.theme file from the "default" folder in the archive and put in in the main "Silver" folder(along with the cursors subdirectory).

After that i was able to select the Silver theme from my Preferences/Mouse/Pointers.  It looks fine at first, but then almost any keyboard activity crashes whatever application i'm using.  In nautilus selecting a file in a directory and pressing a key to skip to the first file starting with that letter will cause nautilus to crash and restart.  Even the search feature from the main menu crashes it (i'm using Linux Mint btw).  The main terminal won't even start, i have to use xterm.

If i switch back to one of my default pointer styles everything goes back to normal.  How can i get this to stop so i can use the new mouse theme?

---

### Post by Kralizec on 2007-08-08
I've had this exact problem before except with another cursor theme. I don't believe I ever got it fixed and I think I had to abandon the cursor theme. The only thing I might suggest is to revert the 'default' directory to what it was before installing the theme.

---

### Post by jancelis on 2008-06-03
I have the same problem when using crystalcursors-1.1.1 mouse theme.
It used to work in 7.10 but not anymore in 8.04. In 8.04 GDM uses crystalcursors and the mouse works. As soon as I touch my keyboard GDM crashes.
I don't think this problem is "SOLVED"

---

