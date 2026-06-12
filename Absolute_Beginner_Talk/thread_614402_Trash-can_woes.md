---
title: "Trash-can woes"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by eDRoaCH on 2007-11-15
I am setting up a winxp box inside virtualbox that will be dedicated completely to work. This way I can play with my computer any way I want! (I dont believe this belongs in the virtualization category because it really has nothing to do with it, and the answer is probably basic)

Anyway, I got a few files off our domain server to set it up. Installs for the vpn, office, etc.

I copied them from a usb stick to copy them to xp thru the virtualbox shared folder (a folder in my home directory)

When I moved them there, I got errors that it couldnt delete the source because I didnt have the permission. As it copied them anyway I didnt care at the time.

Well short story even shorter, I now have a trash can that wont empty. The avant icon says its empty, but a short time later refills itself. The default gnome one  says 

```
/home/edroa...i/atl71.dll" cannot be deleted because you do not have permissions to modify its parent folder.
```

how do i fix this?

---

### Post by ramjet_1953 on 2007-11-15
Probably the easiest way to fix this is to open a terminal and type this in:

Code:

[COLOR="Red"]gksu nautilus[/COLOR]

Enter your password, when prompted

Nautilus will now open in super user mode.

Now, click on View in the top panel of nautilus. When the drop-down menu opens, click on [COLOR="Blue"]Show Hidden files[/COLOR].

Now, navigate to [COLOR="Blue"]File System /home/*your user name*/.Trash[/COLOR]

Don't forget the'.' before Trash

You should now be able to delete the files by rigt clicking on them and choosing delete.

Regards,
Roger :cool:

---

### Post by eDRoaCH on 2007-11-15
thanks, worked like a charm. I should have read the error better to see where the files were.

---

