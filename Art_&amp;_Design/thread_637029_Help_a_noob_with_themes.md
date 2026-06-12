---
title: "Help a noob with themes"
date: 2007-12-10
forum: Art &amp; Design
---

### Post by Valok on 2007-12-10
So I am new to the linux world, and I'm coming up with more and more questions the deeper I delve into it (which isn't very far at the moment).

Right now I really want to customize my desktop, and there are a few themes that I really thought were cool looking on gnome-look.com

I've gotten as far as to downloading them to my desktop and unzipping them there, but as to where to go from there on out, I'm lost.

I also have a few questions on the terms being used and what parts of the desktop they refer to, and which ones are usable to me (I run 7.04 Ubuntu atm)

Metacity
GDM Themes
Splash screens
Desklets
XMMS Themes

Thanks in advance for helping out a newb in this community :lolflag:

---

### Post by Vadi on 2007-12-10
Best idea on understanding what the theme is for is to look at the screenshots :)

Metacity is a window manager. This means it's reponsible for the top bar of the window - the bar with the name of the window, and the buttons on it (usually minimize, maximize, and close - but there are more). To install a metacity theme, you go to System - Prefences - Appearance, click on the Install button, and point it to the theme file.

GDM themes are the themes that you see when you first start your computer, and need to login. The process is similar - except you use System - Administration - Login window - Local to install one.

Splash screens: there are several you can have. First is the GRUB splash screen - you'll see this one when you first start your computer, and it tells you what OS do you want to boot. By default, there is none. To install one, I recommend that you use StartUp Manager to set one ([click here to get it]("apt:startupmanager"), or find it in add/remove, or copy/paste "sudo apt-get install startupmanager" in the terminal).

Next is the Usplash screen. By default, it's that little orange loading bar with a black background. I forget how to remember to install those... but try looking on the net or in help.ubuntu.com/community, you'll find the instructions.

And the last is a little box that shows up after the computer booted, and you logged in. It'll say stuff like nautilus is loading and such.

Desklets are small apps you can have on your desktop. I don't know much about them, I don't use them - I use Screenlets ([click]("http://www.screenlets.org/index.php/Home")) instead.

XMMS I think is a music player that you can get skins for.

So that's about it, I think. If you'll have any questions, feel free to ask!

---

### Post by Valok on 2007-12-10
Thanks!  You've helped clear up a lot of my confusion.  

On question I still have though is the following:

> To install a metacity theme, you go to System - Prefences - Appearance, click on the Install button, and point it to the theme file.

Not so much a question as to this specific installation (metacity) but more so a clarification of the process in general.  When I DL the theme that I want, is there a specific place I need to save it to?  Or format it should be in?  Because I tried to do this this morning, and I DLed a file, extracted it to my desktop and then pointed my computer to that file.  But when I clicked open it just brought me to the subfolders inside of it.

Im thinking I didn't save it under the right format, but I'm just not sure.

---

### Post by Vadi on 2007-12-10
Ahh. You don't need to extract the file - just point the thing to the archived file, it'll extract and set up everything on it's own :). After that, I think you're free to delete the archive, because it'll copy the data over in appropriate places.

---

### Post by Valok on 2007-12-10
Sounds easy enough, once I get home and back on a real computer (;) ) Ill give it a shot and hopefully all will go well.

---

### Post by Valok on 2007-12-11
Bumping this because I have another question now.

When I go into System>Preferences, I don't have any option called appearance that you referred me to. 

Is there something that I have to download first?

---

### Post by Vadi on 2007-12-11
Hrm, unless you removed it, it should be there - it's installed by default. The thing is called "gnome-appearance-properties", but I'm not sure what package exactly installs it...

Try installing **ubuntu-desktop**, maybe that'll have it. So click here ([click]("apt:ubuntu-desktop")) or "sudo apt-get install ubuntu-desktop".

---

### Post by Valok on 2007-12-11
Cool thanks.  When I get home in a couple hours I'll give that a shot and report back.

---

### Post by smartboyathome on 2007-12-11
Are you using Ubuntu, Kubuntu, or Xubuntu? Also, what version? Ubuntu Gutsy is the only one that comes with the appearance menu.

---

### Post by Valok on 2007-12-11
I'm using Ubuntu 7.04 at the moment.  And when I went to DL the ubuntu-desktop it just told me that I already have it, and I still dont have the appearance menu.

---

### Post by Vadi on 2007-12-11
Try typing

gnome-appearance-properties

in the terminal. What does it say?

---

### Post by Valok on 2007-12-11
It returns "Command not found"

---

### Post by smartboyathome on 2007-12-11
> **Valok said:**
> I'm using Ubuntu 7.04 at the moment.  And when I went to DL the ubuntu-desktop it just told me that I already have it, and I still dont have the appearance menu.

That isn't available on Ubuntu 7.04, that is why you can't find it. You have to use System > Preferences > Themes.

---

### Post by Valok on 2007-12-11
Aha!  Got the metacity up and running now, but how do I go about getting the splash screen for GRUB.  I tried installing the file I was directed to earlier, but couldn't find it anywhere.

---

### Post by smartboyathome on 2007-12-11
It is also only available for Gutsy. You have to download it from [here]("http://sourceforge.net/project/downloading.php?groupname=startup-manager&filename=startupmanager_1.9.9-1_all.deb").

---

### Post by Valok on 2007-12-11
ahh, Ill have to wait till I upgrade then.  Thanks for the info

---

### Post by smartboyathome on 2007-12-11
Even if you upgrade, I still suggest using that link I gave you. It is newer than the one in the repo and better imo.

---

