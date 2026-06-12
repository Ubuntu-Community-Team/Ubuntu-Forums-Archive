---
title: "firefox dies when flash kicks in?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2007-03-24
hey guys, i have a pretty big problem here. firefox works well, untill i go to a site with streaming video or music and then it just automaticly closes. i guess flash or java is doing this? and it never happened untill i installed beryl, but even when i kill beryl it still does it. 

any suggestions on how i could fix this?? thanks

---

### Post by taurus on 2007-03-24
What version of flash plugin do you have?  Open firefox and in the address field, type

```
about:plugins
```

---

### Post by xxdad1xx on 2007-03-25
I have the same problem!! I have firefox 1.5 installed. This only happens with flash 9.0 r31. Any help with this would be greatly appreciated. I have also tried the instructions here > [http://www.linuxquestions.org/questions/showthread.php?t=509340](http://www.linuxquestions.org/questions/showthread.php?t=509340) . :confused:

---

### Post by Obywan on 2007-03-26
i suffer from the same broblem as all yall, about 5-10 mins after i fire up firefox, it just up and dies on me, i have 3 OS's on my comp, ubuntu64 (ver5.10) ubuntu 32 (ver 6.06) and windows XP professional, my comp is an athalon 64, 4000 chip 512 ram, Nvidia 7300gs and a 40 gig HD... help please??? anyone??????

---

### Post by Penguin Power on 2007-03-26
My bad. I've completely forgotten what the solution to this problem was, but it's in the forums *somewhere*. Maybe it was updating to the most recent version of flash...

In the meantime, NoScript will stop Firefox crashing.

---

### Post by xxdad1xx on 2007-03-26
How do I use NoScript to help with this issue?

---

### Post by da1nonlymikeo on 2007-03-26
ah i just fixed it! im not really sure how or what was actually wrong but i went into synamptic package maniger and completely deleted all the flash plugin files that where installed. and then just reinstalled a fresh updated version of flash. theres a how to: install flash. just search it in forums. =) no moree firefix crashes. but for some reason whenever i open a video in vlc or mplayer they crash? haha if its not one problem its another.

---

### Post by Obywan on 2007-03-27
i have ubuntu 6.06 on my comp and firefox shuts down after about 5 or 10 mins... any suggestions???

---

### Post by xxdad1xx on 2007-03-28
NoScript did stop the Firefox from closing, but still no flash 9. I have no Sym links  to or anything else that shows flash 7. However when I ran about:plugins it shows version 7. When I go to this link > [http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/) it shows that I have flash nine installed. Does anyone have any idea where Firefox would have stored this path to flash 7?

---

### Post by xxdad1xx on 2007-03-29
I finally figured it out. I had to install libflashplayer.so to /usr/lib/mozilla/plugins/ and then create a symbolic link in /usr/lib/firefox/plugins/ and /usr/lib/mozilla-firefox/plugins/.  :guitar:

---

