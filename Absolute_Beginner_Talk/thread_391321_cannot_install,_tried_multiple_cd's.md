---
title: "cannot install, tried multiple cd's"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by lovely? on 2007-03-23
:confused: i try to install linux edgy 6.10 on my computer, (AMDathlon 3400+ ATI radeon X800GTO, 1.25 gb ram)

when it tries to install, it goes into a screen that resembles a loading screen, but its all black and white and the loading bar goes off to the right for no reason (the part that goes off to the right is gray)

im really exasperated, running a memtest right now, but that will check out... should i try again without my ATI??? because without it, all i have is crappy onboard video 64mb:confused:

---

### Post by Kobalt on 2007-03-23
Is your onboard viedo card disabled in your bios ? I don't think it helps the LiveCD to launch properly if you have two carphic cards active...

---

### Post by ravis_31 on 2007-03-23
Ubuntu is known to have issues with ATi cards,i would suggest you to use the alternate install cd from [here]("http://releases.ubuntu.com/edgy/").This is a text based installer with which you can complete the installtion.
After completion,since yours is a ATi card,you can boot into recovery mode and do this

```
sudo dpkg-reconfigure xserver-xorg
```

Also,you might want to have a look [here]("https://wiki.ubuntu.com/Bugs/AtiDriver")

travis

---

### Post by lovely? on 2007-03-23
i dont understand. do you mean that this version of linux makes me type code to start programs? like DOS or something?

---

### Post by ravis_31 on 2007-03-24
You will boot into the command line where you'll have to modify one file at /etc/X11/xorg.conf and run 'startx' from the cli and you'll be able to into GUI.

travis

---

### Post by lovely? on 2007-03-25
hmm yea i have no idea what that means... first off, where do i find this file, if these boot cd's arent actually letting me 'boot'

---

