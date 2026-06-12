---
title: "In Edgy, how do I change the colour of the panel font?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by n00b@linux on 2006-10-28
I'm in the process of tailoring my Edgy Eft Gnome desktop.
I've got a dark brown background and made the panel transparent.
However, as the 'Applications', 'Places' and 'System' menus are in black font, it's quite difficult to see.
I wanted to change their font colour from black to white.
Can I do this?

---

### Post by Brownedwg89 on 2006-10-28
you could make the panel semi-transparent... it might make it easier to see

---

### Post by n00b@linux on 2006-10-28
Thanks, but I've already done that.  It's the dark background in combination with the black font of the panel that's the problem.  Transparency actually makes the matter worse.

---

### Post by adam.tropics on 2006-10-29
create or open and edit the file ~/.gtkrc-2.0

and in it paste...

```
style "my_color"
{
fg[NORMAL] = "#F3B04F"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
```

You can pick whatever colour yourself obviously. Have fun!

---

### Post by n00b@linux on 2006-10-29
Thanks adam.tropics, but I had already tried that (you probably remember me asking a similar question when I was running Dapper a few months ago).  However, for Edgy, for some reason it doesn't seem to work :(

---

### Post by adam.tropics on 2006-10-29
Sorry it isn't working for you, but it works fine on Edgy here.

---

### Post by notarikon on 2006-10-29
Add the above theme code to a file called panel-fontrc and place it in the .gnome2 folder of your user home directory, e.g.

/home/yourusername/.gnome2/panel-fontrc

Then add this line at the top of your gtkrc file under the include "icons/iconsrc" line (or at the top if you don't have this line)

```
include "/home/yourusername/.gnome2/panel-fontrc"
```

That should get it working

---

### Post by chavo on 2006-10-29
You can try this new app, [http://www.gnome-look.org/content/show.php?content=47349](http://www.gnome-look.org/content/show.php?content=47349).
It lets you change quite a few gnome colors without having to write a whole new them, or your own gtkrc file. Something that's been severely lacking in Gnome since it's inception and one reason I no longer use it.

---

### Post by n00b@linux on 2006-10-29
Well, I don't know what is going on.
I tried notarikon's suggestion.  It didn't work.
I tried adam.tropics' suggestion again.  It didn't work, either.
I tried chavo's suggestion.  Unfortunately, that app requires versions of:

libgtkmm
libglademm
libxml2

that Edgy doesn't have and they're not in the repositories.

So I was at a dead end.  I started to fiddle around with .gtkrc-2.0 and nothing seemed to happen.  Then - for some reason I know not of - when I used 'killall gnome-panel' for about umpteenth time the font colour changed!  WTF?  I don't know why it didn't work the first few attempts, but I'm happy now because I've got white fonts on a completely transparent panel background with a very dark desktop background- just what I wanted!

Thank you all for your helpful suggestions.

---

### Post by adam.tropics on 2006-10-29
I can't see the install method causing this, and either of the above methods should work. 

The only thing I can think is either you have not got the filename quite right, as in it's not '.gtkrc-2.0', or you have  not replaced your user name, perhaps you have not restarted the panel, or finally, as is easy to do, maybe you have 'oversudo illness' and have thereby messed the permissions to .gtkrc-2.0......(ie, you do not need sudo for any of this)?

---

### Post by n00b@linux on 2006-10-29
> **adam.tropics said:**
> I can't see the install method causing this, and either of the above methods should work. 

The only thing I can think is either you have not got the filename quite right, as in it's not '.gtkrc-2.0', or you have  not replaced your user name, perhaps you have not restarted the panel, or finally, as is easy to do, maybe you have 'oversudo illness' and have thereby messed the permissions to .gtkrc-2.0......(ie, you do not need sudo for any of this)?
Thanks adam.tropics, but your post (quoted above) was posted while I was editing my previous post.  It's working now.  Thanks, once again for your help.  Btw, I skipped the /home/n00b/.gnome2/panel-fontrc step and instead, put the coding directly into my .gtkrc-2.0 file.

---

### Post by n00b@linux on 2006-10-29
I've attached a screenie of the finished product for those interested. ;)

---

### Post by daniel6 on 2008-03-14
Now, that's a nice piece of work!

Daniel

---

