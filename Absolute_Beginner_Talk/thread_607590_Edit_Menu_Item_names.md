---
title: "Edit Menu Item names"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by scriptsales on 2007-11-09
:(
OK, What I want to do shouldnt be rocket science, I dont mind editing text files but according to

[This Thread]("http://ubuntuforums.org/showthread.php?t=33606")

The Applications, Places, System items are hard coded. I cant change what these say? do I really have that little choice in customisation?

If these really are hard coded can I delete this main panel and make up one of my own?

---

### Post by hyper_ch on 2007-11-09
have you tried editing it with alacarte?

---

### Post by scriptsales on 2007-11-09
](*,)> **hyper_ch said:**
> have you tried editing it with alacarte?

See, This is the thing that is really frustrating me. All the items on the default menus are for stuff I would actually use, however, I justwant to change the name of the link. For example instead of "Hardware Information" I would like "Device Manager" I cant see any way to do that with Alacarte. I can add new menu Items so I suppose I could just build a new panel with my own names for stuff but whay should I have to?

I know its sad but all I want to be able to do is right click a menu Item and give it another name, shouldnt be too difficult should it? I'm sure there must be an operating system out there which would allow me to edit my menu structure this easily :wink:

By the way, what is with "Move to the deleted items folder" when you right click any document, whats wrong with just plain old "Delete"? :)

---

### Post by Dripbagulhos on 2007-11-09
> **scriptsales said:**
> :(
OK, What I want to do shouldnt be rocket science, I dont mind editing text files but according to

[This Thread]("http://ubuntuforums.org/showthread.php?t=33606")

The Applications, Places, System items are hard coded. I cant change what these say? do I really have that little choice in customisation?

If these really are hard coded can I delete this main panel and make up one of my own?

Hi scriptsales,

Go to System/Preferences/Main Menu (not sure these names are correct. My Ubuntu is localized Brazilian Portuguese :-) )

---

### Post by 3rdalbum on 2007-11-09
Right-click on your Applications menu and choose "Edit Menus".

At the bottom of the left pane you will see "Administration". Click this. Then right-click on "Hardware Manager" in the right pane, choose "Properties" and then change the name.

---

### Post by ace007 on 2007-11-30
There is no context menu when I try to right click in the right panel?

---

### Post by dimbulb1024 on 2007-11-30
> **ace007 said:**
> There is no context menu when I try to right click in the right panel?

Do it through the System>Preferences>Main Menu

When you open that window you can then right click the item, select Properties and it opens a dialog box where you can change the name.

---

### Post by CatKiller on 2007-11-30
> **scriptsales said:**
> ]By the way, what is with "Move to the deleted items folder" when you right click any document, whats wrong with just plain old "Delete"? :)

There is a Delete that you can enable that just deletes stuff - bypassing the Deleted Items folder entirely, like the **rm** command.

The default action isn't it. It just moves things to the Deleted Items folder. It seems substantially less confusing to label things by what they actually do.

---

### Post by CatKiller on 2007-11-30
If you want to change the file manually, you can do ```
sudo nano /usr/share/applications/hal-device-manager.desktop
``` The other menu entries are .desktop files in that directory too.

---

