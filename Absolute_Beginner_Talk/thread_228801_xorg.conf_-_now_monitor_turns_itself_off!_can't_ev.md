---
title: "xorg.conf - now monitor turns itself off! can't even login.."
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by CBTF on 2006-08-03
Hmm.. hi guys. Im new to ubuntu and ive been searching for a way to change the system's screen resolution. Following instructions I saw given to another on the help forums, I did the whole xorg.conf thing.

I pressed enter for everything (had no clue what all those questions were about) and when it came to screen resolution I chose 1280 x 760, 32 bit color.

It now occurs to me that I run 1280 x 1024 in XP which is what I wanted..

Anyhow.. when I logged back in, the login screen was the correct resolution. I had finally fixed the issue. Seems like I got excited just a little too fast. After I put my PW in and it begins to login, my monitor turns itself off and says "Input signal out of range."

So.. how can I possibly revert the changes I made if I cant get into ubuntu?!

Please help a frustrated n00b. :(

---

### Post by spamalam on 2006-08-03
well i guess you can do it from the console, your monitor presumable turns off when xsession starts? (when the login screen comes up).

Noting that I'm a complete n00b.  After i installed the nvidia drivers, my main monitor doesn't work.  So i pressed esc when GRUB comes up, and then chose "Recovery Mode".  You then go to prompt, and you can edit/change/whatever from the terminal then.

Something like
su root
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_broken
mv /etc/X11/xorg.conf_backup /etc/x11/xorg.conf
Then reboot will probably work to restore your backup copy.  Otherwise vi it all back in.

---

### Post by CBTF on 2006-08-03
Wow. I realize half of what I posted wasn't correct. I used:

dpkg-reconfigure xserver-xorg

To change my resolution to 1280x1024, not 760 like I had thought.

Anyways, Ubuntu is working on another old monitor I hooked up.. so is this a hardware thing? If so, what should I do? 

SHould i still try the steps above, do they apply to dpkg-reconfigure xserver-xorg?

:(

---

### Post by CBTF on 2006-08-03
Bump- Still not having any luck. Ive changed the .conf many times to no avail.

---

