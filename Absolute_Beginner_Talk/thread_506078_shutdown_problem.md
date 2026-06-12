---
title: "shutdown problem"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-21
I read other peoples posts who were having similair problems but mine must be a little unique or something...

When I shutdown, it gets stuck on the 'Ubuntu' screen, the bar will fill up, but instead of turning off, it kind of srews up the screen for a sec then goes back to the same screen...

Ive been doing a lot of work trying to get my videa card to work lately, would that have anything to do with it? If so how do I fix it?

---

### Post by ukulele_ninja on 2007-07-21
any help would be great, it makes me nervous doing a hard shutdown everytime!

---

### Post by Trebaruna on 2007-07-21
First of all, try and wait a bit so that members have some time to reply ;)

Secondly, what you can do is checkout the logs (System -> Administration -> System log) and see if any of them show any errors.

Also, you can edit the bootloader to not show the splash screen, but to let it show the stuff it is doing.
The non-permanent way to do this (just one boot) is to edit a line when you reach the GRUB menu (press esc when it tells you to if you dont get the menu). Select the kernel you normally boot (the top one by default) and press e. Select the second line (should be very long) and press e. Now you get a simple editor. Go to the end of the line and change splash to nosplash. Press enter. Press b to boot.
This should give you normal boot messages and also shutdown messages instead of the ubuntu screen.
The next time you start your machine the line is back to normal.

If you see any errors, post back. I'm afraid Im not that much of an expert, but at least others will have more info to work with.

---

### Post by ukulele_ninja on 2007-07-21
I have kubuntu, how do I get to the administartor menu?

---

### Post by Trebaruna on 2007-07-21
Oh dear. I am afraid I know fairly little about KDE.
You can use the terminal, too:
Tell it to "cat /var/log/messages | more" without qoutes.

This will give you a LOT of text as it is the main logfile. Try and see if any of it makes sense (anything saying ERROR: blabla should be interesting).

And of course try the nosplash thing. Might be less confusing, and should at least be more relevant (not every little schmip is reported).

---

### Post by ukulele_ninja on 2007-07-21
> **Trebaruna said:**
> First of all, try and wait a bit so that members have some time to reply ;)

Secondly, what you can do is checkout the logs (System -> Administration -> System log) and see if any of them show any errors.

Also, you can edit the bootloader to not show the splash screen, but to let it show the stuff it is doing.
The non-permanent way to do this (just one boot) is to edit a line when you reach the GRUB menu (press esc when it tells you to if you dont get the menu). Select the kernel you normally boot (the top one by default) and press e. Select the second line (should be very long) and press e. Now you get a simple editor. Go to the end of the line and change splash to nosplash. Press enter. Press b to boot.
This should give you normal boot messages and also shutdown messages instead of the ubuntu screen.
The next time you start your machine the line is back to normal.

If you see any errors, post back. I'm afraid Im not that much of an expert, but at least others will have more info to work with.

When I went into the editor for the second step it brought up a long command line but i didnt see anything to edit. Do i just type in nosplash?

---

