---
title: "Averatec Widescreen Problem in 7.04"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by tmoore4748 on 2008-02-16
As I know it's been addressed at least a hundred times, I won't restate much in this post.  I've tried all the little tricks that I could find to solve my problem, which is this: my screen resolution doesn't work right.  Basically, everything is squished.  Imagine watching a regular movie on a widescreen TV, where the characters on the TV appear shorter or fatter.  This is the problem I'm experiencing.

My laptop is an Averatec 1100, and it has the intel Integrated graphics chipset 855GM.

I've tried everything, and I mean, everything, to solve the problem.  Here's a list of all the stuff I've tried that I could think of:

915resolution
changing the xorg.conf file
remapping resolution
reverting to old stuff and trying to get the new intel driver to work

There's got to be at least one or two other solutions that I've tried that aren't up there, I just can't remember them.

I'm completely new to this whole process, and I'm also completely dumbfounded.  I'm a system administrator for Windows systems, and have been for almost eight years now, so it's hard to break out of those molds.  It's like teaching an old dog new tricks, and I'm exceedingly old.  If it needs to be said, I think I'm going to need someone to hold my hand through this, as I don't have the slightest clue what to do.  Nothing works.

Several times, the x server has crashed, forcing me to reconfigure conf files back to the way they were through using the setup disk and the terminal to get to gedit, on top of an unusual display problem I had with the intel driver, which displayed only to top left quadrant of the screen very poorly (it looked like 640x480 on 8 bit, zoomed in, even though it was supposed to be 1280 by 768, a resolution suggested by 915resolution).

One problem I saw was that someone was trying to assign a resolution that wasn't identified in their BIOS, however, looking through mine, there isn't a single setting for any video adapters, so I don't know what the native resolution should be in my case, only that it be a widescreen format on a 10.1 inch screen.  Any help would be appreciated.

---

### Post by jan quark on 2008-02-16
try to reconfigure the xserver manuall

run this

and answer the questions
perhaps it works
```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tmoore4748 on 2008-02-16
I tried to reconfigure the xserver manually, just like you said, and picked a resolution and refrest rate that I thought would work.  It didn't.  I was left with that peculiar left upper quadrant screen, and had to guess my way over to the screen resolution menu option under GNOME, and tried every resolution on the option menu.  Each time I did, the computer seemed to have had the xserver crash, and started back to the login page.  I'm going to try to do the xserver manual configure again, this time picking a different resolution and frequency, in the hope that it works.  I'll write back when I'm done.

---

### Post by tmoore4748 on 2008-02-16
In an unusual side note: in order to get to the command prompt, I've been going in under the recovery mode (can't get to Terminal if you can't read the thing).  One thing I noticed was that, during the boot-up, the string of text you see executing various commands and scripts during startup changes from on type of text to another.  Is this normal?

---

### Post by tmoore4748 on 2008-02-16
OK, no dice on the xserver reconfiguration.  I'm going to reinstall Feisty, and then do the reconfigure manually, soo if I can correct any errors left behind from previous attempts, and get this fixed.

If anyone has any ideas, please don't hesitate to post, I'm right here, reloading the post page repeatedly in the hope of divine intervention.  I'm way out of my depth here, which is unusual for me, and I'm willing to accept any help, no matter how off-the-wall it seems.  I'll report back again when I'm done with the reload and reconfig.

---

### Post by nittanylion on 2008-02-16
Sorry for the confusion, but you have tried using modelines for your monitor? I perpetually had problems using my native resolution until I stuck the appropriate modelines in my xorg.conf file. I couldn't find any for your monitor in a cursory search, but this post had a good suggestion: [http://ubuntuforums.org/showthread.php?p=1465348#post1465348]("http://ubuntuforums.org/showthread.php?p=1465348#post1465348")

If you do attempt the above suggestion, please backup your xorg.conf file first!

---

### Post by tmoore4748 on 2008-02-16
As far as the above solution, I'm not even capable of attempting it.  This kind of this is way above my experience level, and I don't feel confident in pulling off anything like this.  I'm almost done with the reinstall, I'm about to do the reconfig.  I'll letcha know.

---

### Post by tmoore4748 on 2008-02-16
OK, boils and ghouls, I think I've got it.

There was a solution similar to mine, as well as a little of what was suggested to me through this post, so here's a quick recap of what I just did:

I reconfigured the xorg.conf file through the terminal, making sure to use the vesa driver (someone I found on a different forum has the exact same laptop as mine, and used the same solution, with a twist; while their solution was temporary, it appears mine is permanent).  After I picked the driver, I went through all of the mouse and keyboard stuff, picked my video resolutions (of the myriad ones listed, I only chose five), the restarted the xserver configuration.

I never got the chance to try the i810 driver (it was reported to me a one-time-only fix, and with several crashes afterwards, so I stayed away from it), and instinct told me to stay away from the intel driver as well (too many people reporting problems, even though there were many fixes using it).

Once I shut the xserver down (ctrl-atl-backspace), I restarted the computer, and Ubuntu started in a perfect graphics resolution that I needed (1280x768 @ 61Hz), without any serious text editing on my part.  It seems that, after choosing the expert way of handling the monitor detection (the Expert mode, that is), everything worked fine, whereas previously I had only chosen either simple or intermediate skill levels.  My choice had to do with the fact that, for the most part, I don't have the slightest idea what I've just done, let alone can I tell you what it is I was doing, or what the files were that I edited.  The only thing I can say is what my problem was, and what actions were taken to fix that problem.

Special thanks are in order for Jan Quark: your simple post was too easy for me to understand at first.  Basically, with an engineer (that's my trade of choice), we tend to make things more difficult than they need to be.  Thus, I read too deep into your solution, Jan, and now feel like a total and complete idiot.  Simplicity is better, I suppose, when you actually expect it.  While I might not understand the concept or purpose of what I did to my computer, I can say this: I learned how to think in a patient manner again.  Frustrating as it may have seemed in the beginning, it's not so much any more.

Long-winded though I am, again, thanks Jan for your divine intervention.

---

### Post by jaygo on 2008-02-22
For future reference, you can get to a terminal without having to reboot by hitting CTRL + ALT + F1 (f2,f3 .... f6 will all work as well). Your graphical session, X, will be on F7 and you can switch back and forth. It makes it easy(er) to edit your settings then switch to GUI and restart X to test them.

---

