---
title: "How to Add &quot;Refresh Desktop&quot; to Context Menu?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by LordKelvan on 2007-06-09
Hi:

I hope no one gets mad for such an inane question, but one thing I mix from windows is the "Refresh Desktop" item in the context menu (for some reason I like clicking it a lot :D).  I was wondering how I might be able to add such an entry to the Ubuntu desktop context menu?  

I know what the keyboard shortcut ctrl+r will refresh the desktop, so I guess I am wondering how I might add an entry into the context menu that executes that key sequence?

Thanks in advance.

---

### Post by Pragmatist on 2007-06-10
I'm not sure I know what your referring to.  Do you mean "show desktop"?  Anyway, there is a program called "xrefresh" that you might want to look into (it is in the repositories and should already be installed on your system. Type "man xrefresh" in a terminal to find out more)

---

### Post by ThinkBuntu on 2007-06-10
F5. Saves you a motion (right click + left click).

---

### Post by LordKelvan on 2007-06-10
Hi:

Yes, I understand F5 will refresh, but what I am saying is that I enjoy refreshing the desktop by selecting it from the context menu (yes I its weird, just a habit I picked up).

Pragmatist: No, I mean "Refresh Desktop" - when you right-click somewhere on a Windows desktop, there will be such a menu item.  I checked out the xrefresh prog, but that seems a bit much.

Maybe I should make this a bit more general: I want to add an item to the desktop context menu that will execute a key combo (in this case ctrl+r).  Anyone know how to do this?

---

### Post by Pragmatist on 2007-06-10
Here is how to make a launcher:
[http://linuxfud.wordpress.com/2007/02/15/add-a-refreshreload-gui-button-to-your-gnome-panel/](http://linuxfud.wordpress.com/2007/02/15/add-a-refreshreload-gui-button-to-your-gnome-panel/)

According to that link, the command you need is:
```
**killall gnome-panel nautilus**
```

If you want to add this to the desktop context-sensitive menus, you make a script and put it in ~/.gnome2/nautilus-scripts

Here is how you do that:

1.) Open an editor and make the script:
```
gedit Refresh
```

Now enter this code into the script:
```

#!/bin/sh
killall gnome-panel nautilus;
exit;

```

and save the file.
2.) Copy the file to ~/.gnome2/nautilus-scripts

3.) Make the file executable (type this in the directory you saved the file):
```
chmod a+x Refresh
```

Now you should see the command when you Right-click (it might be in a sub menu called "scripts")

---

### Post by LordKelvan on 2007-06-10
Hi:

Thank you for your help, however that doesn't appear to be what I am looking for.  When I try to execute "killall nautilus" (the refresh desktop part of your command), it doesn't behave in the same way as pressing ctrl+r.

When I press ctrl+r on my system, what it does is like it just reloads the desktop and only the desktop (as if the desktop were a page in a web browser).  I have searched around, but it seems like there is no mention of ctrl+r shortcut, so I have no idea what command it is executing when I do that.

Can anyone help me?

---

### Post by LordKelvan on 2007-06-16
anyone?

---

### Post by deepclutch on 2008-02-04
sorry for bumping :D I too want to get an answer.does someone help me add Refresh option in Desktop right click menu :)
the command I want to add is "xrefresh -white" :p

Please Help dear :D

---

