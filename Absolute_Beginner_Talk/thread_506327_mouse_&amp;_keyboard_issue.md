---
title: "mouse &amp; keyboard issue"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by jmlock on 2007-07-21
hello all, 
I have just installed feisty fawn and have had a couple of problems. the 1st was nvidia drivers, which was solved by other forum posts. thank you. on to the problem at hand.

running from live cd, all is well. running from installed system hmmmm, not so good. at 1st i thought my system  was freezing....nay nay. the os seems to be purring right along in the background but 15-60 seconds after the desktop loads, my mouse and keyboard stop working. my mouse pointer is visible but will not move and the keyboard wont respond. i also noticed that even the caps lock light stops comming on.

i havent found a thread for this yet, but hopefully someone will have a solution.

thank you

---

### Post by nitro_n2o on 2007-07-21
is your mouse and keyboard PS2 or usb

---

### Post by jmlock on 2007-07-21
both are ps2 (plugged into the round colored ports) but one has an adapter that came with it (mouse i think) going from usb to ps2

---

### Post by jmlock on 2007-07-21
the mouse i a rollerball type , logitech i think. dont know if that matters.

thanks

---

### Post by jmlock on 2007-07-21
sorry for the bump, but ive done 3 complete reinstalls now and no joy. 

do you think i should try another older version ????

---

### Post by lisati on 2007-07-21
Have a look at [http://ubuntuforums.org/showthread.php?t=498785&highlight=force+irqpoll](http://ubuntuforums.org/showthread.php?t=498785&highlight=force+irqpoll) - you might find some helpful ideas there

---

### Post by Majorix on 2007-07-21
Try moving your xorg.conf from the LiveCD to your actual installation. When you are on LiveCD, go to your /etc/X11 folder, find xorg.conf and write that on a floppy or usb drive or something. As a last resort you can even email it to yourself :D

Then replace your xorg.conf under the installed system with this one and see if everything is fine.

Post back!

---

### Post by jmlock on 2007-07-21
ill give it a try, but it barely gives me enough time to open anything before the mouse and keyboard disconnect themselves (for lack of a better term)

---

### Post by Majorix on 2007-07-21
Oh sorry you said 15 secs.. I read that as 15 mins :(

What about dropping to the terminal? (CTRL+ALT+F1)

Do the changes from there, then come back with ALT+F7 or a good old restart :D


If you need any guidance on how to do the things from the black screen, post here and we will help. Or they will help since I am going to bed *yawn*

Good luck!

---

### Post by jmlock on 2007-07-21
> **Majorix said:**
> Try moving your xorg.conf from the LiveCD to your actual installation. When you are on LiveCD, go to your /etc/X11 folder, find xorg.conf and write that on a floppy or usb drive or something. As a last resort you can even email it to yourself :D

Then replace your xorg.conf under the installed system with this one and see if everything is fine.

Post back!

can anyone suggest how to do this from the black screen prompt??
thank you

---

### Post by jmlock on 2007-07-21
dont know yet if this is solved, but heres what ive done.
i did a full new install of dapper drake....eveything works smoothly. did all updates....still ok.
am doing the online upgrade to edgy eft (over 1 hour download):-\". i will than do all updates and try it out. if all still goes smoothly, i may do the next upgrade to FF. well see.

ill post again if this works maybe someone else is having the same issues.

---

