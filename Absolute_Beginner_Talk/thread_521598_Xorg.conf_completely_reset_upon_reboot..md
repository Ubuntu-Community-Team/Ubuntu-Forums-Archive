---
title: "Xorg.conf completely reset upon reboot."
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Diablos_Raven on 2007-08-09
I was running Feisty Fawn and I enabled the restricted drivers for my integrated Nvidia graphics chip and then I edited xorg.conf so that i could use the back and forward buttons on my Logitech mouse. I fell alseep while watching a movie then like 3 hours later I woke up and shut my pc down for the night. I then woke up like 3 or 4 hours later and booted my pc up and found that I xorg.conf was reset to its default state. I had to re-enable the restricted drivers and the mouse configuration was no longer there.

Why did this happen and how do I prevent it from happening again?

---

### Post by por100pre1 on 2007-08-09
Did you backup your xorg.conf file? If you did so you can restore it now...

---

### Post by MockY on 2007-08-09
That doesn't help his cause however in the long run. Having to replace with the backup after every reboot gets pretty old after a while and doesn't explain why this happened so it could be prevented or fixed. I haven't experienced this issue however, so I have no solution. Just wanted to reflect on it since small things like this makes new users reluctant to continue using Linux, something I don't want to happen.

---

### Post by por100pre1 on 2007-08-09
> **MockY said:**
> That doesn't help his cause however in the long run. Having to replace with the backup after every reboot gets pretty old after a while and doesn't explain why this happened so it could be prevented or fixed. I haven't experienced this issue however, so I have no solution. Just wanted to reflect on it since small things like this makes new users reluctant to continue using Linux, something I don't want to happen.
[COLOR="Red"][B][B]
The poster edited xorg.conf for a mouse issue. To tell a new user to dpkg-reconfigure xserver-xorg is big business and shouldn't be taken lightly. Please, read before posting.[/B][/B][/COLOR] :mad:

---

### Post by MockY on 2007-08-09
> **por100pre1 said:**
> [COLOR="Red"][B][B]
The poster edited xorg.conf for a mouse issue. To tell a new user to dpkg-reconfigure xserver-xorg is big business and shouldn't be taken lightly. Please, read before posting.[/B][/B][/COLOR] :mad:

In this case, xorg.conf was already configured and in working order. This happened without touching xorg.conf at the time, and since this happened once, it will most likely happen again for no reason once it is backed up again. And it is the reason WHY and not so much HOW, he wants to know.

---

### Post by por100pre1 on 2007-08-09
> **MockY said:**
> In this case, xorg.conf was already configured and in working order. This happened without touching xorg.conf at the time, and since this happened once, it will most likely happen again for no reason once it is backed up again. And it is the reason WHY and not so much HOW, he wants to know.

[COLOR="Blue"][SIZE="4"]Ok. Where's your suggestion???[/SIZE][/COLOR]

---

### Post by MockY on 2007-08-09
> **por100pre1 said:**
> [COLOR="Blue"][SIZE="4"]Ok. Where's your suggestion???[/SIZE][/COLOR]


First of all, your posts with colored fonts in various sizes just makes me not take you seriously. Second, I said in my first post that I didn't have a suggestion (speaking of reading posts) nor claimed I had one. All I did was to point out that replacing the backup after every boot is a pain in the rear end and that the initial poster wanted to know why this happened in the first place, and not so much how to fix it (since he obviously can use a back up or manually enter it again). Granted, your suggestion would fix it temporarily until it happens again, but I don't think he wants to keep replacing the file all the time.  I am also interested in how such thing can happen (it smells OS instability long way) and want to highlight the issue so that it can be fixed in later releases or updates.

---

### Post by Diablos_Raven on 2007-08-09
> **por100pre1 said:**
> Did you backup your xorg.conf file? If you did so you can restore it now...

Just a little extra info I saved a backup of the original default xorg.conf as everyone should do when editing something of this nature. But my issue has nothing to do with a backup of any sort my issue is I edited this file and it was working fine. I used CTRL-ALT_BACKSPACE to reset X and everything was working fine then I shutdown for like 4 hours and booted up and it was reset back to the original default xorg.conf. Also not just the mouse keys were reset but the restricted graphics drivers as well. I had to uninstall them and reinstall them as well.

---

### Post by adamprawitz on 2008-02-23
The exact same thing happened to me.  And no matter how many times/ways I rewrite the xorg.conf file, it always resorts back to the previous one!  Very frustrating!  Someone please help us!

---

