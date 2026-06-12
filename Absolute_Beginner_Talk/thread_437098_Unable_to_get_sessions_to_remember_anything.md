---
title: "Unable to get sessions to remember anything"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by sthapit on 2007-05-08
Hi.  So I installed Ubuntu 7.04 desktop and everything works like a charm.  I have a very simple problem that's totally vexing me (as a newbie to linux).  First, I installed nvidia drivers and I'm able to set the resolution to 1440x900, but when I restart, it goes back to 1024x768 - very frustrating.  The second issue is that anything I add to System:Preferences:Sessions is completely ignored on the next login.  Lastly, is it possible to get gDesklets to start automatically?  Apologies for so many questions, but I figured they're all related.

---

### Post by orb9220 on 2007-05-08
> To set the resolution to 1440x900, but when I restart, it goes back to 1024x768

you need to run as an example **nvidia-settings** as root so you would run it as **sudo nvidia-settings **which would give it root write permissions to xorg.conf file.

or You could just add "1440x900" in front of each mode line where there is a "1024x768" by editing your xorg.conf

> The second issue is that anything I add to System:Preferences:Sessions is completely ignored


Goto sessions manager and on last tab called Session Options is **Automatically save changes to session** checked?

> Lastly, is it possible to get gDesklets to start automatically?

Yes just add gdesklets to **Startup Programs ** tab in sessions manager.

---

### Post by sthapit on 2007-05-08
> **orb9220 said:**
> you need to run as an example **nvidia-settings** as root so you would run it as **sudo nvidia-settings **which would give it root write permissions to xorg.conf file.

or You could just add "1440x900" in front of each mode line where there is a "1024x768" by editing your xorg.conf



Goto sessions manager and on last tab called Session Options is **Automatically save changes to session** checked?



Yes just add gdesklets to **Startup Programs ** tab in sessions manager.

so running suddo nvidia-settings works and now each time i start the computer, it starts at 1440x900 :)  thanks.

sessions is still not working though.  what do i need to do? automatically save is checked...

---

### Post by orb9220 on 2007-05-08
> sessions is still not working though. what do i need to do? automatically save is checked...

Try searching forums on:  > sessions and see what pops up. Sorry I know I have read about that issue before just don't know where.

---

### Post by sthapit on 2007-05-09
had to run sessions as sudo, i.e. sudo gnome-session-properties and then save it.  you have no idea how unintuitive this is to me as a windows user hehe. so i'm able to get gDesklets to start automatically.  is there anyway to get the "gDesklets Shell" window from popping up each time though on startup?

---

### Post by switchOv3rload on 2007-05-14
hey have gdesklets to run as a daemon...which is add 'gdesklets start' in your startup list in the gnome-session-properties.

---

