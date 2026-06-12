---
title: "Searching for google earth"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Joseph5000 on 2008-02-23
Hi there. I installed Google Earth from the Synaptic, but can't find it anywhere. Synaptic shows it as installed. Thanks

---

### Post by Crafty Kisses on 2008-02-23
> **Joseph5000 said:**
> Hi there. I installed Google Earth from the Synaptic, but can't find it anywhere. Synaptic shows it as installed. Thanks

Go into Terminal and type the following:
```
googleearth
```
Try that.

---

### Post by Joseph5000 on 2008-02-23
says:command not found

---

### Post by dcstar on 2008-02-24
If you want the latest version from Google Earth, look at this:

[http://ubuntuforums.org/showthread.php?p=3695951#post3695951](http://ubuntuforums.org/showthread.php?p=3695951#post3695951)

---

### Post by Joseph5000 on 2008-02-26
I installed Google Earth from the Synaptic, but I can't find it anywhere. Does anyone know where to look? Thanks

---

### Post by kesman on 2008-02-26
type google in terminal and press TAB-key to autocomplete the command for you. After that, you can create a launcher in the menu with that command if you like. Also check add/remove programs in applications if google earth is marked as installed in there too.

---

### Post by Sceiron on 2008-02-26
You are standing on it :P

Eh, it should be here:
Applications -> Internet -> Google Earth.

---

### Post by angry_johnnie on 2008-02-26
if you can't see it in your menu, try this:

open a terminal and then type

sudo apt-get install menu && sudo update-menus


if you still can't see it, then you're gonna have to add it yourself.  Right click on the menu and choose edit menus.  Go to Internet and click on add launcher.  
The name would be Google Earth
The command would be googleearth (or /usr/bin/googleearth     either way works fine)
and the icon (think)  would be in /usr/share/pixmaps/

---

### Post by Joseph5000 on 2008-02-26
I tried the google + TAB thing and nothing, and it is not in the Application >Internet part either. I couldn't see it in Add/ Remove either. I tried to re-install which it reported as successful, but still, I can't find it.

---

### Post by Sceiron on 2008-02-26
> **Joseph5000 said:**
> I tried the google + TAB thing and nothing, and it is not in the Application >Internet part either. I couldn't see it in Add/ Remove either. I tried to re-install which it reported as successful, but still, I can't find it.

I guess you have searched some arond, but have u seen this:

[https://help.ubuntu.com/community/GoogleEarth#installation](https://help.ubuntu.com/community/GoogleEarth#installation)

---

### Post by Joseph5000 on 2008-02-26
Hey Sceiron
Thanks a lot, that worked well. Cheers Joseph

---

### Post by Sceiron on 2008-02-26
Feel free to mark the thread as solved,
maybe it will help some other dude

---

### Post by gary0 on 2008-02-26
Hi,
you need to install the medibuntu repos to be able to install google earth from synaptic.

Enter these liness in a terminal:

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

and then the key:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Then search in synaptic again.

Hope this helps.
Gary

---

