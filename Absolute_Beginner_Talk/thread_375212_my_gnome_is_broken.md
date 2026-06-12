---
title: "my gnome is broken"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by nonewmsgs on 2007-03-03
my gnome died.  i ctrl+alt+bkspced and i got to the login and logged in and heard the familiar gnome beer bottle whistle, but then nothing.  that bar across the screen that says loading natalius and what not doesnt come up.  i just have a cursor and no icons or menus.  kde will still start but i want my gnome.

who wants to be a hero?

---

### Post by luke411 on 2007-03-03
If it was working before, did you change any settings to your video card? Your xserver is not loading and that usually means there is an issue with your video card.

when you get to the cursor again, log in as root and type

dpkg-reconfigure xserver-xorg

This will give you a 'semi'-menu with which to configure your video card. It will walk you through several steps, only one or two that probably need changed, specifically your video card settings. There is also one screen that will attempt to auto-detect your card, which might take care of it without changing anything else.

---

### Post by nonewmsgs on 2007-03-03
i didnt touch my videocard for a while...last tihng i was messing around with was different sound packages comparing oss to alsa, but ill definately try that now!

---

### Post by nonewmsgs on 2007-03-03
wait.  where do i type this? in kde terminal?

---

### Post by nonewmsgs on 2007-03-03
ok i did the dpkg-reconfigure xserver-xorg thing but gnome isnt better yet.

---

### Post by nonewmsgs on 2007-03-03
woooh it did fix it after all!!!! first it stopped starting at all
then i went to /etc/X11 and sudo pico xorg.conf and there is this one boolean thing that always makes it not want to start after using the wizard.

thank you!!!1

---

### Post by nonewmsgs on 2007-03-03
yeah it wont start if UseFBDev is set to "true"
i figured a good bit of that out when i was going from an ati card to a nvidia because it's supported better.

fbdev.  is that a frame buffer?  what is that?

---

### Post by luke411 on 2007-03-03
I think it's the frame buffer that the kernel can use. At any rate, glad you're up and running.

---

### Post by nonewmsgs on 2007-03-04
does that mean it isnt using the videocard's memory?  could that be causing more graphics intensive games to have very low frame rates despite this computer being well over 1ghz above the recomended system?

---

