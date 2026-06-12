---
title: "Ok, I'm about to give up, somebody please help me here"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by Catsworth on 2005-12-10
Hi Guys,

I'm desperately trying to find a way, any way, to edit the menus in Ubunto.

Right-clicking on the menus doesn't work.  Can't install Alacarte because python-xdg-0.15 isn't on my system, and that won't install because I have Python 2.4.1 and not 2.4.  And menu-editor doesn't do what I need it to (in other words, it won't delete any menu entries and it will only add to the stucture that's there, I can't create my own top-level menu items).

Here's the other thread I've got going, which doesn't look like it's going to produce any results at the moment.

[http://ubuntuforums.org/showthread.php?t=100359](http://ubuntuforums.org/showthread.php?t=100359)

I thought I'd post this in the absolute beginners are now because SOMEBODY else must have come across this :(

---

### Post by linbetwin on 2005-12-10
Did you try **Applications>System Tools>Applications Menu Editor**?

---

### Post by BoyOfDestiny on 2005-12-10
[QUOTE=linbetwin]Did you try **Applications>System Tools>Applications Menu Editor**?[/QUOTE]

Also try right clicking Applications, Places, or System and choose Edit Menus.

---

### Post by MartinG on 2005-12-10
I'm a Kubuntu (KDE) user, so I hesitate to trespass on Gnome ground :-) , but people in the forums seem to say that smeg does all you want.  Have you tried it?

---

### Post by Catsworth on 2005-12-10
[QUOTE=linbetwin]Did you try **Applications>System Tools>Applications Menu Editor**?[/QUOTE]

Yep, that menu editor will let me edit only specific parts of the structure.

I could, for example, add the following:

Applications
-- Accessories
-- -- {My New Menu Here}

But I couldn't add:

Applications
-- {My New Menu Here}

Also, for some reason, the Menu Editor app. won't let me delete any of the new entries I add (so I now have a fair smattering of "TestMenu" entries all over my menu structures!).

---

### Post by Catsworth on 2005-12-10
[QUOTE=BoyOfDestiny]Also try right clicking Applications, Places, or System and choose Edit Menus.[/QUOTE]

Nope, don't have that option when I right click (or when I click in any other way for that matter!).

---

### Post by Catsworth on 2005-12-10
[QUOTE=MartinG]I'm a Kubuntu (KDE) user, so I hesitate to trespass on Gnome ground :-) , but people in the forums seem to say that smeg does all you want.  Have you tried it?[/QUOTE]

I have looked at SMEG, which has now been renamed "Alacarte".

It won't install though because I don't have a sufficiently high ver. of Python-xdg (which also won't install because my ver. of python is _too_ high.....).

---

### Post by Estariel on 2005-12-10
I cannot help you much there since I don't use GNOME, but before you give up completely, you might want to give KDE a try, perhaps it works better for you...

---

### Post by Catsworth on 2005-12-12
Success at last!

Re-installed Ubuntu and now (after yet more buggering about with the sudoers file because, for some reason, Ubuntu doesn't set me up as being able to sudo for root) I can edit menus the way I should be able to.

Thanks for the help guys, much appreciated :)

---

