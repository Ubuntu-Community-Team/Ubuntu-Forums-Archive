---
title: "GNOME look"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-03-04
Hi
I'm interested in exloring new gnome themes
Went to gnome-look.org and and downloaded a[ popular theme ]("http://www.gnome-look.org/content/show.php?content=19527")
The instruction are : > Since it's an engine, the installation differs from a 'normal' theme. Just run "./configure --prefix=/usr && make install" and you should be set.

Can anyone explain what does it mean?

---

### Post by codejunkie on 2006-03-04
[QUOTE=seshomaru samma]Hi
I'm interested in exloring new gnome themes
Went to gnome-look.org and and downloaded a[ popular theme ]("http://www.gnome-look.org/content/show.php?content=19527")
The instruction are : 
Can anyone explain what does it mean?[/QUOTE]
clearlooks is already installed in ubuntu so you shouldn't need to install that.

---

### Post by Pragmatist on 2006-03-04
It means you go into the directory that you downloaded and type just what they said.

---

### Post by andrewsawyer on 2006-03-04
You need to extract the file to a subdirectory in your home directory.  Then open up Terminal and go to the directory. If you were to extract it to a subdirectory called 'clearlooks' for example, you would open up Terminal from the Applications menu and type the following to get to the directory:
```
 cd ~/clearlooks
```

You would then type:
```
sudo ./configure --prefix=/usr && make install
```

And this would compile the program and install it.  Not, you would need the build-essential package from Synaptic to get this to work:

```
sudo apt-get install build-essential
```

You might need the kernel headers and kernel source too - you'll find these in Synaptic just by doing a quick search.

I hope this helps.  If you get any errors, please post them and it'll help us to locate the problem for you.

---

### Post by seshomaru samma on 2006-03-04
[QUOTE=codejunkie]clearlooks is already installed in ubuntu so you shouldn't need to install that.[/QUOTE]
Great - so how do I change Gnome themes then?

---

### Post by aysiu on 2006-03-04
I've never found the instructions on Gnome-look to be correct or simple.

Just download the .tar.bz2 to your desktop, go to System > Preferences > Themes.

A Theme Manager window will open. Drag 19527-clearlooks-0.6.2.tar.bz2 from your desktop to the Theme Manager window. You'll be asked if you want to install it, click **install**.

That's it.

Do not unzip the 19527-clearlooks-0.6.2.tar.bz2 file. Leave it as is.

**Edit**: As codejunkie said, though, Clearlooks is already in Ubuntu's default Gnome. You shouldn't have to install it... unless, of course, 0.6.2 is a newer version of Clearlooks.

---

### Post by seshomaru samma on 2006-03-04
Found it - preference >theme

---

### Post by aysiu on 2006-03-04
[QUOTE=seshomaru samma]Found it - preference >theme[/QUOTE] Yeah, just drag the file in there.

---

### Post by seshomaru samma on 2006-03-04
[QUOTE=aysiu]I've never found the instructions on Gnome-look to be correct or simple.

Just download the .tar.bz2 to your desktop, go to System > Preferences > Themes.

A Theme Manager window will open. Drag 19527-clearlooks-0.6.2.tar.bz2 from your desktop to the Theme Manager window. You'll be asked if you want to install it, click **install**.

That's it.

Do not unzip the 19527-clearlooks-0.6.2.tar.bz2 file. Leave it as is.

**Edit**: As codejunkie said, though, Clearlooks is already in Ubuntu's default Gnome. You shouldn't have to install it... unless, of course, 0.6.2 is a newer version of Clearlooks.[/QUOTE]
Thanks , but when I try to install it it asks me for a directory , yet every directory I give it ,it says the format is not supported . Where should I install it?

---

### Post by aysiu on 2006-03-04
I'm sorry. This is a freak theme.

Andrew Sawyer's right on this one.

You do need to compile this theme. Most themes you can just drag-and-drop.

I believe these two Clearlooks themes are not freak themes, though, and can be dragged and dropped:
[http://www.gnome-look.org/content/show.php?content=21377](http://www.gnome-look.org/content/show.php?content=21377)
[http://www.gnome-look.org/content/show.php?content=26624](http://www.gnome-look.org/content/show.php?content=26624)

Is there anything wrong with the Clearlooks that comes with Ubuntu?

---

