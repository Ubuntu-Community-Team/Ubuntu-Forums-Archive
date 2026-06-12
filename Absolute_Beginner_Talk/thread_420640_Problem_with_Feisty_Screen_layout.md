---
title: "Problem with Feisty Screen layout"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Baasha on 2007-04-23
I just upgraded to Feisty a couple of days ago.  Everything was fine.  Then today when I logged on I have a problem with all my application windows.

Every application boots up with the window at less than full maximized size.  The Title bars are missing, the menu bars are the highest thing in the window.  This means that I can not shut down the application by clicking the "x" in the top right hand corner, I can not click on the Title bar to move the window around the screen, and I can not click in the top left corner to maximize the window.  The other strange thing that is happening is that application tabs no longer appear in the status bar at the bottom of the screen.  If I want to switch applications I have the close the foremost window using the file menu.

How do I correct this problem?

---

### Post by gustavo77ut on 2007-04-23
Hey, Baasha,

Are you able to get to a terminal window?  

I really don't know how to fix which XSession you log into, other than possibly change it at the login screen itself.  Check and make sure, at login, that you have Gnome selected as the session manager.

If you're starting from terminal, you might try using gdmgreeter (as I believe it's called).  I wish I could give you more.  I'm pretty new myself, so I don't know how to edit all the stuff for `startx` quite yet.

Gustavo

---

### Post by Jhodytropical on 2007-04-24
> **Baasha said:**
> I just upgraded to Feisty a couple of days ago.  Everything was fine.  Then today when I logged on I have a problem with all my application windows.

Every application boots up with the window at less than full maximized size.  The Title bars are missing, the menu bars are the highest thing in the window.  This means that I can not shut down the application by clicking the "x" in the top right hand corner, I can not click on the Title bar to move the window around the screen, and I can not click in the top left corner to maximize the window.  The other strange thing that is happening is that application tabs no longer appear in the status bar at the bottom of the screen.  If I want to switch applications I have the close the foremost window using the file menu.

How do I correct this problem?

I Have the same problem after rebooting the machine I can't move my windows and I don't have the x or Minimize or Maximize. Anyone ?

---

### Post by Twiggy003 on 2007-04-24
I have the same problem by the looks of it, applications dont have title bars, it wont minimize or show the active windows in the menu bar.  any ideas why this is?

---

### Post by gustavo77ut on 2007-04-26
Well, I was wondering if any of your desktops look like some of these screenshots:

[http://fluxbox.sourceforge.net/screenshots.php]("http://fluxbox.sourceforge.net/screenshots.php")

Or one of these desktop environment -slash- window managers:

[http://xwinman.org/]("http://xwinman.org/")

OK.  So that's a base-line, since I don't know a lot of Linux Windows Managers (WMs), and all of my experience has been since nice KDE and Gnome stuff has been available to gawk at.

I hope this helps, since identifying something like a WM might help.  Otherwise, I'm wondering what graphics cards you have...  Maybe one of the drivers reverted to the Open drivers instead of the proprietary ones.

Cheers,
Gustavo


*** off-topic ***

I wonder why Ubuntu sends me only the first of the replies...  Is that to be nicer to the mail server(s), or simply 
a courtesy.  I'm guessing the latter.

---

### Post by gustavo77ut on 2007-04-26
Better yet, one simple question:

Does your desktop still look anything like Gnome or KDE?

---

### Post by Twiggy003 on 2007-04-27
Its a GNOME  desktop.  As a temporary solution ive made 'metacity' a auto start application which gives me my desktop back the way it was.  but it isnt really knowing what the actual problem is.  i have a ATI radeon 9200, but ive used Ubuntu a fair bit before and its been fine, and it was a few weeks into using Ubuntu Fawn before it suddenly did this.

---

### Post by Gina on 2007-04-27
Could it be anything you've installed recently?  It sounds like it's been using an alternative Windows Manager.  Since its OK with Metacity (the Gnome WM) it doesn't sound like your standard Gnome WM (metacity) has been corrupted.

---

### Post by freebird54 on 2007-04-27
Sounds like a misconfigured "desktop effects' problem to me.  The metacity fix should work for all if that is the case.  A proper fix depends on knowing a LOT more about the individual configurations.... (what you TRIED to have setup, and on what vid card etc)

Did this start for any of you after a kernel upgrade? from -14 to -15 for instance?

---

### Post by Twiggy003 on 2007-04-27
That's what I thought it may be, as that's the only thing that's different, the fact ive installed stuff, but i can't think what would mess up my desktop.

---

### Post by Twiggy003 on 2007-04-27
I dont think so.  Can i get rid of Compiz/Desktop effects? i dont have them enabled but i did at one point.  can i get rid of it entirely?

---

### Post by wog on 2007-04-27
Sounds like the problems I had when I turned on Desktop Effects.

Check at System -> Preferences -> Desktop Effects and see if the check-boxes below the "Enable Desktop Effects" button are outlined in black instead of gray. If so, you just need to click the button to turn off the effects and get your title bars back.

I hope that helps you.

---

### Post by Twiggy003 on 2007-04-27
Thanks, Yes it is all turned off, is there a way to actually uninstall them completely? or are they part of ubuntu-desktop?

---

### Post by wog on 2007-04-27
All I know is Desktop Effects was there when I installed. I suspect there's a way to remove it, but I'm not yet knowledgable enough to know how you could remove it without messing something else up. Sorry. :(

My current solution: don't touch it. :)

---

### Post by Twiggy003 on 2007-04-27
:), alright thanks for trying anyhow.  Well, at least it still works with the metacity on auto started applications.

thanks anywho

---

### Post by freebird54 on 2007-04-27
My current solution differs a little bit - I installed Beryl and Beryl-manager, and then I can choose which WM is active (Beryl, Compiz, or Metacity).  Beryl and Metacity work at the moment - Compiz broke along with the -15 upgrade...

---

### Post by Twiggy003 on 2007-04-27
Ok thanks, i'll give that a go. if all else fails i can just get rid of Beryl and go back to the ol' method.

---

### Post by firfin on 2007-04-27
Same problem. I read in [this thread]("http://ubuntuforums.org/showthread.php?p=2544883#post2544883") that deleting the session might help. 
but then, I also just installed gdesklets (using synaptic), maybe that could be the problem?

Where can I find more info on WHY the WindowManager doesn't start?

---

### Post by Twiggy003 on 2007-04-27
I don't know, ive got gdesklets also, installed through Automatix2, i could give that an uninstall, never really used them. ive tried deleting/renaming that session file before, and i didnt get any luck from doing so.

---

### Post by firfin on 2007-04-27
> **Twiggy003 said:**
> I don't know, ive got gdesklets also, installed through Automatix2, i could give that an uninstall, never really used them. ive tried deleting/renaming that session file before, and i didnt get any luck from doing so.
Hmm, that's a shame. It appears to have the trick for me. Rebooted a couple of times to check but after removal of the session file everything seems fine. I still wonder what caused the problems though.

I installed gdesklets using synaptic btw, not with automatix so maybe it will make a diference for you. I just mentioned it because it was the last thing I can remember changing. It seems to be working fine now btw.

Something must have gone wrong with the session or something.

---

### Post by gustavo77ut on 2007-04-28
Hey, Baasha and everyone,

I don't know if I could have gotten screenshots, but I was able to duplicate this problem in Fiesty, on my box.

It's easy to duplicate, all you need is for /etc/X11/xorg.conf to be setup to use the wrong driver.  The box I'm working on has an NVidia GeForce 6800 (?) in it, but trying to get the "restricted" nvidia drivers to work with/for Beryl pooched my Desktop to where Metacity was showing nothing for the panes or theme (such as the Title Bar with minimize, close and maximize).

When the nvidia driver installs, it does some automatic settings for xorg.conf and makes a backup called /etc/X11/xorg.conf.backup.  

A couple of times, I had to do `apptitude install xserver-xorg-video-nv` because I uninstalled it for troubleshooting.

I'd be happy to share the broken and fixed xorg.conf sections and attach the files, if anyone is interested.

--Gustavo

---

### Post by freebird54 on 2007-04-28
Knowledge never hurts!  Post the broken/fixed versions by all means.  I wonder if we should have a repository of working xorg.conf files for each card type we've run into online somewhere...  Beginner Team??

---

### Post by gustavo77ut on 2007-04-29
Thanks for the tip.

Here are the files, labeled appropriately with the easy-to-read dash format common to LISP, Scheme and the like (but it's just the filenames, not file content, that mimics Scheme, imho).

Hopefully this helps.  Shortly, I'll also post a version that works with VMware, but all these settings do is make it so my xorg nvidia driver (see "nv" in synaptic search).  Of course the broken one was the nVidia driver's attempt to work.  

But the reason why the "broken" file didn't work is because I don't have the right version of xserver-xorg-core installed.  It's looking for `>=1:0.99.0-1`, and I have something less (can't remember the numbers).

Oh.  And the break only occurred (where I saw the windows do some of really goofy things described by Baasha and others--head of list) when I tried to run Beryl or Beryl Manager (beryl and beryl-manager, respectively).

NO WARRANTY implied and blah, blah, blah. See GPL.

Gustavo

P.S.  I'm not sure what the "about-working" file is all about, but I remember it was the last version I was working on before xorg.conf (there's like 20 "backups" done using ""<filename>`date -u +%F`-01"").  Does that make sense?  Point being, I'm not sure what's in there, but maybe with a diff, it might prove useful to someone else.

---

### Post by gustavo77ut on 2007-04-29
BTW:  My graphics card is an nVidia GeForce 7600gt sold by EVA, or something like that.

---

