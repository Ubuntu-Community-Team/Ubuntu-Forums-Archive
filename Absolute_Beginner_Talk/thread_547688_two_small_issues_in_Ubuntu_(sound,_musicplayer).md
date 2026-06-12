---
title: "two small issues in Ubuntu (sound, musicplayer)"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by alwiap on 2007-09-10
1.  Everytime I boot up my sound doesnt work, I go to System > Preferences > Sound, and all the tracks are on 'USB Audio - Not Connected', so I go to the dropdown list and select 'USB Audio', and then I can hear again.  I have to do that every time I start up. Is there any way I don't have to do that?  I have a C-Media USB headset (Icemat Siberias).

2.  I have no idea how this happened, but I use rhythmbox media player, and I liked having the little music notes at the top bar when I minimized so I could control it from there.  I did something and now the minimized icon is no longer there. I went into preferences of rhythmbox but there doesn't appear to be a setting in which I can put the system tray icon back up there.  Any solutions?

Thanks for reading.

---

### Post by glaubergoncalves on 2007-09-10
1. Do you have any on-board sound-card? If so, try disabling it on your system BIOS to see what happens...

2. I don't know how to restore the minimized icon, you are referring to the tray icon, right? I would say you could re-intall Rhythmbox, or erase it's personal settings folder on your /home directory, but there must be better options. I can give a suggestion: go to the Synaptic Packet Manager and look for the "Music Applet", then install it. It's a nice way to control your player trough the task bar, and it does show the current music that's playing when you hover the mouse over it.

---

### Post by alwiap on 2007-09-10
> **glaubergoncalves said:**
> 1. Do you have any on-board sound-card? If so, try disabling it on your system BIOS to see what happens...

2. I don't know how to restore the minimized icon, you are referring to the tray icon, right? I would say you could re-intall Rhythmbox, or erase it's personal settings folder on your /home directory, but there must be better options. I can give a suggestion: go to the Synaptic Packet Manager and look for the "Music Applet", then install it. It's a nice way to control your player trough the task bar, and it does show the current music that's playing when you hover the mouse over it.

I uninstalled and reinstalled Rhythmbox in Add/Remove, but it retained my previous settings, so I will try erasing the personal settings.  Exactly where are they in my /home directory?
Thanks for your help

---

### Post by alwiap on 2007-09-10
also, i have the same problem with gaim, when i minimize it it doesnt appear in my system tray either :(

---

### Post by glaubergoncalves on 2007-09-10
If the same thing is happening with Gaim, then probably you've disabled the "Notification Area" applet... Try right-clicking the upper panel, then choose "Add to panel", then select the "Notification Area" applet and add to it.

---

### Post by alwiap on 2007-09-10
> **glaubergoncalves said:**
> If the same thing is happening with Gaim, then probably you've disabled the "Notification Area" applet... Try right-clicking the upper panel, then choose "Add to panel", then select the "Notification Area" applet and add to it.

Doh!

That solved the problem, can't thank you enough for your help.  Now I feel a bit smarter :)

---

### Post by glaubergoncalves on 2007-09-10
Glad for helping!

---

### Post by ocramavaf on 2008-01-27
hey i have a few problems ever since i installed xubuntu sound isent working i tried changing the mixer but no luck, i dont know if its with my soundcard or what
Also whenever i try to install any application except the ubuntu recomended ones with add/remove i get an error message saying its conflicting with something but doesent specify what.
It would be great if you could help

---

### Post by glaubergoncalves on 2008-01-27
Hi ocramavaf. Xubuntu is not my cup of tea... but you could say more about your hardware, what sound card do you own, what's your motherboard and processor, for example. It helps on giving better answers to your hardware issues. One thing you could do in order to achieve this is opening a terminal, type *lspci*, and then copy/paste it's output on this tread, it'll help to identify your hardware and come up with some possible answers...

   About the programs you try to install, which ones exactly are they? What's exactly the message you get when you try to install them? And keep in mind that *.exe* files are Windows only, you can't install them on Linux, at least not natively. A cool site that I recommend you to look for new programs is [GetDeb](http://www.getdeb.net/), there you'll find a vast amount of applications that it's just download, click and install ;).

---

