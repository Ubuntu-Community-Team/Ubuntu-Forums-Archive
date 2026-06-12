---
title: "[SOLVED] Where are user created menu items stored?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-02-05
Hi there.

Let me explain:

Using the package installer I have installed a program that I wrote and packaged myself. Its works just fine and creates a menu item for itself which also works fine.

If I navigate to /usr/shared/menu/  I can find the file (Plain text) that is associated with this menu item. I can open it and read it. No problems.

Using the "Edit Menus" application (Found by right clicking the menu in the taskbar), I am able to create a new menu which shows as it should, and I can also create a new item in this menu, that also works as it should.

However, I am unable to find the files associated with this new item.

The item in question was created by copying the information found in the properties of my installed application menu item. This all works just fine, and the newly created menu item opens my program correctly, just as it should. However I am unable to find the file that should go with this menu item.

I currently need to view this file and compare it to the one that is associated with the menu item that was created when my program was installed. I can find the installed one, but for the life of me I cant find the one that I just created manually.

Can anyone tell me where this item (And any others that I might create) are stored?

Thanks

Max

---

### Post by spiderbatdad on 2008-02-05
seems like it would depend on the types of files they were. For example, executables may have gone to /usr/bin/....pixmaps to /usr/share/pixmaps/ and so on.

---

### Post by jrothwell97 on 2008-02-05
Yes, apt works in funny ways... my only advice is to keep searching for said file, using the system-wide search if necessary.

---

### Post by MaxVK on 2008-02-05
The files should be plain text if they are like the one that was installed.

I can find the one that the package manager installed - thats where it should be, but Iv done a system search for the items I create myself and I cant find them anywhere!

Im looking for the items I manually created in the menu editor. They should have a plain text file associated with them, just like the menu item that was installed by the package manager, but so far I cant find any reference to the new menu items anywhere, let alone find the files that should be associated with them.

---

### Post by y-lee on 2008-02-05
Interesting question,  ya might want to see this [Menu editing in the GNOME 2 desktop]("http://www.gnome.org/start/2.0/menuediting.html") as well as the link on the bottom of that page.

---

### Post by MaxVK on 2008-02-05
Thanks for the link - its an interesting read, but unfortunately hasn't helped me in the slightest!

---

### Post by y-lee on 2008-02-05
I'll look around and give it some thought making no promises  i can figure it out. I'm thinking it is somewhere in your home directory ... ah maybe all menu items you create using alacarte in one file alacarte loads. I could be wrong but it would make sense for alacarte to keep user specific stuff in user home dir somewhere. 

Write the programmer of one of the developers of alacarte, he has a web site i found it earlier tho i didn't bookmark. lol. If anyone would know he would.

---

### Post by MaxVK on 2008-02-06
It certainly makes sense to keep this stuff in the users home dir, but Iv been through that with a fine toothed comb (Okay, so Iv not examined *every* file, but there were plenty of teeth on the comb anyway) and Iv not found them yet!

---

### Post by y-lee on 2008-02-06
Try looking at the file **applications.menu** found

```
 /home/username/.config/menus
```

and from that file I found a menu item i created  in the directory

```
/home/username/.local/share/applications
```

it was a launcher not a text file for items you added yourself to alacarte.

---

### Post by Gen2ly on 2008-02-06
I believe you are looking for .desktops.  These are files that contain information about every menu entry.  It lookes like ubuntu may be different that other distros?  On my current system they are located globally at [COLOR="Green"]/usr/share/applications[/COLOR].  They can also be added locally in the [COLOR="Green"]~/.local/share/applications[/COLOR].

---

### Post by MaxVK on 2008-02-06
Thanks y-lee - I found them once already, but the item I added wasn't there. Iv just looked again and now it is. Maybe I couldn't see the wood for the trees!

Cheers

Max

---

### Post by y-lee on 2008-02-06
Glad ya found it. I just had to take the time to look, should've looked to begin with instead of googling it.:lolflag:

---

