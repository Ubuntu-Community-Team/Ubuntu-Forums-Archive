---
title: "Icon Theme Problem"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by puke929 on 2007-09-11
Ive downloaded a icon theme off gnome-look.org but cant seem to find a way of getting them working. i tried a couple of things but realisticly im no good at this stuff so atm i have a tar.gz and i have just the folder on my desktop.. could someone give me a simple or well explained way of doing this. Dont make the assumption that i can do anything becouse i cant!
cheers, Luke

---

### Post by chrome307 on 2007-09-11
Go to SYSTEM - PREFERENCES - THEME MANAGER

Once you've opened that up, just drag the folder directly into the Window and it will install itself

---

### Post by K.Mandla on 2007-09-11
Or, if you like, you can do it the hard way by making a folder called .icons (with a dot in front) inside your home folder, if one doesn't already exist.

```
mkdir ~/.icons
```
Then decompress your theme into that folder, like this.

```
tar -xvzf name_of_your_theme_goes_here -C ~/.icons/
```
Then set the theme through the theme selector if you're using Gnome or XFCE, or however it's done in KDE. You can also hand-edit the .gtkrc.mine file to include the theme. 

But really, it's easier to drag and drop into the theme manager. ;)

---

