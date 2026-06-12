---
title: "Rolling back updates"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by pjhenry1216 on 2008-01-22
I tried to find a situation that matched mine, but either I don't know the correct terms to search for or I just can't find it.  Anyway, I finally got my wireless working and set the thing to update, I may have clicked it to search for too many updates or whatever, but it said it found 187 updates.  Said it needed to restart to finish installing the updates.  However, now after the Ubuntu progress bar, but before the login screen, it just hangs at a black screen with the little circling wait mouse pointer indefinitely.  Is there any command I can run from recovery mode to roll back and uninstall those updates so I can actually take a look at not just install all the updates blindly?  I'm using gutsy.  I've used linux for about a total of 5 days.  I have virtually no background whatsoever with anything remotely related to linux.  I'm coming from a windows background.  i'm fairly competent with Windows and computers in general (i built this specific system from scratch and it worked with a clean install of gutsy, but these updates apparently broke it).  Any help would be appreciated.  Commands would have to be relatively specific cause I don't really know many commands off-hand.  i've read very brief overviews of using terminal and only know the *very* basic basics.

edit:  just a quick note.  when i hit the power button to power down, it shows all the status messages and its always frozen on the same one, "running local boot scripts" or something to that affect.  dunno if that helps.

---

### Post by crjackson on 2008-01-22
try booting into recovery mode.  If you are in a text screen, then login.  Once logged in type exit and see if it takes you to the graphical desktop.

If that works, then edit your /boot/gurb/menu.lst file.  Find the two entries that have "splash" and change them to "nosplash"

It's a shot in th dark but who knows?

---

### Post by pjhenry1216 on 2008-01-22
unfortunately, that did not work.  i logged in and then typed exit, all it did was clear the screen and put the prompt at the top of the screen.  i typed exit again and then it tried to put into graphical mode and it at least appeared in hang in the same way.  just a black screen with the white waiting cursor.  if it helps at all, the "running local boot script" or whatever the message was has something along the lines of "/etc/local.rc" or something like that in parenthesis.  i keep on telling myself i'll write down, but i then keep saying, nah, you can remember that, but then i run up stairs and i sit here and i'm like... darn.  anyway, the next time i'll remember to write down the exact message that it seems to be freezing on.

---

