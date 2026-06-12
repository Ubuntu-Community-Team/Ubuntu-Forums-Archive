---
title: "Applications menu problem??!"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by _mOrgoth_ on 2006-06-06
Hi!
I am new user (noob). Few days ago i downloaded and install xubuntu. I was doing something with applications menu edit, dont know whay or why, but i did, and now when i click on applications menu nothing happens???
Same thing with right click on desktop!

I tried to find solution but i only ](*,) 

HELP!!!!!

---

### Post by Osamabingandhi on 2006-06-06
i found one solution, write "metacity &" in terminal....that fixed the panel-menu but still i cannot find a solution for the rightclick on the desktop. It doesn't work on my ubuntu login either...

---

### Post by fluffington on 2006-06-07
The same thing happened to me. I'm running Ubuntu now and not Xubuntu, so I may be a little off on this, but try the following:

```
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml
```

What that does is copy the default menu file to your home directory. What had happened with me is that I somehow added an extra space or something somewhere in the menu.xml file and the next time I loaded up the menu editor, it saw invalid XML and deleted the whole thing. Reloading the default fixed it and I didn't have the problem again.

---

### Post by fluffington on 2006-06-07
[QUOTE=Osamabingandhi]i found one solution, write "metacity &" in terminal....that fixed the panel-menu but still i cannot find a solution for the rightclick on the desktop. It doesn't work on my ubuntu login either...[/QUOTE]

I don't think that so much fixed the problem as loaded your GNOME panel on top of the XFCE one. XFCE uses XFWM and not Metacity as it's window manager.

---

### Post by _mOrgoth_ on 2006-06-07
Ok, thx for help, but how can i write in terminal when i dont haw applications menu?????:confused: 

How to reach terminal? Only thing that works is right click on applications menu icon.
When i clik Edit menu is says: "Error!  File doesn't exist!":-k

---

### Post by bradh on 2006-06-07
[QUOTE=fluffington]The same thing happened to me. I'm running Ubuntu now and not Xubuntu, so I may be a little off on this, but try the following:

```
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml
```

What that does is copy the default menu file to your home directory. What had happened with me is that I somehow added an extra space or something somewhere in the menu.xml file and the next time I loaded up the menu editor, it saw invalid XML and deleted the whole thing. Reloading the default fixed it and I didn't have the problem again.[/QUOTE]

Thanks - although I am not the original OP, this worked for me!  I can't recall having fooled around with any .XML files, and I was very frustrated while trying to resolve this problem by deinstalling/reinstalling Xfce* and xdesktop and xubuntu.  I wonder if this problem was not caused by "wetware" problems, but may have been a problem introduced by one of the "regular" updates, post-Dapper?

---

### Post by fluffington on 2006-06-07
[QUOTE=_mOrgoth_]How to reach terminal?[/QUOTE]

Use ALT-F2 to bring up the run application dialog and type in "xfce4-terminal" (without the quotes) to start the terminal. Or just type the command in that box.

Or you can hit CTRL-ALT-F1 to bring up the first virtual terminal, do stuff there, then switch back to X with CTRL-ALT-F7 (that's what I do).

---

### Post by Jose Catre-Vandis on 2006-06-08
[QUOTE=fluffington]The same thing happened to me. I'm running Ubuntu now and not Xubuntu, so I may be a little off on this, but try the following:

```
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml
```

What that does is copy the default menu file to your home directory. What had happened with me is that I somehow added an extra space or something somewhere in the menu.xml file and the next time I loaded up the menu editor, it saw invalid XML and deleted the whole thing. Reloading the default fixed it and I didn't have the problem again.[/QUOTE]


Thanks, this got my applications menu back, but not the desktop right click.

After you have done the copy, type this into a terminal:

> xfdesktop &

This works while the terminal screen is open. You might then have to go:

Applications>Settings>Desktop Settings

and tick the box that allows xfce to manage the desktop. And just for the heck of it, check under the Behaviour tab that "Show Desktop Menu on right click" is ticked too :-)

You should now have your right click menu back :-)

---

### Post by _mOrgoth_ on 2006-06-08
[QUOTE=fluffington]The same thing happened to me. I'm running Ubuntu now and not Xubuntu, so I may be a little off on this, but try the following:

```
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml
```

What that does is copy the default menu file to your home directory. What had happened with me is that I somehow added an extra space or something somewhere in the menu.xml file and the next time I loaded up the menu editor, it saw invalid XML and deleted the whole thing. Reloading the default fixed it and I didn't have the problem again.[/QUOTE]

THX=D>  Right click on destop also works.

---

### Post by _mOrgoth_ on 2006-06-08
[QUOTE=fluffington]Use ALT-F2 to bring up the run application dialog and type in "xfce4-terminal" (without the quotes) to start the terminal. Or just type the command in that box.

Or you can hit CTRL-ALT-F1 to bring up the first virtual terminal, do stuff there, then switch back to X with CTRL-ALT-F7 (that's what I do).[/QUOTE]


THX:grin: 

Now i now how to reach terminal!!

---

### Post by Brian Kendig on 2006-06-08
I hit the same exact problem. I'll log it as a bug.

---

### Post by Brian Kendig on 2006-06-08
Actually, it's already been logged as bug 48178.

[https://launchpad.net/distros/ubuntu/+source/xfdesktop4/+bug/48178](https://launchpad.net/distros/ubuntu/+source/xfdesktop4/+bug/48178)

---

