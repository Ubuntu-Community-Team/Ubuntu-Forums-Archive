---
title: "Top Panel Missing"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Thanatos10 on 2007-06-07
Well, while expermenting with twinview (which still doesn't work), I've lost my top panel.  And now I logon is different also.  It's KDE I believe, a lovely blue screen with a few more options.  Not to sure what I've done, but how do I undo it?  I really would like to get my top panel back since I'm really a rookie and kind of lost without it.  Oh, I'm using the 64bit version if that matters at all.

Thanks in advance for any suggestions and your time.

---

### Post by pbw on 2007-06-07
right click the existing panel and select the option to add another. also, you can choose whether to login to either gnome or kde at the login prompt. Look under sessions.

---

### Post by Thanatos10 on 2007-06-07
OK, I added a new top panel, but it's blank.  How do I put the drop down menu items back?

Thanks

---

### Post by NeoLithium on 2007-06-07
Right click on the empty panel, and select the Add to Panel option.  It'll bring up a selection of things you can add. The menus are near the bottom of the collection :)

---

### Post by Nythain on 2007-06-07
you are probably actually thinking of something along the lines of this
in terminal type
```

kcontrol

```
then navigate down to Desktop------>Behavior
in the middle of the right side should be a section called
"Menu Bar at Top of Screen"
select the one your want... click apply and voilla, thats probably the panel you were wanting...

if not, then the panels they have already mentioned should suffice for anything else you want to do

---

### Post by pbw on 2007-06-07
Actually, i think he's referring to the gnome menus.

There's a tweaked kde menu made to look like gnome. (have to compile it and am too lazy to explain how to do that, since we're still on just getting a panel to appear lol)

In terminal enter
wget 
[http://pbw.fdns.net/debs/31031-kmenu-gnome_0.6.4-1_all.deb](http://pbw.fdns.net/debs/31031-kmenu-gnome_0.6.4-1_all.deb)

sudo dpkg -i 31031-kmenu-gnome_0.6.4-1_all.deb

Then right click the panel, select add applet, and choose kdesktop menu.

---

