---
title: "Cannot find Gedit Folder / Latex"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2007-10-24
Hi,

I wish to install the LaTeX plugin for Gedit. I am using Gutsy. I have the plugin, it's extracted. According to the developers and various websites, I navigate to:

cd ~/.gnome2/gedit/

And drop the plugin in the plugins folder.

If there isn't a plugins folder then I need to create one.

My problem is that I don't even have a gedit folder.

I've tried through the terminal and nautilus and there is no gedit folder in .gnome2.

I have the application Gedit and it works fine.

Can someone tell me how to locate the gedit folder so I can drop the LaTeX plugin into it.

Thank you.

Tweed.

---

### Post by Rajca on 2007-10-24
```
/home/rc/.gnome2/gedit
```
I have that folder, so you should check it :D Did you checked that after using gedit?
Try to navigate using Nautilus, or anything else that you use.

---

### Post by Tweedicus on 2007-10-24
No I don't have it there.

---

### Post by yorkie on 2007-10-24
HI 
Go to places then HOME FOLDER click on VIEW  then click on SHOW HIDDEN FILES then scroll down to .gnome2 folder GEDIT FOLDER INSIDE

---

### Post by Tweedicus on 2007-10-24
As I mentioned in my first post, the problem isn't with .gnome2

I can navigate to the the hidden file .gnome2 no problem

I can open it up.

The problem is that there is no gedit folder inside .gnome2

So I need to know where is it

---

### Post by Hospadar on 2007-10-24
You might just not have one, try just making the gedit folder there and then making the plugins folder in it.

---

### Post by Maestro23 on 2007-10-24
Look in:

> usr/lib/gedit-2

---

### Post by gdw2 on 2008-03-19
Yes, when I tried to install it in the recommended .gnome2/gedit/plugin folder, it didn't work.  The above suggestion worked for me.

---

