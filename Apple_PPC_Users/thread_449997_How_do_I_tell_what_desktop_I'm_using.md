---
title: "How do I tell what desktop I'm using?"
date: 2007-05-20
forum: Apple PPC Users
---

### Post by joshjani on 2007-05-20
OK, so now I've got Ubuntu running on my Old World Beige G3, I want to use the xfce desktop environment. I love the gnome that comes with Ubuntu, but I've read that xubuntu would run a little more snappily on underpowered machines.

So I used synaptic to search for xubuntu, then installed what I found. I restarted, but the only difference in the desktop that I can tell is the login screen.

So how do I know what environment I'm in, and if I haven't yet actually installed the xfce desktop, how do I do it?

Thanks

JC

---

### Post by tgoose on 2007-05-20
On the login screen there should be a button that says "Options" or "Settings" or something similar, with a menu to "Select session..." and on that there should be an option between terminal, GNOME and XFCE. I'm sorry I can't be more specific from that because the login screen can look different (and so have menus with different labels) when XFCE is installed, and I use GNOME.

---

### Post by stmiller on 2007-05-20
sudo apt-get install xubuntu-desktop

---

### Post by joshjani on 2007-05-21
> **tgoose said:**
> On the login screen there should be a button that says "Options" or "Settings" or something similar, with a menu to "Select session..." and on that there should be an option between terminal, GNOME and XFCE. I'm sorry I can't be more specific from that because the login screen can look different (and so have menus with different labels) when XFCE is installed, and I use GNOME.

Thanks- that's what I needed- I can try out different looks/feels for the desktop

---

### Post by joshjani on 2007-05-21
> **stmiller said:**
> sudo apt-get install xubuntu-desktop

I'm sorry if it's a noob question, but does that command differ from finding and installing it through synaptic package manager? 

I ask because I thought I did indeed change to xubuntu by installing throuogh synaptic, but it didn't change anything- I have to choose at the login screen options.

---

### Post by 3rdalbum on 2007-05-21
No, the command doesn't differ from installing it through Synaptic.

As ubuntu-desktop and Gnome are still installed, they are still given as options at the login screen. If you really want to be rid of them, you could find and delete all the Gnome stuff, but if you don't need the space you might as well keep them on there in case you don't like XFCE.

---

### Post by tgoose on 2007-05-21
If you choose a different session from the default, it should give you the option to set that as the default one (I think)

---

