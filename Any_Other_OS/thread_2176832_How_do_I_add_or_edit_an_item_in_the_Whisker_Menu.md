---
title: "How do I add or edit an item in the Whisker Menu?"
date: 2013-09-26
forum: Any Other OS
---

### Post by abisdad on 2013-09-26
Hi any Whisker experts out there!

How do I add an item into the Whisker Menu?

I've installed a program onto my XFCE Mint system, which didn't add itself and cannot work out how to add an item into the Whisker Menu - very frustrating!

...Or am I just being thick?...

Thanks,

Rob.

---

### Post by slickymaster on 2013-09-26
Don't know if it applies, but have you already seen this: [http://forums.linuxmint.com/viewtopic.php?f=110&t=144907#p766982](http://forums.linuxmint.com/viewtopic.php?f=110&t=144907#p766982) ?

---

### Post by ncy on 2014-04-23
> **abisdad said:**
> 
I've installed a program onto my XFCE Mint system, which didn't add itself and cannot work out how to add an item into the Whisker Menu - very frustrating!

...Or am I just being thick?...


Hi there! Not thick at all. I realize this is an old thread, but I came across the same problem because I recently installed Xubuntu 14.04 and Whisker now comes standard on it. I installed usb-creator-gtk (a.k.a. "Startup Disk Creator"), and the launcher never showed up. On the other hand, when I installed synaptic, it popped up in the Whisker menu no problem!

I googled and google and googled to no avail. I decided to settle for the old "Applications Menu" as mentioned in the link by slickymaster, but usb-creator-gtk was still missing! Also, no more Alacarte (now it's MenuLibre) so the menu entries were all exactly the same as the Whisker menu -- well, unless I created my own Custom Menu File, which I did not want to do. The thing I found frustrating was that in MenuLibre (right-click the Whisker menu icon and go to "Edit Applications", or just type "menulibre" in a terminal), the launchers were there! In fact, a whole lot of launchers are there that just don't show up. To me, Whisker is useless if the Search function can't even find the programs I'm looking for.

So after some comparisons of the .desktop files from /usr/share/applications, I found that removing the "Settings->Settings" category does the trick. I did this through MenuLibre because I didn't want to deal with editing .desktop files. Remember to save the changes for each launcher! It will automatically create an updated launcher file in ~/.local/share/applications.

hth

---

### Post by Lemuriano on 2014-04-24
I use lxmed (lx menu editor) in Sabayon and is also in the Gentoo repositories. Perhaps this link is of some use: [http://askubuntu.com/questions/54303/gui-for-editing-menu-in-xubuntu](http://askubuntu.com/questions/54303/gui-for-editing-menu-in-xubuntu)

[ATTACH=CONFIG]252473[/ATTACH]

Regards

---

### Post by slickymaster on 2014-04-25
> **Lemuriano said:**
> I use lxmed (lx menu editor) in Sabayon and is also in the Gentoo repositories. Perhaps this link is of some use: [http://askubuntu.com/questions/54303/gui-for-editing-menu-in-xubuntu](http://askubuntu.com/questions/54303/gui-for-editing-menu-in-xubuntu)

[ATTACH=CONFIG]252473[/ATTACH]

Regards

Can't pronounce myself regarding Xfce Mint (the system mentioned by the OP) as I've never tried it, but in what Xubuntu is concerned, and from 14.04 onward, the link you provide isn't of use since Alacarte has been replaced by MenuLibre (2.0.1) for editing menus.

---

### Post by ridgeland on 2014-05-09
Thank you ncy
I wondered why menulibre would replace alacarte since it's doesn't work.  With your help I can now have the functionality of alacarte for hidding or showing items.  In alacarte it was a simple check box on/off - done.  But in menulibre with your work around I can now hide or show an item by first getting the item functional by clicking on the item say "Software Updater"  then clicking on "System system" in the tab "Categories" then clicking on the [-] minus sign at the bottom then clicking up at the top on the second icon just right of the [+] to save the change.  Then I can click on the toggle On/Off to hide from menus.
So for me the fix is use alacarte and throw away menulibre - I'll look at menulibre again when 14.10 is released.  Maybe by then the installation will have been fixed.
I'm using Xubuntu 14.04

---

