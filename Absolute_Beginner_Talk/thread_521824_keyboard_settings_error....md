---
title: "keyboard settings error..."
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jeremy1138 on 2007-08-09
Every time I start up Ubuntu I get an error that says 'The X system keyboard settings differ from your current GNOME keyboard settings.  Expected was model "pc101", layout "us" and no options, but the the following settings were found: model "pc105", layout "us" and no options.  Which set would you like to use?'.  I think I'm getting this because I was recently messing around with my laptop trying to get my ATI card working and I couldn't get gnome to start up so I used sudo dpkg-reconfigure xserver-xorg to reset things...  What can I do to fix my computer so I don't get this error?  Thanks in advance for any help you can give!

---

### Post by meierfra on 2007-08-09
Go to

System -> Preferences-> Keyboard 

and click on the Layout tab.   I  think it will say "pc 101 us".  Change it to "pc 105 us" ( it might be the other way around)

---

### Post by Leed on 2007-10-03
I have the same problem, unfortunatly meierfra's suggestion has no effect, neither does dpkg-reconfigure xserver-xorg. 

I'm pretty sure this happens because I recently tried using xserver-xgl, that only messed up my keyboard settings and gave no benefit. It seems to have muddled up some setting that I cant find.

Solved:
uncheck "separate layout for each window" in the Gnome Keyboard settings

---

### Post by NoVista on 2007-10-07
After installing and un-installing xgl-server, I had same prob.
But uncheck "separate layout for each window" in the Gnome Keyboard settings didn't work by itself. I then also had to click the reset to defaults field.

---

