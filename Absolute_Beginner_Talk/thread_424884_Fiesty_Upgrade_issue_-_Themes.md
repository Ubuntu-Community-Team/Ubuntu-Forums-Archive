---
title: "Fiesty Upgrade issue - Themes"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by wog on 2007-04-27
When I click System -> Preferences -> Theme I get the following message:

"The default theme schemas could not be found on your system.  This means that you probably don't have metacity installed, or that your gconf is configured incorrectly."

I *think* metacity is installed, since it comes up during boot-up. I haven't the faintest idea what this gconf is about. I seem to have a lot of files and folders named that on the drive, if that makes any difference.

What do I do?

---

### Post by johnny4north on 2007-04-27
i believe that you only got the theme for the log in and you need to get the rest of the them here - [http://www.gnome-look.org/](http://www.gnome-look.org/)   there are themes for your log-in, menus/title bar and icon.

---

### Post by wog on 2007-04-27
> **johnny4north said:**
> i believe that you only got the theme for the log in and you need to get the rest of the them here - [http://www.gnome-look.org/](http://www.gnome-look.org/)   there are themes for your log-in, menus/title bar and icon.

I thought I remembered there being more than just one theme in the defaults, so you could choose from at least a few examples before having to go looking for something more substantial or interesting.

I took the error message to imply my Fiesty install wasn't complete, or was misconfigured. Any idea how to make sure it's configured properly?

And is there a quick and easy way to create your own customized themes?

---

### Post by johnny4north on 2007-04-27
i believe your system themes[default] are there and there is no real easy way to customize them[that i know of].  go here to this site for more themes and forums on how to install them - [http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by RomeReactor on 2007-04-27
Hi. wog, did you install **gnome-compiz-manager** (found in "System-->Preferences-->GL Desktop"), and if so, did you uncheck the "Use metacity theme" on the first tab? It's checked on my system, and I am able to change themes. Just a thought.

---

### Post by wog on 2007-04-27
> **RomeReactor said:**
> Hi. wog, did you install **gnome-compiz-manager** (found in "System-->Preferences-->GL Desktop"), and if so, did you uncheck the "Use metacity theme" on the first tab? It's checked on my system, and I am able to change themes. Just a thought.

I did not install gnome-compiz-manager, and I do not have a System -> Preferances -> GL Desktop.

Should I have one?

---

### Post by RomeReactor on 2007-04-27
Only *if* you installed gnome-compiz-manager. I thought you had that installed and the setting I described could be the problem.

> "The default theme schemas could not be found on your system. This means that you probably don't have metacity installed, or that your gconf is configured incorrectly."

To launch Gconf, open a terminal and enter

```
gconf-editor
```

Or to enable its menu entry permanently, right-click on the **Applications** menu, select "Edit Menus", and on "Applications", make sure "System Tools" is enabled; that's where you'll find it under the name **Configuration Editor**. In Gconf, the only references I could find were on ** schemas-->desktop-->gnome-->applications->window manager** and **schemas-->apps-->metacity**; don't know what you could look at there, sorry. Just be very careful not to change other settings there.

Also, are you on Feisty, Edgy, Dapper?

---

### Post by wog on 2007-04-27
> **RomeReactor said:**
> 
To launch Gconf, open a terminal and enter

```
gconf-editor
```

Or to enable its menu entry permanently, right-click on the **Applications** menu, select "Edit Menus", and on "Applications", make sure "System Tools" is enabled; that's where you'll find it under the name **Configuration Editor**. In Gconf, the only references I could find were on ** schemas-->desktop-->gnome-->applications->window manager** and **schemas-->apps-->metacity**; don't know what you could look at there, sorry. Just be very careful not to change other settings there.

Also, are you on Feisty, Edgy, Dapper?

I'm using Fiesty. I just upgraded to it from Edgy.

Well, gconf-editor works on the command line, anyway. However, I don't have an "Edit Menus" option under "Applications", so that might be something missing. Honestly, I don't even have a System menu under "Applications". How do I put that in place?

When I went into the Add/Remove option under Applications, I found several Configuration Editors, and I'm not sure which one to install, honestly. Here's something else that's weird -- when I filtered the list with the word "configuration" I found **Configuration Editor** like you said, but it's under System, and I don't have a System menu. So how do I get a System menu if I don't have one?

---

### Post by trellis on 2007-04-28
hi 

I ve the same problem too , but mines has just occurred since the last update . which i think had something to do with the gnome panel . I have no theme and when i try to change it i get the message 

"The default theme schemas could not be found on your system.  This means that you probably don't have metacity installed, or that your gconf is configured incorrectly."

any ideas ?

---

### Post by RomeReactor on 2007-04-28
Hi. I think both of you could try this: Open Synaptic (System-->Administration-->Synaptic Package Manager) and search for **human-theme**; if it appears, and is not installed, try to install it and see if it complains about a conflict with **human-gtk-theme**, which is the one that *should not* be installed. I think you'll also need to install **human-icon-theme** and **human-cursors-theme**. Or, to do it in one single command from the terminal:

```
sudo aptitude install human-theme human-icon-theme human-cursors-theme
```

provided the search in Synaptic shows they're not installed, or shows them marked as broken packages.

---

### Post by trellis on 2007-04-28
thanks for the reply 

The human theme is installed , i reinstalled it , but made no difference

---

### Post by trellis on 2007-04-28
Its seems as if its a bug since the last update, here it is reported at launchpad .
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/105609](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/105609)

Is there any way to undo the update , back to the way it was ?

---

### Post by trellis on 2007-04-30
I think i have found a fix for this problem here

[https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/50150](https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/50150)

the command :

$ sudo gconf-schemas --register /usr/share/gconf/schemas/*.schemas

seems to have done the trick and everything is fine now , hope this helps

---

### Post by wog on 2007-04-30
> **RomeReactor said:**
> Hi. I think both of you could try this: Open Synaptic (System-->Administration-->Synaptic Package Manager) and search for **human-theme**; if it appears, and is not installed, try to install it and see if it complains about a conflict with **human-gtk-theme**, which is the one that *should not* be installed. I think you'll also need to install **human-icon-theme** and **human-cursors-theme**. Or, to do it in one single command from the terminal:

```
sudo aptitude install human-theme human-icon-theme human-cursors-theme
```

provided the search in Synaptic shows they're not installed, or shows them marked as broken packages.

Human-theme is apparently installed.

On a hunch, I did a search through Synaptic for "-theme" and installed gnome-themes-extras, and it installed another theme at the same time, "SphereCrystal", which is probably a demo of those installed extras. 

Now the themes window works again. All the usual defaults are there and selectable.

I suspect what happened was, in order to install the new theme and extras, Synaptic had to fix my current problem with the rest of my themes. 

As an added bonus, it seems to have fixed my problems with setting my mouse. I'm good to go! :)

---

### Post by wog on 2007-04-30
> **trellis said:**
> I think i have found a fix for this problem here

[https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/50150](https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/50150)

the command :

$ sudo gconf-schemas --register /usr/share/gconf/schemas/*.schemas

seems to have done the trick and everything is fine now , hope this helps

Before I tried the above solution I tried yours. No good.
But it's fixed now, so I guess it's all okay anyway. 

Thanks for your help! :)

---

