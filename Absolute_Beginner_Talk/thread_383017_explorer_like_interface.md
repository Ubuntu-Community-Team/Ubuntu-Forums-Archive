---
title: "explorer like interface"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by gjmoyer on 2007-03-12
I am used to windows explorer.  Creating folders, dragging dropping files from folder to folder, right clicking 100 pictures, and resizing them, moving the resized pics to other folder.

I love Linux, but how do I do these routine tasks in Linux?  I have GNOME commander which seems kinda useless to me.  I also have Nautilus which does not seem to have this ease of use as windows explorer.  I know that it is probably more of a learning curve for me then the fact that Linux is harder to use.

Where is right click in folder, to create a new folder?  Where is select several photos, right click and resize to another name like mypic101.jpg to mypic101 (medium).jpg?

Thank you!

---

### Post by Dr. Nick on 2007-03-12
In nautilus just right click and hit "create folder"

I have never seen the pic resize feature in XP, or are you on vista?

I know their are some batch resize programs if you look around, not sure if they integrate into nautilus though

---

### Post by russell.h on 2007-03-12
I'm interested in the photo resize thing too, I always had to go into paint which had some sort of crappy scaling algorithm, or wait for GIMP to load (which took like 5 minutes because I installed some huge font pack and it had to load them all).

---

### Post by Dr. Nick on 2007-03-12
look for the package nautilus-image-converter in synaptic, It looks to do what you want.

I installed it and it doesnt show up, may need a restart or something though

---

### Post by Marsolin on 2007-03-12
I'm not sure about Ubuntu, but Kubuntu does all of those things by default in Konqueror. You could probably install [Konqueror]("http://linuxappfinder.com/package/konqueror") and [Kim]("http://linuxappfinder.com/package/konq-kim") in Ubuntu and use if from within Gnome as well.

---

### Post by Dr. Nick on 2007-03-13
the nautilus-image-converter i mentioned above appeared on restart, 

It allows you to resize and rotate pictures via the right click menu.

It is easy to install from synaptic

---

### Post by gjmoyer on 2007-03-18
That nautilus image converter sounds like what I am looking for.  I can't see to install it though.


sudo apt-get install nautilus-image-converter

E: coudn't find package....

I will try downloading and installing manually from the site.

---

### Post by Inevitable Glitch on 2007-03-18
> **Dr. Nick said:**
> In nautilus just right click and hit "create folder"

I have never seen the pic resize feature in XP, or are you on vista?

I know their are some batch resize programs if you look around, not sure if they integrate into nautilus though

That is an extremely useful feature in WinXP, but it's not in WinXP by default, it's a powertoy that is available free from Microsoft.  It is one of many things I always install right off on a fresh install, so it's as good as built in as far as I'm concerned.

---

### Post by 454redhawk on 2007-03-18
> **gjmoyer said:**
> I am used to windows explorer.  Creating folders, dragging dropping files from folder to folder, right clicking 100 pictures, and resizing them, moving the resized pics to other folder.

I love Linux, but how do I do these routine tasks in Linux?  I have GNOME commander which seems kinda useless to me.  I also have Nautilus which does not seem to have this ease of use as windows explorer.  I know that it is probably more of a learning curve for me then the fact that Linux is harder to use.

Where is right click in folder, to create a new folder?  Where is select several photos, right click and resize to another name like mypic101.jpg to mypic101 (medium).jpg?

Thank you!

You sound like you might be a KDE kinda guy.
KDE is much more powerful and has a better ability to be customized and does the things you mentioned all by itself.
May I suggest Mepis or Kubuntu. IMO Gnome is kind of a newbie type interface.

---

### Post by Dr. Nick on 2007-03-18
> **gjmoyer said:**
> That nautilus image converter sounds like what I am looking for.  I can't see to install it though.


sudo apt-get install nautilus-image-converter

E: coudn't find package....

I will try downloading and installing manually from the site.
Oops, sorry. Its only available in the feisty universe repo, I upgraded my edgy and assumed it was in the edgy repo aswell, apparently not.

Hope the manual install works

---

### Post by DarkN00b on 2007-03-18
This is a little off topic, but there are a couple of other Nautilus related scripts I noticed when looking around in Synaptic.

1.     nautilus-script-audio-convert  - audio convert is a script that converts between WAV, Ogg, MP3, MPC, FLAC, APE, AAC, and WMA files. _This script is great for batch converting audio files._

2.     nautilus-open-terminal - Right-click a folder and select Open in Terminal. I have been looking for something like this for a while.

One thing about nautilus-script-audio-convert though --- you need to type

```
nautilus-script-manager enable ConvertAudioFile
```

into a terminal window and then restart Nautilus to get it in the right-click context menu.

---

### Post by Psed on 2007-03-23
> **Marsolin said:**
> I'm not sure about Ubuntu, but Kubuntu does all of those things by default in Konqueror. You could probably install [Konqueror]("http://linuxappfinder.com/package/konqueror") and [Kim]("http://linuxappfinder.com/package/konq-kim") in Ubuntu and use if from within Gnome as well.

Chad,

Very interesting reply. I installed Konqueror, but am not able to get a desktop Icon placed on my desktop so I may more readily use it.

Could you lead me through how I may place a desktop icon for Konqueror, please?

Psed

---

### Post by Marsolin on 2007-03-23
> **Psed said:**
> Chad,

Very interesting reply. I installed Konqueror, but am not able to get a desktop Icon placed on my desktop so I may more readily use it.

Could you lead me through how I may place a desktop icon for Konqueror, please?

Psed

I use KDE so I'm not sure of the exact steps in GNOME. In KDE I can right-click on the desktop and select Create New | Link to Application, then select Konqueror from the list.  GNOME might have something similar.

Does a menu item appear for Konqueror? If it does you could try right-clicking on it to see if you can Copy it or try to drag it to your destop to create a copy that way. In KDE right-clicking the menu icon gives an Add Item to Desktop option.

---

