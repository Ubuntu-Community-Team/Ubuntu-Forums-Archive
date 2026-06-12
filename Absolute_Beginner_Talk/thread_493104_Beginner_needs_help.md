---
title: "Beginner needs help"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-05
Hello, i am having a problem with my system's Suspend option. When i close the lid of my machine, Ubuntu is set to enter suspend mode. This also happens with the lid open, if the machine is left alone for 30 mins.
When it recovers from suspend mode, i get an error saying that "Suspend failed. Check the help log for further information."

I started a thread yesterday about another issue i was experiencing and i think this is causing the problem as it happens right after recovering from suspend mode.Check here for the display issue:[[COLOR="Blue"]_http://ubuntuforums.org/showthread.php?t=492199_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=492199")

Is this a normal problem with an easy fix?

---

### Post by wastedfluid on 2007-07-05
Does it still suspend and recover?  As long as it's usable, I wouldn't worry about it.  My suspend used to work, and my hibernation didn't - and every time I booted from Suspend - it would tell me my computer didn't suspend properly - bu everything worked. 

I switched to alternate methods of hibernating, and suspending.  I see you're using 7.04.  Let me look up the thread for you.

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

Hopefully, that fixes your suspend problems.  Usually, when one doesn't work - the other method works.  As far as the actions that take place when you close your lid - my laptop has never done that.  To change that behavior, go to System -> Preferneces -> Power Management.

Good luck!

---

### Post by ITdrummer on 2007-07-05
well, the problem i have with my windows displaying improperly happens now matter how i enter suspend mode:  closing the lid or clicking the icon.  Everything seems to work fine when it returns from suspend but i have to restart my machine to get the windows working properly again

---

### Post by wastedfluid on 2007-07-05
> **ITdrummer said:**
> well, the problem i have with my windows displaying improperly happens now matter how i enter suspend mode:  closing the lid or clicking the icon.  Everything seems to work fine when it returns from suspend but i have to restart my machine to get the windows working properly again

Ahh.  Now I understand.

Try [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

If that doesn't fix it, I'm not quite sure.  Hope this does fix it, though!

---

### Post by ITdrummer on 2007-07-05
isnt that the same link you sent earlier?

---

### Post by ITdrummer on 2007-07-05
more help needed.......

---

### Post by ITdrummer on 2007-07-05
Should i post this thread in another area?  Seems like no one knows/cares about suspend issues?

45 views
2 replies...

---

### Post by wastedfluid on 2007-07-06
> **ITdrummer said:**
> Should i post this thread in another area?  Seems like no one knows/cares about suspend issues?

45 views
2 replies...

Did you try implementing the s2 method I provided?  Usually, if the "suspend" and "hibernate" that come wit Fiesty don't work.. I've seen great success with people trying to 's2" method(myself included.)

Did it not work for you?  What's the problem??

---

### Post by ITdrummer on 2007-07-06
Well i read through that link you gave me.  The issues discussed dont relate to my problem.  When my computer returns from standby, the machine works great.  It doesnt freeze or performance doesnt slow down, its just the damn windows..  Everything i open only shows the title bar and the border.  When i click on a tab such as Applications, the dropdown list doesnt display until i move my cursor over the dropdown items.  My desktop is the same way, no icons until i move my mouse pointer over them.

That link looked helpful and the suggestion is worth a try, im just trying to see if someone else has experienced my same problem and maybe have a better/easier solution.

---

