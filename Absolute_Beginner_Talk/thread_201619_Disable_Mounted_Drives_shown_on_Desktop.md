---
title: "Disable Mounted Drives shown on Desktop"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by yy1124 on 2006-06-22
HI, just curious ?
Is there anyway to disable mounted drives showing on desktop?

Just that sometime I wanted a total clean desktop

thankx

---

### Post by mozetti on 2006-06-22
Yes, I think it's in the gconf configuration tool. Should be under Apps->Accessories, if memory serves. There's an option in there to show/hide them. I'm at work, so I don't have Ubuntu here to verify the exact location, but I know it's there somewhere.

---

### Post by _simon_ on 2006-06-22
Ok well firstly see if you have configuration editor displaying in Applications -> System Tools.

IF NOT:

Right click on Applications and select "Edit Menus" 
Select "System Tools" and put a tick in the box next to "Configuration Editor" then press close and go back to your Applications -> System Tools menu and select "Configuration Editor"

NOW IN CONFIGURATION EDITOR:

apps -> nautilus -> desktop

To hide mounted drives on the desktop, untick "volumes_visible"

Then close Configuration Editor and you're done :)

---

### Post by yy1124 on 2006-06-22
I manage to use the Configuration Editor and hide those volume from desktop,

thx Simon and Mozetti:D

---

