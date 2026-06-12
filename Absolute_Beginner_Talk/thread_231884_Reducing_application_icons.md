---
title: "Reducing application icons"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by coffeejunkie on 2006-08-07
Hi,

Just installed for the first time... and it's working!! [-o< 

I'm looking for a way to reduce the large icons in my applications to save space on my screen.  Firefox and OpenOffice icons in particular seem oversized, but also the icons on "Applications, Places and System" are too big for my taste.

I found heads of tipps how to reduce desktop or nautilus icons but none that describes how to control the applications.  Any way to do this for all applications?  And/or separately for the ones that seem too large?

Many thanks!

---

### Post by JcZndeR on 2006-08-07
> **coffeejunkie said:**
> Hi,

Just installed for the first time... and it's working!! [-o< 

I'm looking for a way to reduce the large icons in my applications to save space on my screen.  Firefox and OpenOffice icons in particular seem oversized, but also the icons on "Applications, Places and System" are too big for my taste.

I found heads of tipps how to reduce desktop or nautilus icons but none that describes how to control the applications.  Any way to do this for all applications?  And/or separately for the ones that seem too large?

Many thanks!

Since the desktop is controlled by nautilus, to reduce the icons on your desktop just open your file browser and change your prefs.  To do them separately right-click icon.
Your places and system problem can be solved by running gconf in the terminal and changing the menubar to drawer instead of bar or something like that.. I am not on ubuntu right now so I can find it for you to tell you which one to change.. You can ask someone else.

This is only AFAIK so im sorry if it is inaccurate.

Edit:  To clarify the menubar solution changes the bar into a single icon that way you can change the default ubuntu one and its much smaller.  But all your menus will collapse into one so this might not be a desired solution.  (You can always change the panel's pixel size, but that only works to a certain extent.)

---

### Post by JcZndeR on 2006-08-08
> **JcZndeR said:**
> Since the desktop is controlled by nautilus, to reduce the icons on your desktop just open your file browser and change your prefs.  To do them separately right-click icon.
Your places and system problem can be solved by running gconf in the terminal and changing the menubar to drawer instead of bar or something like that.. I am not on ubuntu right now so I can find it for you to tell you which one to change.. You can ask someone else.

This is only AFAIK so im sorry if it is inaccurate.

Edit:  To clarify the menubar solution changes the bar into a single icon that way you can change the default ubuntu one and its much smaller.  But all your menus will collapse into one so this might not be a desired solution.  (You can always change the panel's pixel size, but that only works to a certain extent.)


I was mistaken its gconf-editor not gconf and also I found where the panel settings are.  It is under apps/panel/objects/object_*.
* This is a number which refers to which panel object it is.  I don't know which one is one your computer so just try them.  I changed mine so I am not sure but I think you are looking for something that says menu-bar in the object_type key.  Once you fine it change it to menu-object.

That should work.

---

### Post by coffeejunkie on 2006-08-09
> **JcZndeR said:**
> It is under apps/panel/objects/object_*.
* This is a number which refers to which panel object it is.  I don't know which one is one your computer so just try them.  

Thanks!

I found the item for the menu-bar but what I had in mind is changing the image sizes rather than collapsing the menus.  I imagine that's also somewhere in gconf but couldn't find it.  Does it come with the theme or is there a global setting? :-k 

Many thanks!

---

### Post by JcZndeR on 2006-08-12
> **coffeejunkie said:**
> Thanks!

I found the item for the menu-bar but what I had in mind is changing the image sizes rather than collapsing the menus.  I imagine that's also somewhere in gconf but couldn't find it.  Does it come with the theme or is there a global setting? :-k 

Many thanks!

As I said in my first post I didn't think this was what you wanted but I don't know about doing it any other way...  I guess its a theme?  But I personally do not know of any way to do this, I made mine using the instructions above and changed my icon to a Penguin!  ;)

---

