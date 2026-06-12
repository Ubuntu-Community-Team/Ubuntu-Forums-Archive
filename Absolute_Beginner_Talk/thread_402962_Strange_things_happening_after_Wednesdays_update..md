---
title: "Strange things happening after Wednesdays update."
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-04-06
OK first this is my Nvidia XServer Setting control console, as you can see everything looks fine but when I click on
 OpenGL/GLX infomation the the screen turns black and it goes to the log screen.

[IMG]http://i19.tinypic.com/34j7hpc.png[/IMG]

And now when I try to start a game like Ut 2004 or Think Tanks the screen turns black and it goes to the log screen, and if thats not bad enough if I leave my PC running for more than 6 minutes without activity the the screen turns black and it goes to the log screen. As long as I'm doing something it's fine, this is really bad for me because I host games on my PC and it goes to the log screen after 6 minutes or so even with the game server running. It's not rebooting it just goes back to the log in screen.

I really need help, I was thinking about just upgrading to Feisty to see it that will fix it.

Thanks 
Repent

---

### Post by Aircooledmadness on 2007-04-06
Sounds like youve got a graphics driver problem.

You can try reinstalling your video card driver

Or also do another apt-get update && apt-get upgrade to see if any new packages are out

And finally,  you could reconfigure your X by doing a sudo dpkg-reconfigure xserver-xorg

---

### Post by Repent on 2007-04-06
Wow I reinstalled my Nvidia driver and it works now, strange it worked just fine before the update.

Thanks man.

---

