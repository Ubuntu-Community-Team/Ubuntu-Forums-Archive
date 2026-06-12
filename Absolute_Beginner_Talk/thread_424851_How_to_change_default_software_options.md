---
title: "How to change default software options?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by ebattleon on 2007-04-27
How do i change the default sofware options in dapper?

For Example if i want to change my torrent client from Bit Torrent to Azureus in Firefox.

1) Opening X.torrent dialog
2) Open With **Bit Torrent (Default)** click drop down bar, and select **Other**.
3) Choose Helper Application Dialog.

Then what? In what folder/s are applications stored in Dapper?

Is there a web site or wiki explaining what each folder means in Dapper?

thanks in advance

ebattleon:confused:

---

### Post by zvacet on 2007-04-27
When you click on **other** you must see window with list of apps.From that list select one you want.If it is not on the list at the bottom you have option **use special command**.open that and type app name wich you want to use as default.

---

### Post by ste82 on 2007-04-27
see the post at the bottom of this thread:

[http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

I got mine working by adding this:

application/x-bittorrent; /opt/azureus/azureus

to this file:

/etc/mailcap

---

### Post by zurn on 2007-07-10
thx that worked great!

---

### Post by denBosch on 2008-01-21
> **zvacet said:**
> When you click on **other** you must see window with list of apps.From that list select one you want.If it is not on the list at the bottom you have option **use special command**.open that and type app name wich you want to use as default.

No, when I click on "Other", I get a dialogue called "Choose helper application", but it doesn't have a list of applications. It's just a standard "select file" dialogue -- i.e. I have to look through the filesystem for the application I need. I know where applications are stored on Windows (in a folder called "Program Files"), but I have no idea where they are stored on Linux. I've done a full search for files called "azureus", but can't find any executable. I don't understand, do you even have executable files on Linux? If not, how am I supposed to "Choose helper application"?

I tried to make Azureus the default app for ".torrent" files, by right-clicking and choosing "Open with other application" and then choosing Azureus, but this didn't change the default -- if you double-click on a .torrent file, it still opens with the "BitTorrent" application. I even tried to uninstall the BitTorrent app, but Synaptic warned me that other important things would stop working, so I didn't.

This situation is ridiculous; all I want is to be able to click on a torrent link in Firefox, and have it automatically open with Azureus, which is my favourite torrent application. I had it working like that on Windows without any problems. It's crazy if I can't do the same thing on Linux, which is supposed to be more customisable, not less. Why is Ubuntu trying to make me use the over-simple "BitTorrent" application? If anyone has any suggestions, I would be very grateful.

---

