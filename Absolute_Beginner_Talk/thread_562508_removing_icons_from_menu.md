---
title: "removing icons from menu"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by graywizard on 2007-09-28
I down loaded a browser app to try - didn't like it and removed it completely in synaptic and I still have icons in the menu. restarted and even shutdown and started again - It is still there? how do I remove the icon?

---

### Post by kshane on 2007-09-28
> **graywizard said:**
> I down loaded a browser app to try - didn't like it and removed it completely in synaptic and I still have icons in the menu. restarted and even shutdown and started again - It is still there? how do I remove the icon?

Yep!  Goto System > Preferences > Main Menu and remove the "X" from in front of the app name.

Kevin

---

### Post by graywizard on 2007-09-28
KShane - thanks - that was easy. it has been so long that I looked in there I forgot.

I downloaded guarddog and that never showed up. Maybe that was also the reason is reverse.

---

### Post by kshane on 2007-09-28
> **graywizard said:**
> KShane - thanks - that was easy. it has been so long that I looked in there I forgot.

I downloaded guarddog and that never showed up. Maybe that was also the reason is reverse.

You are totally welcome...  Some apps don't show up in the menu and there is a way to add them, but I don't know how it's done.  :(

Glad I could help!

Kevin

---

### Post by Frijolie on 2007-10-12
I'm having the same problem. I've 'completely removed' a few applications using synaptic (which is supposed to uninstall the application along with it's configuration files) and yet they still appear in the menu(s).

I know of this trick:

> Goto System > Preferences > Main Menu and remove the "X" from in front of the app name.

However, isn't this just a band-aid? When you uninstall the application shouldn't it completely remove it from your system (including the entries in the menus, all associated application folders, configuration files, etc...)?

Also, when and if I choose to reinstall the program, it comes back with all the old configuration(s).

Is there a way you can remove the old menu entries?

---

### Post by forestpixie on 2007-10-12
if you've got a problem with an old config - have you checked in your home for a hidden folder - isn't that where they hide ?

---

### Post by OldTimeTech on 2007-10-12
Applications - accessories - terminal:
type in
sudo apt-get remove package
give password

should remove everything of the package

---

### Post by Frijolie on 2007-10-12
I've done this and still doesn't work:

> Applications - accessories - terminal:
type in
sudo apt-get remove package
give password

I've also looked for hidden folders in my home directory.

I even tried using

```
locate PackageName
```

in the terminal and then removing them that way. Hmm... is using Synaptic different from 'apt'? It was my understanding that Synaptic was just a GUI for 'apt', am I wrong?

---

### Post by CowzRule on 2007-10-12
Have a look in the /usr/share/applications folder.

---

### Post by Frijolie on 2007-10-14
in /usr/share/applications all I've got is a bunch of icons. I only see one folder and it's called "screensavers". Hmm...I've unchecked the applications in "System > Preferences> Main Menu"  and I guess that's working for now. Just wish when you removed an application (via Synaptic or Terminal) it completely removed them. I guess I'm just picky.

---

### Post by CowzRule on 2007-10-14
> **Frijolie said:**
> in /usr/share/applications all I've got is a bunch of icons.
Those icons are the "shortcuts" that you see in your menu.
> **Frijolie said:**
> I've unchecked the applications in "System > Preferences> Main Menu"  and I guess that's working for now.
You can also right click the item and select delete.
> **Frijolie said:**
> Just wish when you removed an application (via Synaptic or Terminal) it completely removed them. I guess I'm just picky.
Did you install the app with Synaptic? If you didn't, that's probably why it's not being completely removed.

---

### Post by Frijolie on 2007-10-14
No, I installed them via:

```

sudo aptitude install *applicationName*

```

Isn't synaptic just a GUI for the 'apt' command in the terminal? What benefit(s) does synaptic have over the command line? Sorry, I'm still considered a noob in GNU/Linux.

---

### Post by CowzRule on 2007-10-15
> **Frijolie said:**
> No, I installed them via:

```

sudo aptitude install *applicationName*

```

Isn't synaptic just a GUI for the 'apt' command in the terminal? What benefit(s) does synaptic have over the command line? Sorry, I'm still considered a noob in GNU/Linux.

I'm somewhat of a noob myself, been using Ubuntu for about the last year so I'm not sure if Synaptic is "just a gui for apt". I do know that there are 2 different terminal commands for installing software. There's "apt-get install" and "aptitude install". From all the research I've done I understand that apt-get and aptitude basically do the same thing but I believe they do it differently. What they do differently I don't know. I have read that aptitude does a better job of removing stuff than apt-get does. So I guess my suggestion is to use the same method to remove stuff as you did to install. In other words, if you "aptitude install something" then "aptitude remove something".
For more info on aptitude or apt-get, in the terminal just type "aptitude --help" or "apt-get --help".

---

