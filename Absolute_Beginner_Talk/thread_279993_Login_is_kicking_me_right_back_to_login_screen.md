---
title: "Login is kicking me right back to login screen"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by hotstovejer on 2006-10-18
Got a weird occurance going on with my Dapper install. I go to login at the greeter, then when I enter in my correct user name and password, it flashes a TTY at me, then shows me the Nvidia splash screen again, then takes me back to the login greeter. 

Any idea as to what would be causing this? I can log in to the tty just fine, so there's nothing wrong with my account. Also, when I log in as root in recovery mode, it takes me right into Gnome. 

Thanks!

---

### Post by kidders on 2006-10-18
Hi there,

There might be a problem with your Gnome settings.

I use KDE, and if something like this happened to me, my first instinct would be to drop to a console and type **mv ~/.kde ~/dotkde**. I imagine the same thing would work for Gnome.

If another login attempt fails, you can "mv" your .gnome (?) back again, and try something else. If you succeed, you can log back out and start copying back settings, parts at a time, until you hit one that breaks.

Let us know if you have any luck!

---

### Post by hotstovejer on 2006-10-18
Thanks for the reply!

Tried that, and that didn't work. It's almost like the greeter is crashing. No errors, or anything to go off of. It's almost like I would have to reinstall gnome, which I think is stupid. There have been no updates to said machine, and all of a sudden, the login stops working.

Any other ideas?

---

### Post by kidders on 2006-10-19
_**No**_ updates?! And I'm guessing that you'd know if you tinkered with something that just happened to coincide with your logins failing, hehe. If that's the case, I can't help wondering if there's a hardware failure at work here. :???:

It's the "No errors, or anything to go off of" part that gets me though ... if something were crashing, wouldn't it show up as, say, a SIG 11 in your system logs? I might be jumping the gun here a little, but perhaps testing your RAM, fsck-ing your filesystems, temporarily "swapoff"-ing and trying again would be a worthwhile reassurance that nothing has broken.

You could also try doing a few things manually, like starting X yourself from the console, then starting the greeter, or your own gnome environment from another terminal, so that you could see exactly what was happening, and when. Your original post gave the impression that not all users might be affected by whatever's going on ... is that true?

Personally, I'd start with one more look through my system logs, then perhaps some manual messing like I suggested, followed by a few basic hardware tests. The answer *has* to be in there somewhere! I wonder if it's possible that someone has broken into your box and done something nasty, like exploit a buffer overflow to make your login sound effect crash X?

---

### Post by hotstovejer on 2006-10-19
Really don't think it's a hardware issue, cause I had the same issue on my laptop. Had to reinstall the entire OS to get that fixed, cause I couldn't figure out how to fix it. And I don't think it's a hack job, cause my girlfriend was able to log in after the machine sat there for a week, but then I came home from a business trip, did the updates, and rebooted for good measure, and viola, back to the same issue.

So what logs would hold any greeter errors?

---

### Post by headshrinker on 2006-10-19
I had similar problems when configuring my graphics card - if it was configured to use the wrong driver and/or screen resolution/refresh rate it did the same thing.

If this is the case with you, then the solution will probably be to correctly configure the file

/etc/X11/xorg.conf

If you look at this file and your a bit of a beginner on these sorts of matters then it will probably scare the crap out of you. Instead of manually editing this file, you can run

dpkg-reconfigure xserver-xorg

from the command line. This will take you through various questions regarding your system setup relating to graphics hardware, monitor, keyboard etc... It will try and auto detecy some things for you and gives directions on what you should enter. First time round, you'll need a bit of patience and it may take around 10 mins. When it's done, it will write out a new xorg.conf file for you (and it also backs up the old one).

Anyway, there are loads and loads of postings on the forum relating to issues with graphics cards, screen resolutions etc... If you type in "screen resolution problems" into the search box it will give you loads to look through - even though your problem isn't necessarily a screen resolution problem, the solution may be the same.

Hope this helps

---

### Post by hotstovejer on 2006-10-19
Actually, it isn't a xorg.conf problem. It was a gdm problem. I just ```
sudo aptitude purge gdm
sudo aptitude install gdm
```

And everything was kosher. So woohoo!

Yay for reconfiguring stuff!

---

### Post by runemaste644 on 2007-09-16
I did have that problem before. All that was wrong was my /home was full:-\"

---

