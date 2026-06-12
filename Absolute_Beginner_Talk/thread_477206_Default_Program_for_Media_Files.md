---
title: "Default Program for Media Files?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-06-18
How can I set this up to where it removes Totem as the default player, and adds vlc?
(also; when I removed totem, the totem player is still assessable, is there something I'm missing?)

---

### Post by Chilli Bob on 2007-06-18
You can't remove Totem (or firefox). I'm too new to understand why exactly, but it is required for Ubuntu to work properly.  I know how you feel though, I wanted to remove Totem to replace it with Mplayer, but Totem still auto-starts whenever I put in a DVD.  I can't work out how to set it up so that Mplayer autostarts instead.

---

### Post by RomeReactor on 2007-06-18
Hi. To make totem the default for a specific file format, try right-clicking on that file and select "Properties"; on the "Open With" tab, make sure VLC is there and the radio button is set to it. If it's not, click "Add", choose ti from the selection and, again, make sure the radio button is set to VLC. This way any file with that format (mpg, avi, etc.) will open in VLC whenever you double click on them. The downside with this approach is that you *must* do this for every file format you wish to open with VLC.

To set Mplayer to open DVD's, go to "System-->Preferences-->Removable Drives and Media" select the "Multimedia" tab, and on "Video DVD Discs" enter **gmplayer** as the command (though I can't remember if it's just **gmplayer** or **gmplayer /media/cdrom** or **gmplayer /dev/dvd**). You can try with those if it doesn't work at first, or look at your **/media** and **/dev** folders on root to see what's there.

---

### Post by Chilli Bob on 2007-06-18
Thanx for Mplayer suggestion, will try that when I get home.

---

