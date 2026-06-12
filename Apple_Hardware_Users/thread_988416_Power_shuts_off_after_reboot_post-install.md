---
title: "Power shuts off after reboot post-install"
date: 2008-11-20
forum: Apple Hardware Users
---

### Post by lemonbar on 2008-11-20
After my ten millionth attempt at installing Ubuntu of various flavors on my [blueberry - fruit colors]("http://www.everymac.com/systems/apple/imac/stats/imac_dv_400.html") (crammed with 640MB RAM for extra speedy goodness), wiping the hard drive, reformatting, PRAM-ming, re-adjusting the xorg.conf, having a day where every repository was coming up "not found," I have finally gotten Intrepid on the dang thing - sorta.  I need to edit my xorg.conf, but I can't get a flippin' command line.  After last night's installation. I got a blank screen after reboot, and then the power shut off (but the little green power light was still on).  This happened after the second stage boot.  

I tried "Control-Option-F1" repeatedly after second stage, but it just clicked off.  This has happened pretty consistently after several installation attempts with Hardy and Intrepid.  I know now that I need to build a "Modules" section in my xorg, but I am sort of new to all this.  What do I do (in noob language - I'm a cave woman.  I have fire, but only when lightning strikes a tree).  Do I have to start all over?  I've already got the information in the computer - I don't want to start all over if I can just get in my xorg and tap out a couple of instructions.

---

### Post by tiresia on 2008-11-20
After installing Ubuntu and restarting the computer, do you get the yaboot prompt?

---

### Post by lemonbar on 2008-11-21
Yes.  I hit TAB, and it gives me the option of "Linux" and "old."  "Old" does nothing, and "Linux" gives me a white screen, some code, a black screen, "Loading..." and then I hear a click and everything goes dark.  The power light stays on, but nothing else happens.

---

### Post by tiresia on 2008-11-21
Have you tried giving 'Linux video=ofonly'?

---

### Post by stream303 on 2008-11-21
As a first-time install, I might suggest an older version which still gets updates, such as Dapper 6.06x.  Although you'll still need to apply some tricks to get it up and running, you'll get a very valuable working xorg.conf and yaboot.conf for reference later on if/when you want to upgrade.

If the screen is still black when you load dapper, you can use the now-deprecated utility at the commandline  (CTRL-ALT-F2) and pick your video card etc.

```
sudo dpkg-reconfigure xserver-xorg
or
sudo dpkg-reconfigure -phigh xserver-xorg
```

(NOTE: This utility does not work in recent releases, although it will provide a skeletonized version of xorg.conf)

If for some reason the monitor is still shutting down with Dapper, you'll have to reboot the install cd into rescue-mode, drop into a root shell, and do some vi editing to the xorg.conf and possibility of yaboot.conf as well with the values shown in the faqs and threads.  This may prove too frustrating, so judge your tolerance level.

---

### Post by lemonbar on 2008-11-21
Thank you both for your help - at this point I have tried so many combinations of things with so many installs that I can't remember what I have and haven't done. My determination is stronger than my tolerance level, so I will get some form of Ubuntu running.  When I had Edgy, I couldn't get synaptic to work, so I'll try Dapper again if I don't get Intrepid going.

I actually had a decent xorg file in Intrepid this time, it just didn't have a modules section - that's why I didn't want to go back and start over.  I think if I were able to disable the dri and glx all would be fine and dandy.

I'm at work right now, so it might be awhile before I can try out everything - let me know if you have any more ideas.  I love Ubuntu on my pc, so I know it's worth the trouble;).

---

### Post by lemonbar on 2008-11-22
> **tiresia said:**
> Have you tried giving 'Linux video=ofonly'?

Woohoo!!!!!!!!

I got it started in low graphics mode immediately!  Itworkeditworkeditworkeditworked!:guitar:

Thanks so much - I feel a little less primitive now;)

---

### Post by lemonbar on 2008-11-22
...except I can't seem to get it to do anything useful, and I'm sleepy.  I have a low graphic desktop, and when I get a command line (terminal doesn't work, Firefox doesn't either) and edit the xorg (using stream303's template, modified for my specs), I get various error messages.  I'm probably messing with things I don't understand:). I'll get  back to this when I've had some sleep. If this comes off like I'm discouraged, I'm not at all.  I like that I get pictures and sound at least.  Thanks!

---

### Post by stream303 on 2008-11-22
That's great!  Let us know if you eventually get out of low-graphics mode.  You've definitely got the right attitude - keep it fun.  When it does fire up normally, I **guarantee** you'll be jumping around the room.  It's one of those "gotta be there" moments. :)

BTW, the problems you were seeing with the repos is that for some, especially with upgrades, is that the update repos were taken off the main mirrors, and reside solely on specific ports mirrors - thus another file to manually edit.

The change is noted on Ubuntu's release notes page for Hardy about half-way down:

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

BUT, some still have trouble when changing from archive.ubuntu.com to ports.ubuntu.com **unless they add a trailing slash!**

For example, the syntax as shown for corrected entries looks something like this:

```
deb http://ports.ubuntu.com/ubuntu-ports hardy main restricted
deb http://ports.ubuntu.com/ubuntu-ports hardy-security main restricted
```

However, it does not contain the trailing slash, so I would advise adding one if they are not present and one is having update difficulties:

```
deb http://ports.ubuntu.com/ubuntu-ports/ hardy main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security main restricted
```

Be sure there is at least one space after the trailing slash.  And, be sure to update it:

```
sudo apt-get update
```

I haven't had to do this with normal install of Hardy or Intrepid lately, so this should be already taken care of if you look at /etc/apt/sources.list

---

### Post by lemonbar on 2008-11-22
> **stream303 said:**
> That's great!  Let us know if you eventually get out of low-graphics mode.  You've definitely got the right attitude - keep it fun.  When it does fire up normally, I **guarantee** you'll be jumping around the room.  It's one of those "gotta be there" moments. :)

I wanna be there!

My xorg situation is driving me nuts - I can't get anything to happen in low graphics - no internet, no terminal (unless I ctrl-alt-f1), not even Gnometris or mahjongg!  I get error messages after booting "Linux video=ofonly"  - no driver, which I correct, and then "screens found but none in usable configuration" or whatever (I'm on my break at work, so this is totally from memory - forgive the casual coding).  I've built a module disabling glx and dri, changed my refresh rates, torn out my hair, banged my head on the keyboard - all the stuff I'm s'posed to do.  I'll get back later when I know what I'm messing up in more detail;)

---

### Post by stream303 on 2008-11-23
Well, which one of your G3 machines are we talking about? :)

And what version of Ubuntu are you trying to get to run?

Perhaps you can post the xorg.conf file that you are working with and maybe we can see something you might be missing..

---

### Post by lemonbar on 2008-11-24
This is the Fruit flavored blueberry, and I was working with Intrepid.  I'll post my xorg later, but I think I might start over again with Dapper and then try upgrading from there after changing the source lists.  I'm not messing with it today - too sleepy.

---

### Post by stream303 on 2008-11-24
> **lemonbar said:**
> I'm not messing with it today - too sleepy.

What? That's the best time for me to accidentally wipe out my OSX partition, or mess up my yaboot.conf so bad that nothing boots anymore.  Then you discover that you have to be at work in 4 hours, but you're so wound up you can't sleep. :)  (kids, don't let this happen to you!)

Seriously, sleep sounds like a good move to me too.

---

