---
title: "How can I brings the drums back in Xubuntu?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by gyalakias on 2007-10-28
I just installed Xubuntu Gutsy Gibbon using the alternative CD (not the desktop one). Everything is fine so far, but there is one small problem...

No startup drums! Instead I get a small beep when the login screen appears. Please note that I do have sound and ALSA works just fine.

Is there a way to bring the drums back?

 For that matter, is there a way to add my own login/logout/shutdown sounds in Xubuntu*?

Thank you very much for your time.

*I have a couple of my own sounds that I happen to like very much.

---

### Post by chlorinekid on 2007-10-28
system > admin > login window

click on the accessibility tab, you can select sounds from there i think.

sounds are in /usr/share/sounds

---

### Post by gyalakias on 2007-10-28
Hmm... It seems like there are no sounds in the /usr/share/sounds folder, but there are 5 other folders:

/alsa
/ekiga
/linphone
/opl3
/purple

As far I can tell, there is no drum sound in any of them. Maybe I should add them on my own?

If yes, how should I name them?

**EDIT:** Yep, the problem is that the drum sound is absent. Can anyone post it in here? I can't seem to find it anywhere.

---

### Post by Mark76 on 2008-01-06
Your best bet would be to create a folder in usr/share/sounds (open thunar as root by typing sudo thunar into a terminal) and then to trawl [www.gnome-look.org](www.gnome-look.org) and [www.sfce-look.org](www.sfce-look.org) for sounds you like, drop the .wav files into the new folder and then point the login window to the ones you want to use.

Or just leave it in your home folder and direct the login window to there.

---

