---
title: "Crash troubles with AMD/ATI Radeon HD 6400M/7400M on Macbook Pro 8.2"
date: 2014-07-31
forum: Apple Hardware Users
---

### Post by tienneOz on 2014-07-31
Hi,

I just reinstalled Ubuntu 14.04 on a macbook pro 8.2 with double video card (Intel HD and AMD/ATI Radeon HD 6400M/7400M). The first install worked perfect but now I got issues with my video card. It seems that the libre pilot doesn't do his work well and I can't use the proprietary one because I can't boot with it.
My major issue is that I can't put my computer on sleep mode. When I shut the top, the computer starts to become hot and I got a message saying "CPU temperature above average". At this point, the only thing I can do is hardrebooting. And when I choose sleep mode manuely, it doesn't display this message but only a "_" without further informations.
Other clues that it is my video card which is the problem is jerky video rendering and slow computer when a video is running. I have too an error message in the boot.log file : "Starting load fallback graphics devices [fail]". Finally, I can't use my external screen, Ubuntu don't recognize it.
By the way, I got some trouble during the installation process (using live USB), I had to manually change the boot configuration from "quiet splash" to "nomodeset". Any other configuration just gave me a blackscreen. Maybe it has a relation ?
I did a lot of research and handlings with no results...
I tried too to turn of the ATI card to use only the Intel one, but no success.
I too have my fans which a running fast for no reason and high CPU temps.

If anyone have a clue, It will be nice !

Thanks,

Étienne

---

### Post by coffeecat on 2014-07-31
Support request, not chat.

*Thread moved to **Apple Users**.*

---

### Post by tienneOz on 2014-07-31
Thanks for having moved the thread, sorry for the mistake.

---

### Post by coffeecat on 2014-07-31
No problem - the forum is like a labyrinth! I've edited the thread title to include your Macbook model which may help to attract those who can help.

Welcome to the forum!

---

### Post by tienneOz on 2014-08-02
I finally solved my issue. If anyone need, I did a clean install of mac os then Ubuntu using these [instructions](http://ubuntuforums.org/showthread.php?t=2157775). I finally had a working system using only the Intel video card. But I still didn't have my external screen working so I tried to boot from ATI allowed grub and all was surprisingly working fine !
I hope this will help.

---

