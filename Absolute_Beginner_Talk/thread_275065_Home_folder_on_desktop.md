---
title: "Home folder on desktop"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by skip910 on 2006-10-10
How do I get my home folder shortcut onto the Desktop?

I'm using GNOME.

Thanks!

---

### Post by jd65pl on 2006-10-10
Make sure you have a clear screen i.e. have the desktop showing...

navigate to PLACES>HOME

Click and drag the item you see as "Home" and drop it on your desktop.

You should now have a link on your desktop to "home"

---

### Post by Kateikyoushi on 2006-10-10
With terminal.

```
cd ~/Desktop
ln -s ~ home
```

---

### Post by skip910 on 2006-10-10
Haha, I'm not THAT much of a beginner.

I tried that, but the following error message comes up:
"You cannot move a folder into itself

The destination folder is inside the source folder"

---

### Post by skip910 on 2006-10-10
Yup, that worked, thanks!

---

### Post by jd65pl on 2006-10-10
Go with the command provided above... If your not that much of n00b then you should have tried it already!

---

### Post by andiii on 2006-10-10
You could do it in one line ;)

ln -s ~ ~/Desktop/home

---

### Post by Kateikyoushi on 2006-10-10
Actually what jd65p says also works, these drag and drop things surprise me, they are new to me.
You have to drag it from the top places menu, if try from nautilus won't work, seems draggin = moving in nautilus.

---

### Post by jd65pl on 2006-10-10
For clarification the tilda {~} refers to your home directory for your information.

---

### Post by blendmaster on 2006-10-10
It's like a battle of wits over the command line here!:-D

---

### Post by jd65pl on 2006-10-10
well > andiii  	You could do it in one line

ln -s ~ ~/Desktop/home

drops in a symbolic link with an arrow in the corner.(Some what untidy in my synical opion!)

As a GUI method has been provided by the programmers of the system so one may as well use the functionality made by them??

---

### Post by Anduu on 2006-10-10
Call me crazy but this all seems like a rather untidy/convoluted way of doing it.

Using gconf-editor go to apps>nautilus>desktop and check the "home folder visible" box.

you can also show other things on the desktop from there.

---

### Post by jd65pl on 2006-10-10
For a new user to ubuntu I feel that the drag/drop method is the most transparent and easy way to do it I have merely tried to explain the other solutions to the same issue. There may be other ways of doing the same way which other users find better/more comprehensive.

---

### Post by sgornick on 2007-10-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/48025](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/48025) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

jd65pl, I agree -- new users (even experienced users) would like to simply drag the icon to the desktop and be done with it.   This was addressed in Bug #48025, (which references the underlying issue -- "Can't drop the entries in "Actions" menu to the desktop" ). It currently sits with "confirmed" status, but with "low" importance.

Here's how to resolve your issue:

- Add Gnome Configuration Editor to your start menu (if you haven't yet):
   System -> Preferences -> Main Menu

  This will launch the program Alacarte.

  Then select
     Applications -> System Tools
     Then click on "Show" checkbox next to 
        Configuration Editor
   Close Alacarte.

   You will now have a "System Tools" menu option on your Main Menu.

- Run Gnome Configuration Editor
  System Tools -> Configuration Editor

  Set the home_icon to be visible:
    apps -> nautilus -> desktop
    Mark the checkbox next to home_icon_visible
  Close Gnome Configuration Editor

  You will now have an icon named "[username]'s Home" on your desktop

---

