---
title: "&quot;Lost&quot; my shutdown icon"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by twrock on 2007-05-21
I somehow lost my "shutdown" icon (and word) in the menu that pops up when I click Main Menu > Quit.... I don't think I did anything to "delete" it. The other five standard icons/options are still there. Can anyone help me get it back?

Incidentally, I'm using Feisty.

Thanks.

---

### Post by finer recliner on 2007-05-21
something similar happened to me once. however that was when i was dapper, and now i'm on feisty. i remember the fix was as easy as checking a box in a settings window. but i dont know where that window is anymore; i think it got moved in feisty.

try going to some of the system > prefrences or system > administration tools and see if you can find it.
try system > prefrences > sessions (just a guess)

---

### Post by Rotaj on 2007-05-21
try right-clicking on an empty area of of a panel, add to panel( 1st option), click and drag to where you want the shut down button in the panel.

---

### Post by twrock on 2007-05-21
It's not a panel "thing". I actually don't want a shutdown icon in my panel (yeah, to each his own, I guess). But I do want a shutdown icon in the standard menu (the one that includes Log Out, Lock Screen, Switch User, Suspend, and Hibernate).

I will try hunting for something in the system settings.

---

### Post by Austin_KW on 2007-05-21
Did you change your display manager eg, switch to kdm as your login manager. 
If so and you are running gnome as your window manager then you may want to switch back to gdm to get all the quit options;

"sudo dpkg-reconfigure gdm"
and select gdm as your display manager.

This may need a reboot or a display manager restart.

---

### Post by wormser on 2007-05-22
> **twrock said:**
> I somehow lost my "shutdown" icon (and word) in the menu that pops up when I click Main Menu > Quit.... I don't think I did anything to "delete" it. The other five standard icons/options are still there. Can anyone help me get it back?

Incidentally, I'm using Feisty.

Thanks.

The same thing just happened to me.  My shut down button is no longer there.  I did change my boot screen earlier and have not rebooted since.  I wonder if that has something to do with it?  Well, I am just going to do a sudo halt because I do not have time right now.

Did you ever solve this twrock?

---

### Post by twrock on 2007-05-22
I'm home from a day of travel. Thanks for the replies.
Austin, I haven't done anything like you are wondering (at least not to my knowledge). I haven't made any changes like that.

Wormser, have you done anything else to change your system?

The only possibility I can imagine (i.e. the only "strange" thing I did recently) was that I created another "user" called "guest", messed around with it for a day, then deleted it. Since the "/home/guest" folder didn't go away, I manually deleted it. Is there any way that this can be related? I can't imagine.

Today, I messed around a lot with the Configuration Editor, But I didn't find anything that worked. So I'm still hoping someone can give me some other ideas.  I'm at a loss.

Incidentally, I did add a "quit" icon to my panel to see what would happen. It didn't do anything to help and only brings up the same menu sans the "shutdown" icon.:(

---

### Post by ikonia on 2007-05-22
There is a debatable bug within gnome on this one, in some situations it appears a theme file or gdm file can interact and change the default settings.  I did have a bug repoted to this but as it is random when this occurs it is hard to prove / issolate. I am working on getting hard fact on this bug.

The solution is this

Go to: System -> Administration -> Login Window

On the Local tab under "Menu Bar" the option "Show Actions menu" has to be enabled.

you should be good to go.

---

### Post by twrock on 2007-05-22
Yes! That's it! Thanks much ikonia.

I hadn't noticed that I had lost the Restart icon as well (don't use it much), but everything is back. I also noticed that the shutdown option was missing from the login window options as well. I suspect this will solve that too.

Thanks again.

---

### Post by twrock on 2007-05-22
Final follow up from me.

Yes, everything is back to normal, both with the standard menu option at the GDM login screen and the Quit menu.

Since you mentioned that this is a potential bug and that it might have something to do with the GDM theme, I should mention that I have been messing around extensively with my GDM theme (particularly since I had been tweaking a black theme that I uploaded to GNOME-Look.org; it's pretty nice looking, if I do say so myself ;)). So I can think of two possibilities:
1. there is some kind of bug, possibly "inconsistent" and difficult to reproduce
2. some time in all that messing around, I inadvertently clicked on that particular box and turned it off

Since this is all taking place on my laptop, and since it is configured to respond to a tap on the touchpad as a click, it is quite possible it is nothing more than an errant click in my case. I do make errant clicks with some regularity, particularly when I'm not working at a table. Anyway, I just thought I'd at least mention all of that for your consideration.

---

### Post by wormser on 2007-05-22
> **ikonia said:**
> There is a debatable bug within gnome on this one, in some situations it appears a theme file or gdm file can interact and change the default settings.  I did have a bug repoted to this but as it is random when this occurs it is hard to prove / issolate. I am working on getting hard fact on this bug.

The solution is this

Go to: System -> Administration -> Login Window

On the Local tab under "Menu Bar" the option "Show Actions menu" has to be enabled.

you should be good to go.

That solution resolved the shut down icon problem.

One thing I also noticed.  You can select multiple themes.  When I rebooted after changing my log in screen the wrong screen showed up.  When going back to the login window there were multiple themes checked.  I did not do this.  It took a couple of boots and unchecking before the right screen appeared.  Maybe this also has something to do with the theme file or gdm file interacting with the default session?

---

### Post by forth on 2007-05-27
IKONIA I cant thank you enough, although it is a silly bug. Cheers again!!!

---

