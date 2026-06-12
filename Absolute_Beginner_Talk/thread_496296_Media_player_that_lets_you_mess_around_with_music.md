---
title: "Media player that lets you mess around with music?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Feba on 2007-07-09
I remember in Windows I had Winamp plugins that would allow me to play songs backwards, change the pitch, or speed songs up or slow them down. Are there any media players like this for Linux? I tried audacity, but it gave me troubles with finding a sound device, I assume because I use onboard sound, but it's just not compact enough to do things on the fly (say, move a slider two notches to change the pitch) , so I'd really like if I could find a media player that would do the same.

---

### Post by dragonwings on 2007-07-09
in ubuntu 7.04 fiesty 

go to appliations(top left of desktop)

then add and remove

on the right drop box choose all avalible applications

in search box type audacity

now tick the audacity  box

click apply

job done 

note: after install you will be informed where shortcut icon is placed .

other programs  to search for    :sweep
                                                      
                                                         :terminatorx

---

### Post by Tomosaur on 2007-07-09
He said he's tried Audacity and it doesn't do what he wants effectively.

Anyway, use the following command to install Audacious and the necessary plugins:

```

sudo apt-get install audacious audacious-plugins audacious-plugins-extra

```

Once it's installed, open Audacious (you'll notice that it's essentially a clone of Winamp), click the menu button in the top left of the Audacious window, then Preferences, then go to the Plugins tab, and enable the LADSPA plugins, which are in the 'Effects' section. On the same screen, click the 'Configure' button, and then add whichever effects you wish to use. A box will pop up for each individual effect, and you can manipulate each until you get the sound you want :)

---

### Post by Feba on 2007-07-09
> He said he's tried Audacity and it doesn't do what he wants effectively.

Thanks for reading :D Doesn't seem like many people do that anymore.

I'll try the rest of that too- I was kinda hoping that I could find XMMS plugins that would do something similar, but hey, if it works it works :3 thanks

---

