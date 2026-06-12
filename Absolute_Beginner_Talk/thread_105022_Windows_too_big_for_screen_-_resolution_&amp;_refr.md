---
title: "Windows too big for screen - resolution &amp; refresh rates"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by fizzybrain on 2005-12-17
I am really trying to love Ubuntu, but it's proving difficult (complete Linux newbie, but quite brave, technologically :) )

I know my monitor can do 1024x768 (other live Linux distros manage it).
SO I installed kubuntu, and ended up with a blank screen. I assumed it had just gone to sleep, so pressed a few keys - nothing. Then I remembered to do CTRL-ALT-F1 (,2,3,4,5,6) which showed up some very interesting screens but didn't tell me anything useful. Tried startx, etc, andgot SERVE ALREADY RUNNING-type messages. I assumed I had done something Bad by pressing random keys, so I re-installed (!).

Same again. I finally guessed that the X-login screen was there, but not being displayed. So I managed to edit the Xorg.conf file (I think I used the configure program), and took out the 1024x768 option, and restarted.
result - LOGIN SCREEN in 800x600 - HURRAH!

THE PROBLEM
-------------
 - can't actually use anything in 800x600 - all the OK buttons are too near the bottom of the windows, and the windows are too big! This seems ... well ... a bit stupid. Now I'm sure this sort of thing is configurable, but not by someone with my lack of knowledge.

SO - how do I tell X to run at 1024x768, but at a particular refresh rate (as the maximum refresh rate for 800x600 is different from the maxiumum refresh rate at 1024x768)?
OR - how do I get over the windows-too-big-for-the-screen problem (some sort of *real* virtual desktop, perhaps?

This is really starting to annoy me now, but -

I want to believe.

---

### Post by bscbrit on 2005-12-17
X will try to start at the first resolution on the Mode line of xorg.conf.  So, if the first entry is "1024x768", that is what it will do.  The other resolutions are also available but not opened by default.  
If you select the appropriate scan rates for 1024x768, I think that it should do what you expect.  Make sure that you back up your xorg.conf before you make any changes.  By the way, is it an LCD monitor or a CRT?  Although the initial installation might not have found the correct monitor by default, by setting it manually you can often get much better results.
I just discovered that I have never done this under Ubuntu but have done it with Mandrake, Fedora and Suse.  I will have to look through the menus to find a graphical interface to make this task easier!

---

### Post by GoldBuggie on 2005-12-17
try ```
sudo dpkg-reconfigure xserver-xorg
``` That will give you a ui that sets up xorg.conf.

---

### Post by bscbrit on 2005-12-18
Thanks - I was missing the obvious.  It was obviously time for me to have a break from the keyboard!

---

### Post by fizzybrain on 2005-12-18
Thanks for the info, but nothing helped - even wading through the results of doing
sudo dpkg-reconfigure xserver-xorg
 - I could not tie specific frequencies to resolutions (and couldn't create the 56Hz option which I know to be good)

Well, I gave up in the end, and used a dodgy 1024x768 monitor, only to find that the network setup system is broken anyway (won't go into administrator mode - a recognised bug, I now find)

I hate to say it but Windoze still wins in terms of take-it-out-of-the-box-and-switch-it-on, (partly) because:
- it defaults to the *lowest* available resolution
- you have proper control over screen resolutions and frequencies in the GUI
- (I think) you can run all the important boxes in 800x600 (though, IMHO it should be *possible* to run everything in 640x480, even it is by using virtual screens or scroll bars)

Now I am well above average as a computer user, and am well aware of all of M$ shortcomings (hence the desire to change), but we still have some way to go.

Still, I have always maintained that you can't complain about something you have got for nothing :) (but you can point out, comment on and discuss problems...;) )

Right, time to try (G)ubuntu, where I gather the network setup is not broken - though as I'm setting up a 233MHz PII I'll make sure I've got a book handy ... now where is that Tolstoy...?

Share and Enjoy

---

### Post by lila on 2005-12-18
Hello,
I'm also a newbie and nowhere near as computer literate as you seem to be, and I do have the same problem with the windows being too big and the clickable buttons too far down to reach.  I have all sorts of other problems to sort out first (apart from pre-holiday lack of time), and for the moment I'm working around it by right clicking on the window (or the top bar of it, usually) and using the "resize" option.  You then need to put your mouse straight to the bottom of the window and pull it up (sometimes it'll try to do a left-right adjustment first, just left click and repeat).  That way, you can work around the whole problem until you have time and inclination to sort it.  Bit annoying at times, but I've lived with worse problems...  Will get round to it eventually.  
Lila;)

---

### Post by bscbrit on 2005-12-18
fizzybrain

Just for my own interest, could you please tell me the make and model of the misbehaving monitor and, if you can get to it, any data from the manufacturer's label, usually on the rear of the case.

---

### Post by fizzybrain on 2005-12-18
(Of course, I should have said that I know a different DE might solve some of the problems)
Tried doing the resize thing with little success, but I'l maybe have another go in the future.
Re: make and model of the monitor - ha ha ha ha that's exactly the problem. the monitor(s) I have tried being "memorex telex" (!) - model CAM6383 (800x600 problem and colour distortion/magnetism at corners) and PMA1403 (working but eye-watering - horizontal hold is frigged at certain resolutions).  I couldn't find anything about the first one, and didn't try for the second. Ideally I will end up using the first one as the machine will be mostly unattanded.

Anyway, the good news is that Gnome is running much better than I had feared, and all the dialog boxes seem smaller; and, more importantly, all the signs are that I will be able to configure it properly.

So, smiles have returned! Time to get on with the rest of my life, getting a job, etc....

---

### Post by bscbrit on 2005-12-18
OK, if you think that you are going to stay with gnome, and that everything appears to work well, I will not do too much work on this.  But I am curious as to why it wouldn't install cleanly with kubuntu. Enjoy ubuntu!

---

