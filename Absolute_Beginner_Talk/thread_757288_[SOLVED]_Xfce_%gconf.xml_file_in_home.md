---
title: "[SOLVED] Xfce: %gconf.xml file in /home"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Bruce M. on 2008-04-16
I'm running Xubuntu 7.10 and have a strange file in my /home directory that I don't understand: %gconfig.xml

It's not hidden, here's the contents:
```

<?xml version="1.0"?>
<gconf>
        <entry name="network_icon_visible" mtime="1208299247" type="bool" value="false">
        </entry>
        <entry name="home_icon_name" mtime="1208299247" type="string">
                <stringvalue>Home</stringvalue>
        </entry>
        <entry name="computer_icon_visible" mtime="1208299247" type="bool" value="true">
        </entry>
        <entry name="home_icon_visible" mtime="1208299247" type="bool" value="true">
        </entry>
        <entry name="trash_icon_visible" mtime="1208299247" type="bool" value="true">
        </entry>
        <entry name="volumes_visible" mtime="1208299247" type="bool" value="false">
        </entry>
</gconf>

```
Any ideas as to what it is?
Can I delete it?

Thanks for your time.
Bruce

---

### Post by Meskarune on 2008-04-16
Its a gnome configuration file. and from the looks of it I think it might be for the icons on your desktop. Its best to leave most config files alone...unless you are deleting an application, and then they should only be deleted through synaptic. I hope that helps.

---

### Post by Bruce M. on 2008-04-16
> **Meskarune said:**
> Its a gnome configuration file. and from the looks of it I think it might be for the icons on your desktop. Its best to leave most config files alone...unless you are deleting an application, and then they should only be deleted through synaptic. I hope that helps.

OK, but I'm running Xubuntu not Ubuntu.

Strange... if it's onky for Icons, I'm going to change one to true and see what happens.
Be back soon, I may need a Ctrl+Alt+Backspace

Thanks for the response
Bruce

---

### Post by Meskarune on 2008-04-16
Xubuntu also runs gnome. lol. Its what sets your system color themes. Xfce is just the window manager: just the frames/buttons of the windows and the panels. :)

But good for you for experimenting.

---

### Post by Bruce M. on 2008-04-17
> **Meskarune said:**
> Xubuntu also runs gnome. lol. Its what sets your system color themes. Xfce is just the window manager: just the frames/buttons of the windows and the panels. :)

But good for you for experimenting.

Here's what I did:

[LIST=1]
[*]I tested changing one false to true and one true to false.
[*]Re-started PC rather than do a session restart.
[*]No changes
[*]Changed back to the original false true statements and
[*]Re-started PC again
[*]No changes
[*]So then I renamed the file to **%gconfig.lmx** and there is no difference.
[/LIST]
**Conclusion:** fairly certain it's NOT needed.

It's still there as an **.lmx** file and I'll remove it after a few days when I'm 100% sure it's not needed.

Thanks for your help.
Bruce

---

