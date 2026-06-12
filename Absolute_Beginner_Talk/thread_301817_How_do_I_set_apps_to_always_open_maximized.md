---
title: "How do I set apps to always open maximized"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-11-17
My guess is that I need some command line in the Launcher Properties' Advanced tab, where it says "Try this before using:" so that the app loads in a maximized window. But what, exactly, would "this" be? TIA

---

### Post by ricardisimo on 2006-11-18
I just pored over the manual... nothing. Any help appreciated.

---

### Post by aysiu on 2006-11-18
Use KDE?

---

### Post by ricardisimo on 2006-11-18
Not that I know.

---

### Post by underdog on 2006-11-18
Are you using standard Ubuntu, or Kubuntu or Xubuntu. Which does it display when the box is starting up?

---

### Post by adam.tropics on 2006-11-18
If they are closed from maximised, then gnome should re-open them maximised.

---

### Post by ricardisimo on 2006-11-18
> **adam.tropics said:**
> If they are closed from maximised, then gnome should re-open them maximised.

Not happening for all of them. I'm on Dapper, by the way.

---

### Post by localuser on 2006-11-18
> **ricardisimo said:**
> Not happening for all of them. I'm on Dapper, by the way.

In Gnome, When you close a window it should reopen to the same size.

This won't work if when you maximize the window you simply click on the "Maximize Window" button on the top right.  You have to drag the window to its full size.

---

### Post by adam.tropics on 2006-11-18
> **localuser said:**
> In Gnome, When you close a window it should reopen to the same size.

This won't work if when you maximize the window you simply click on the "Maximize Window" button on the top right.  You have to drag the window to its full size.

Sorry but it does for the apps I use. Except obviously small utilities that don't have a maximize button. (also except qt apps and gconf-editor, and that doesn't work the other way either)

---

### Post by adam.tropics on 2006-11-18
And if it's a real pain, you could look up a program like [Devil's Pie.]("http://www.burtonini.com/blog/computers/devilspie")

---

### Post by localuser on 2006-11-18
> **adam.tropics said:**
> Sorry but it does for the apps I use. Except obviously small utilities that don't have a maximize button. (also except qt apps and gconf-editor, and that doesn't work the other way either)

My bad.  I should have been more precise and said that this won't *always* work...

---

### Post by ricardisimo on 2006-11-18
> **localuser said:**
> My bad.  I should have been more precise and said that this won't *always* work...

Don't feel too bad. On at least one of my apps, FreeCiv, the window always opens small, no matter what size I set previously or how. I'm certain that there's another program that does this, but I can't remember which. There has to be some simple command line I can put somewhere in the Launcher Properties Options. Shouldn't there be?

---

### Post by adam.tropics on 2006-11-18
Yeah, I thought there might be a setting as with terminal geometry,

gnome-terminal --geometry 76x19

but apparently not, or at least I haven't found one yet.

---

### Post by ricardisimo on 2006-11-25
I just realized that I never answered one person's question: I'm on Ubuntu 6.06, although I might very shortly try out edgy. I'm assuming by the stunning silence that there is in fact no way to set apps to open maximized, other than to rely on Gnome. Can that be true? Anyone know of anything?

---

### Post by adam.tropics on 2006-11-25
[http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)

[http://wiki.foosel.net/linux/devilspie](http://wiki.foosel.net/linux/devilspie)

---

### Post by jerrykenny on 2006-11-25
You have to edit the config file for the particular application . . . 

Look in your home folder, then tell your file manager to "show hidden files"

All the applications you use have folders hidden here, and within that folder is a plain-text file called "config", open config with a text editor like gedit , and scroll down 'till you see a geometry specification . . . . change the figures here to your actual screen geometry eg 800x600, or 1024x768

afterthought . . . Maybe its a good idea to make a backup copy of the original config in case you need to go back to it . . ..

---

### Post by ricardisimo on 2006-11-25
No such line of text in any of the configuration files I opened. I tried a dozen or so, including apps I know I've resized. Nothing.

---

### Post by ricardisimo on 2007-03-21
So far as I have been able to tell, all of the regular image viewers (Eye of Gnome, G-Thumb Viewer, Gimp) refuse to re-open maximized. It's particularly odd when they don't even open to the "real" size of the image in question, when they're shrinking it down to this random window size.

Is there really no such option as "always open maximized" within Ubuntu (Gnome)? Can anyone recommend another image viewer. I was always very fond of IrfanView... is there a correlate in Linux? Thanks again.

---

### Post by DealerMan on 2007-03-31
In my search to figure this out as well, I found this which has cured my ills.  Open your app, right-click the titlebar, and select Advanced>Special Window Settings.  Click the Geometry tab>Size>select Remember.  Input your resolution setting ( for me it's 1024,768 ).  I'm running 6.10 Edgy, hopefully this will work for others as well.  Please post your success.

;)

---

### Post by ricardisimo on 2007-03-31
I'm thinking that this is a function of the particular app with which you did this. Nothing remotely resembling "Special Window Settings" appears. Try doing the same with Image Viewer ("Eye of Gnome") and see if it works.

I'm on Fesity, and I would think I'd be seeing *more* windows options, not less... but maybe they're still working stuff in slowly.

---

