---
title: "Why would my Ubuntu installation be missing all sorts of things from the menus?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Ice Dragon on 2007-07-16
I ran Ubuntu from the live CD without installing it and I noticed the menus had a lot of items in it that were useful and made things easier (like synaptics, restricted manager, etc..), but when i installed Ubuntu and logged in with my user name it didnt have those items in the menu.

I thought perhaps that it could have been because I was not logged in as root, but it wouldent let me log in as user root from the welcome screen.

Any ideas what happened? I did a standard installation, nothing special, and of course did all the updates that it popped up and told me were needed.

Are updates dangerous in Ubuntu?

---

### Post by Outrunner on 2007-07-16
> **Ice Dragon said:**
> Are updates dangerous in Ubuntu?

Yes, they will sprout horns and eat your flesh.

Did you check System -> Administration for Synaptic?

---

### Post by dptxp on 2007-07-16
Have you checked SYSTEM>ADMINISTRATION ?

Else go to SYSTEM>PREFERENCES>MAIN MENU and enable them.

And you are installing months after the release. You are bound to get updates. You are not
forced to update. You can even remove the icon

---

### Post by James.Dedon on 2007-07-16
And if it's not there, go to system>preferences>main menu to see if you can add it back onto the menu.:)

---

### Post by testube_babies on 2007-07-16
This is a strange problem; just about everything on the LiveCD menus should be installed by default.  You may end up trying a fresh reinstall and see if it was a one-time thing.

Perhaps items are installed but not showing up in the menus?  You can run alacarte to see your menu layout.

If, for some strange reason, the LiveCD failed to install all of the correct packages, you can do this to get the default Ubuntu setup:```
sudo apt-get install ubuntu-desktop
```

---

