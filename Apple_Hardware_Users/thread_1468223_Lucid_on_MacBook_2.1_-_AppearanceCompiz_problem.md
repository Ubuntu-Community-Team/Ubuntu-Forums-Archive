---
title: "Lucid on MacBook 2.1 - Appearance/Compiz problem"
date: 2010-05-01
forum: Apple Hardware Users
---

### Post by G_u_s on 2010-05-01
Hi all,

I've just updated my MacBook 2.1, from 9.10 to 10.04.

The first time I logged in, I had display problems:
- Windows were too high, overlapping the top panel.
- Desktop icons were also a tad too high, as if they didn't "register" the top panel when ordering themselves.
- On top of all of that, keyboard shortcuts were not working (Alt + F7 to move windows around, for instance).

Thanks to having Gnome Do installed, i succeeded in invoking the Appearance menu, and noticed that visual effects were disabled. When i enabled them (any of the three other options - Normal, Extra, Custom), it said "enabling drivers" or something like that, and things started to work as before. I was happy, until i rebooted and noticed that it didn't save my changes. It doesn't change anything that I reboot, log out and back in, or use Ctrl+Alt+Backspace.

One other thing I have noticed: it also didn't save my changing the number of workspaces.

Any idea? This is my work laptop, I can't really afford to have to hack every time i boot... Thank you very much for your help!

---

### Post by linuxopjemac on 2010-05-02
Good luck solving this. I never recommend to upgrade to a newer release on a work computer, unless I have support that it works.
Just keep an eye on this page:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

Sorry can't help you with your problem though.

---

### Post by G_u_s on 2010-05-02
Thank you, I know the page, I used it when I installed 9.04, and later 9.10, on this MacBook.

I made a backup of all my important data before switching, and i could reinstall Karmic if needed.

However, it seems the problem is relatively minor and could easily be fixed, if only I had an idea of what is wrong. I can fix it by hand everytime, it's just a matter of going to Appearance=>Visual Effects and going from "None" to something else. 

Actually, I've just switched back to "None" and it keeps working. So the problem appears to be that the wrong drivers are loaded at startup. It's probably just a rogue line in a config file. I just need to know which...

Please help =D

---

### Post by G_u_s on 2010-05-03
Actually, it seems it was not a Mac issue at all. See this thread (and post) for more info: [http://ubuntuforums.org/showthread.php?p=9224455#post9221161](http://ubuntuforums.org/showthread.php?p=9224455#post9221161)

---

