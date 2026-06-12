---
title: "Icons on the desktop!  How do I?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by doublecheese on 2007-06-11
Hi!

I'm using Feisty.  I read somewhere that part of the simplicity of Ubuntu comes from no icons being on the desktop at start.  That's all fine and well but I'd like to get various icons (such as Computer, Trash, etc...) to show up on the desktop.  How would I go about doing that?

---

### Post by RomeReactor on 2007-06-11
Hi. Try dragging icons from the menu (if the ones you want are there) to the desktop.

---

### Post by doublecheese on 2007-06-11
Doh!  It worked fine for Computer but what about Trash?  Right now the trash is in the bottom right corner of the menu bar.  I can't get it to create a shortcut.

---

### Post by RomeReactor on 2007-06-11
Sorry; I have yet to figure that one out myself... :-k

---

### Post by doublecheese on 2007-06-11
I know it can be done.  I've seen plenty of GNOME screenshots with the trash sitting on the desktop.  I just don't know how :p

---

### Post by Chris S. on 2007-06-11
type gconf-editor in a terminal.

Go to apps->Nautilus->Desktop

Click on the right option, there should be one for trash (edit: it's trash_icon_visible, sorry).

---

### Post by ramjet_1953 on 2007-06-11
To put trash, computer, home folder, etc on your desktop do this:

Copy and paste this into a terminal:

[COLOR="Red"]gconf-editor[/COLOR]

A window will open with a nested menu selection.

Navigate to [COLOR="Blue"]apps>nautilus>desktop[/COLOR]

In the right panel, just put a tick in the boxes of the icons that you want visible.

Viola! you now have a working trash can and other icons on you desktop!

By the way, if you want a [COLOR="Blue"]documents icon[/COLOR] on the desktop, you have to make the folder first in nautilus.

Regards,
Roger :cool:

---

### Post by doublecheese on 2007-06-11
You guys are awesome!  This forum is awesome!  Thanks so much!

Really guys.  Thanks :)

---

### Post by jimrz on 2007-06-11
> **doublecheese said:**
> I know it can be done.  I've seen plenty of GNOME screenshots with the trash sitting on the desktop.  I just don't know how :p  

in the configuration editor (gconf-editor) go to apps > Nautilus > desktop and put a check in the box next to "trash_icon_visisble" you can also give the icon a name if you like

---

### Post by Go_Bucks on 2007-07-28
I stumbled across this trying to figure out why icons don't show up next to program names on the menu bar in Ubuntu Feisty. If I go into gconf editor to apps>nautilus>desktop the only item present is "start state" and when I click on it, it tells me "This key has no schema". Can anyone help with this?

---

### Post by mcduck on 2007-07-28
> **Go_Bucks said:**
> I stumbled across this trying to figure out why icons don't show up next to program names on the menu bar in Ubuntu Feisty. If I go into gconf editor to apps>nautilus>desktop the only item present is "start state" and when I click on it, it tells me "This key has no schema". Can anyone help with this?
"start_state" should be in /apps/nautilus. Are you sure you clicked yourself into /apps/nautilus/desktop?

---

### Post by Go_Bucks on 2007-07-28
Sorry... I guess that was the point. There is no apps>nautilus>desktop. Just apps>nautilus. I also get a gconf error message if I try to go into themes on System>Preferences on the menu bar.

---

### Post by Go_Bucks on 2007-07-28
I should also state that I just reinstalled nautilus through synaptics and rebooted. That didn't change anything.

---

### Post by Go_Bucks on 2007-07-28
This wasn't the result of any system changes I've made, either. The icons have not been on the menu since I installed about a month ago. See screenshot below.

---

### Post by Go_Bucks on 2007-07-28
Actually, a preferences module popped up after the reinstall. See attached screenshot to see what I am talking about.

---

### Post by Go_Bucks on 2007-07-28
bump

---

