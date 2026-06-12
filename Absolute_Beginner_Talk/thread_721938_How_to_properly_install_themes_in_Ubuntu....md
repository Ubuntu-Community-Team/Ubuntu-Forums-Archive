---
title: "How to properly install themes in Ubuntu..."
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Avsfan60 on 2008-03-11
Hey guys, I'm very new Ubuntu and the whole Linux thing. Im just learning so please bear with me..

I recently tried to install this theme.

[http://www.ubuntu-unleashed.com/2008/02/howto-install-new-slickness-theme-in.html](http://www.ubuntu-unleashed.com/2008/02/howto-install-new-slickness-theme-in.html)

and i followed the instructions on the site, but now i cannot see the close, maximize, or minimize icons... 

Im trying to install a new theme:

[http://www.gnome-look.org/content/show.php/Death+Note?content=76034](http://www.gnome-look.org/content/show.php/Death+Note?content=76034)

and I go to System > Pref > Appearance and i click install and i clicked on the file without extracting it which is what your supposed to do right? It says it installs but it isnt listed in the theme choices.

I try to go back to the original theme and it does the windows but yet i still cannot see the icons....

what am i doing wrong and how can i fix this? 

thanks in advance

---

### Post by dmsynck on 2008-03-11
You might try extracting the theme gzip file (either with command line or Archive Manager) into your ~/.themes folder and then see if it shows up in the themes control panel

---

### Post by Avsfan60 on 2008-03-11
Ok, this is a stupid question i know, But where is the Theme folder?

---

### Post by Oldsoldier2003 on 2008-03-11
> **Avsfan60 said:**
> Ok, this is a stupid question i know, But where is the Theme folder?

its inside your home folder

---

### Post by spiderbatdad on 2008-03-11
At least one of those is a GDM theme. That the theme you would see at login. To install that go Administration>>Login Window>>Local and drag and drop the tar.gz in the window where you see other themes. Then select it by clicking the little bubble. Note don't have more than one selected. And check the window to make sure you aren't set for Random theme selection. It should say Theme: "selected only"

---

### Post by Avsfan60 on 2008-03-11
I open my home folder and it only has Desktop, Documents, Examples, Incomplete, Music, Pictures, Public, Templates, and Videos. I checked every folder and there is no theme folder

---

### Post by Oldsoldier2003 on 2008-03-11
> **Avsfan60 said:**
> I open my home folder and it only has Desktop, Documents, Examples, Incomplete, Music, Pictures, Public, Templates, and Videos. I checked every folder and there is no theme folder

its ./themes (a hidden folder) you can see it by pressing CTRL +H in nautilus

---

### Post by Therion on 2008-03-11
Easy way to install Slickness:

Download the theme to your desktop.
You'll have 71933.SlicknesS.tar.gz on your desktop. Don't touch it.
Go to System/Preferences/Appearance
The Preferences Manager will open.  
Resize the window so you can see the Slickness.tar.gz on your desktop.
Drag and Drop the Slickness.tar.gz file ONTO the Preferences Manager window.
(You'll get a message that the theme was installed.)
Scroll down in the Preference Manager window until you see the theme "SlicknesS" and click on it to apply it.  
That should be all there is to it.  
Just did it and it works just fine for me.

---

### Post by spiderbatdad on 2008-03-11
> **Therion said:**
> Easy way to install Slickness:

Download the theme to your desktop.
You'll have 71933.SlicknesS.tar.gz on your desktop. Don't touch it.
Go to System/Preferences/Appearance
The Preferences Manager will open.  
Resize the window so you can see the Slickness.tar.gz on your desktop.
Drag and Drop the Slickness.tar.gz file ONTO the Preferences Manager window.
(You'll get a message that the theme was installed.)
Scroll down in the Preference Manager window until you see the theme "SlicknesS" and click on it to apply it.  
That should be all there is to it.  
Just did it and it works just fine for me.

Exactly! and for the GDM theme you drop it in the window at System>>Administration>>Login Window>>Local

---

### Post by Avsfan60 on 2008-03-11
Ok, now i can get the themes installed, i know how to do that now. But I dont know how to get my close, maximize and minimize icons back and its real frustrating to right click and do these commands.. any idea on how to get these back?

---

### Post by Avsfan60 on 2008-03-11
here is a screenshot showing there is no close icons..

[IMG]http://i27.tinypic.com/j5jf9g.png[/IMG]

---

### Post by spiderbatdad on 2008-03-11
Thats a problem with that particular theme it looks like. Probably missing something in in the chrome.css or whatever thingy. Of course the options should be under the file tab.

---

### Post by Avsfan60 on 2008-03-11
its with all the themes that is listed in the Appearance manager every single one of the themes has no icons....

---

### Post by Therion on 2008-03-11
Ahhh the old disappearing buttons... Hate it when that happens.  

See [this thread](http://ubuntuforums.org/showthread.php?t=422676) for help with that.

---

### Post by Avsfan60 on 2008-03-12
> **Therion said:**
> Ahhh the old disappearing buttons... Hate it when that happens.  

See [this thread](http://ubuntuforums.org/showthread.php?t=422676) for help with that.


thanks a bunch! that solved it!!

---

