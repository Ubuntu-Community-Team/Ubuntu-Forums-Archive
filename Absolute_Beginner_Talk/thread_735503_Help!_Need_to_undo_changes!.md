---
title: "Help! Need to undo changes!"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Horomancer on 2008-03-25
Yesterday i read and implemented the changes found in the thread  'Complete Streaming, Multimedia & Video How-to'
After going through the various terminal commands in section 1 and 2 i turned off my computer. Today i restarted it and was most unpleased.
1) I use to be able to view sites such as Youtube and newgrounds without any troubles. Now youtube says i'm missing the firefox flashplayer and newgrounds opens up another window where the flash looks really odd and unrefined
2) My volume control is set to my on-board sound card insted of my soundblaster card. I figured out how to change which device i'm controling though preferences
3) ALL my audio devices (mplayer vlc skype audacious) now try to go through my headset by defualt, when before they went through my speakers (which are hooked to my Soundblaster card)

I had things working pretty good before I followed the steps in that thread. How can i go back to that state without re-installing my Ubuntu?

---

### Post by LaRoza on 2008-03-25
> **Horomancer said:**
> Yesterday i read and implemented the changes found in the thread  'Complete Streaming, Multimedia & Video How-to'
After going through the various terminal commands in section 1 and 2 i turned off my computer. Today i restarted it and was most unpleased.
1) I use to be able to view sites such as Youtube and newgrounds without any troubles. Now youtube says i'm missing the firefox flashplayer and newgrounds opens up another window where the flash looks really odd and unrefined
2) My volume control is set to my on-board sound card insted of my soundblaster card. I figured out how to change which device i'm controling though preferences
3) ALL my audio devices (mplayer vlc skype audacious) now try to go through my headset by defualt, when before they went through my speakers (which are hooked to my Soundblaster card)

I had things working pretty good before I followed the steps in that thread. How can i go back to that state without re-installing my Ubuntu?

A link to the thread you followed would help.

You can quicky change sound devices with asoundconf-gtk (search in synaptic)

For the Flash issue, I can't tell what you did, so please link to the thread.

---

### Post by Horomancer on 2008-03-25
[http://ubuntuforums.org/showthread.php?t=661833&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=661833&highlight=mplayer)

here is the thread i was following along with.

---

### Post by jan quark on 2008-03-25
concerning the flash issue try to remove it and to reinstall it again

```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

### Post by Horomancer on 2008-03-25
The command line you gave me has corrected the flash player and it works fine now. I dled the asoundconf-gtk through Synaptic but do not know where to find it so i can use it.
Thank you very very much.

---

### Post by LaRoza on 2008-03-25
> **Horomancer said:**
> The command line you gave me has corrected the flash player and it works fine now. I dled the asoundconf-gtk through Synaptic but do not know where to find it so i can use it.
Thank you very very much.

Press Alt + F2 and type "asoundconf-gtk".

You can make a launcher for it, if you find it useful.

---

### Post by Horomancer on 2008-03-25
Yay! the asoundconf-gtk worked great and sound is coming from all the right holes.
Thank you very much for your quick response and support.

---

