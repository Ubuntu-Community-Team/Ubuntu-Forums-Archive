---
title: "Removed Ubuntu, installed XP, boottime is &gt;10 minutes."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by ap3rtis on 2007-04-21
Hey all,
I had to install windows on a friend's laptop, so I loaded up the windows xp cd, and deleted the linux partition (was on the whole harddrive). Then formatted the harddrive and installed windows. Now anytime I go past the BIOS screen, I get the loading bar (white and black along the bottom of the screen), which my friend says was part of ubuntu, but I can't remember exactly. But this takes about 10 minutes to load, and then finally the xp loading screen shows up. I've run fixmbr and fixboot and no luck there. Any ideas?

Thanks.

---

### Post by n3tfury on 2007-04-21
you SURE there are no other partitions?  get the gparted live CD and take a look at the partitions using that instead.

---

### Post by Tundro Walker on 2007-04-21
Please provide more info...

Which version of Windows did you install?

On the "white bar" screen, what does it look like, in detail.  "a white bar" is pretty vague, because I'm booting Ubuntu, and it shows the Ubuntu splash and an orange bar as the OS loads.  Then goes to a GNOME or KDE or XFCE splash as the desktop loads.  In Windows, they sometimes had a white ASCII block bar on the bottom that filled in solid white as Windows loaded.  Is that what you see?

After loading Windows, did you tweak it?  WinXP is like Ubuntu when it's first installed...it's setup in "swiss army knife" mode with lots of things turned on.  You need to go in and tweak the services to only what you need.  After that, should boot up faster and run smoother.

EDIT: 

How's that for support...not only are we supporting Ubuntu issues in these forums, but Windows, too!  LOL!   Ubuntu really is "humanity towards others".

I'd like to hear about the support someone gets in the Microsoft Windows forums if they post about dual-booting with Ubuntu/Linux, and asking for help with their Ubuntu install.  I've got $5 saying the response you get is comedic gold!  In fact, we could start a whole other post just debating what kind of response someone would get.

---

### Post by ap3rtis on 2007-04-21
Actually there is another partition, it's 25 GB, he was going to use it to reinstall linux, then we used 70 GB for XP Home. It's possible the windows install is screwed up, since he decided to shutdown the computer during install because it was taking so long lol. Yes Windows install is painful, ubuntu is so much nicer in that regard. Maybe I will download xp pro from msdnaa and try that again. I think the bar is part of windows actually, don't know what my friend was thinking. the load time is atrocious then. reinstall likely required :( unless anyone has any other ideas.

---

### Post by MiCovran on 2007-04-21
> **ap3rtis said:**
> Hey all,
I had to install windows on a friend's laptop, so I loaded up the windows xp cd, and deleted the linux partition (was on the whole harddrive). Then formatted the harddrive and installed windows. Now anytime I go past the BIOS screen, I get the loading bar (white and black along the bottom of the screen), which my friend says was part of ubuntu, but I can't remember exactly. But this takes about 10 minutes to load, and then finally the xp loading screen shows up. I've run fixmbr and fixboot and no luck there. Any ideas?

Thanks.
About this "loading bar" you described, it's windows' thing, not ubuntu's. Ununtu doesn't use this kind of bars at bottom of the screen.

Maybe windows aren't installed properly? Try to reinstall again.

---

### Post by oilchangeguy on 2007-04-21
tundro walker i'm not sure where you came up with this, quote: After loading Windows, did you tweak it? WinXP is like Ubuntu when it's first installed...it's setup in "swiss army knife" mode with lots of things turned on. You need to go in and tweak the services to only what you need. After that, should boot up faster and run smoother.
because you couldn't be more wrong. a fresh install of any os will load and run fast simply because nothing has been added yet to cause it to run slow. i'm not sure how the user loaded windows, i'd say it was not done correctly. but since we can't see the computer it'll be hard to say just what was done wrong. but it's not because of any need to tweak anything.

---

### Post by ap3rtis on 2007-04-21
I checked the event's, it says there are some bad blocks on the harddrive, so I'm going to run disc error checking. it says I have to reboot before I can do that, which means another long boot time. yay! I did defrag though, and there were files all at different ends of the harddrive, so hopefully that helps.

---

### Post by Pobega on 2007-04-21
I'd reformat the whole drive if I were you; It'd be the quickest fix to this problem. Then reinstall Windows and you should be fine.

I sound like Dell Support now :)

---

### Post by ap3rtis on 2007-04-21
haha, well it is a dell laptop :p 
Well the boot time was instant now, must've been the defrag that fixed it. Definitely was a windows problem, but it was a pretty sketchy install (shut down during install/format a couple of times). thanks guys, this forum is great!

---

### Post by oilchangeguy on 2007-04-21
sounds like you may need to invest in a new hard drive. you can try this with your windows cd.is it a true windows cd, or a factory restore cd? this will only work with a windows cd. follow the prompts to load the repair console. from the command prompt type chkdsk. and i belive the correct command to attempt to preform a repair is chkdsk /r but try the chkdsk first.

glad to see you got if fixed!

---

