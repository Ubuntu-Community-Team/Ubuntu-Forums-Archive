---
title: "How to switch off &quot;Mouse battery low&quot; pop-up ?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by laffinet on 2008-02-04
Everytime I log in I get a pop up saying "Mouse battery low" or "below 14%" or something like it. While this might be true the mouse is usually working for at least a few more days. This is very annoying, so I would just like to turn the notification off (I'll notice soon enough myself once the batteries are empty).

Where can I switch this notification off ?

Thanks for the help.

---

### Post by Ebuntor on 2008-02-09
The only way I can think of to disable the pop-up is to disable all the power-manager pop-ups, if you're using a laptop the battery notification would be disabled too.

Here's how to disable it:
Press Alt+F2 and run the program "gconf-editor" (without the quotes).
Once the Configuration Manager has started up in the left pane double click on "apps" => "gnome-power-manager" => "notify" and uncheck the "low-power" box.

Hope that helps :)

---

### Post by laffinet on 2008-02-09
I'll try that. Thanks.

Guess I just have to be careful that I don't run out of laptop battery power...

---

### Post by laffinet on 2008-02-09
Hm. Didn't actually work. Changed the entry in gnome-power-management but still got the notification.

Annoying.

---

### Post by Ebuntor on 2008-02-10
> **laffinet said:**
> Hm. Didn't actually work. Changed the entry in gnome-power-management but still got the notification.

Annoying.

You did? That is really odd. I'll have to look into that.

---

### Post by David_1cog on 2008-03-23
It looks like that power setting is just for main battery - not the mouse battery.

Any other suggestions?  I get the low battery warning on every boot - even if there are fresh batteries in my mouse with weeks of charge left.

---

### Post by kindofabuzz on 2008-07-24
Yeah I get the same thing, even if the batteries have been charging all night it ALWAYS says they are low at %14. Bug?

---

### Post by DavidONE on 2008-07-24
What mouse is everyone using?  Is there a pattern?

I have a Logitech Trackman FX in PS/2 port and a Logitech MX1000 in USB.  I haven't tested to see which (or both?) of these is causing the issue.  Also, mine always reports 28%.

I also found that by editing menu item for 'Update Manager' and adding 'gksu' so that password is requested at application start, this also triggers the battery warning.

Not a big deal, but irritating.  

I see kindofabuzz just raised a bug: [https://bugs.launchpad.net/ubuntu/+bug/251498/](https://bugs.launchpad.net/ubuntu/+bug/251498/)

---

