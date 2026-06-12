---
title: "Remapping keys on keyboard"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Brendantb on 2007-03-27
Hi, 

I would like to swap the positions of the @ key and " key, as I am more used to their positions on the mac keyboard. Is there an easy way of doing this in the terminal?

---

### Post by Brendantb on 2007-03-27
... yes there is! 

Use: 

xmodmap -pke 

to see the key map, and use: 

xmodmap -e "keycode *** = amended list" 

where *** is the keycode in question. Couldn't be simpler...

---

### Post by Brendantb on 2007-03-29
Hi, 

I have since noticed that the changes made to the keyboard mappings aren't persistent, and revert whenever the computer is rebooted. 

Looking about on various forums, I saw a suggestion to add the lines to the .xinitrc file, in the home directory, creating one if necessary. Is this the correct way to go about this, or can I change the settings at a root level?

---

### Post by drs305 on 2007-03-29
I have some keys remapped and have added them to the startup tab of session manager (System, Preferences, Sessions, Startup Programs. Here is an example of what I have there:

xmodmap -e "keycode 112 = Tab"

The remap takes effect on boot.

---

### Post by Brendantb on 2007-03-29
Hi, 

Thanks for the quick response. 

I am using Xfce, so I don't have those menu paths. Is there some way to achieve the same end using terminal commands?

---

### Post by Brendantb on 2007-03-30
Hi, 

I have tried putting these xmodmap changes into the /etc/rc.local file, but they are not being executed with a restart. Is there something else that I should be doing?

---

### Post by Brendantb on 2007-03-30
Hi, 

I have resolved this at last. 

I put the xmodmap modifications in a file, .profile, in the home folder. Now the changes persist through a reboot. 

There are a variable number of spaces between the "keycode" term and the following number, and I have found that it is critical to have the same number of spaces in the remapping command. 

Thanks to all who made suggestions.

---

### Post by raequin on 2007-04-03
I wanted to change one of the "window" keys on my pint-size laptop keyboard to ctrl since it only has one ctrl button.  I found the keycode using xev and the name I wanted (Control_R) using "xmodmap -pke" and issued the command

xmodmap -e "keycode 116 = Control_R"

but this had no effect other than when I ran xev again I got "keycode 116 (keysym 0xffe4 Control_R); it didn't function as a ctrl key.  Then I found out that I also had to type the following command:

xmodmad -e 'add Control = Control_R'

I just thought this might help someone, or maybe someone would want to comment on this issue.

---

