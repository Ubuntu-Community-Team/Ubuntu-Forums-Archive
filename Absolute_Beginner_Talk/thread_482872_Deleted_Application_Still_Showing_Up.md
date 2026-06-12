---
title: "Deleted Application Still Showing Up"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Gus_T_Reer on 2007-06-24
Feisty Fawn
Gnome Desktop

Hi all,

Although I'm using Gnome I installed Kaffeine which is one of my favourite apps from my KDE days. The other day I noticed on the right mouse button context menu that I had 2 entries for it within the Open With... sub-menu.
I couldn't find a way to edit the menu so I completely deleted the application to see if it would reinitialise the context menu entries.

Now, although the application has been deleted I still have a single entry pointing to it in the right mouse button context menu.

I don't think this is a menu problem because if I right click on a mpg file and select Open With Other Application then Kaffeine is still showing up on the list of available applications. It has definitely been deleted so I was thinking, if I can remove Kaffeine from the list of apps that nautilus seems to thing it has then the entry on the context menu will also disappear.

Could someone tell me how to remove the reference to a deleted application, I assume it's in a config file somewhere.

Thanks

---

### Post by shifty_powers on 2007-06-24
system>preferences>main menu

also try:

```
sudo apt-get autoremove
```

---

### Post by Gus_T_Reer on 2007-06-24
Thanks for replying s_p.

The thing is that the Kaffeine entry from Applications/Sound & Video was deleted when I uninstalled the app and autoremove did some tidying but hasn't resolved the problem. When I right click on a mpg file and select Open With Other Application I'm given a list of applications to choose from. It is here that kaffeine is still showing up. Selecting it from here does nothing. I need to get rid of it from this list. Thanks

---

### Post by Gus_T_Reer on 2007-06-24
Well after getting to the situation where I had kaffeine uninstalled and still a single entry on the right click contect menu, I reinstalled it using apt-get-install and now it's working fine. App installed and a single entry on the context menu. Problem solved but still no wiser to the inner workings of Ubuntu.

---

