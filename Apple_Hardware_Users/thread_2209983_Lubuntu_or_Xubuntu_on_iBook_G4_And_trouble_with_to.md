---
title: "Lubuntu or Xubuntu on iBook G4? And trouble with touchpad"
date: 2014-03-08
forum: Apple Hardware Users
---

### Post by bgriffinn on 2014-03-08
Hello. I'm new here and to Linux; I hope I've chosen the right forum.

A couple of days ago, Google decided that with OS X 10.4.11 (iBook G4 PPC), not being able to update Firefox or run Chrome, I might as well be banned. I can't load any Google-related pages or watch videos on Youtube (the YT website does load). At first, google.com gave me a page asking me to download Chrome (even though I couldn't and it knew I couldn't). Now the browser just loads a blank or nothing at all. I tried TenFourFox but nothing. 

I didn't think there was any update or workaround on OS X I could try (**I know it's off-topic, but I wouldn't mind if you told me different**). I'd never tried Linux (on pc or Mac) but the only thing that came to mind was that if I installed Linux on a partition I could solve my problem. I can do all I want on OS X 10.4.11, and Lubuntu (see below) is comparatively rudimentary (at least for me), so I meant to use Linux only for surfing the web (especially accessing Gmail and getting Youtube videos to run).

My Mac is as follows:

iBook G4
PowerPC G4 933 MHz
1.12 GB DDR SDRAM (I expanded it myself some time ago)
HD 160 GB

Ubuntu itself seemed out of the question. Xubuntu doesn't seem to be available for PowerPC in a nice ISO file, so for the moment I decided to download Lubuntu, burn it on a cd and try it live (I didn't even know it was possible).

Now I can indeed load Google and watch Youtube videos on Lubuntu, but I have three or four problems. For the moment, I'd be happy if I could solve this one:


[LIST]
[*]**my touchpad** (or trackpad&#8212;the in-built thing below the space bar) **does work for dragging the cursor, but I can't click on it (left- or right-click)**. I haven't found any specific threads dealing with this: either the pad is not recognized or the trouble is only right-clicking. My problem is different. 
[/LIST]

I can click with the button below the pad, but I shouldn't because of a hardware issue: if I click enough times, the cursor starts jumping around (the iBook is obviously old). A mouse works, and *sometimes* ctrl+F11 works, but I'd like to be able to click on the pad. I don't see how I could retrieve the driver for the touchpad, for instance, and Lubuntu doesn't seem to have a "touchpad panel" in the preferences.


[LIST]
[*]**Secondly, given the above specs of my IBook G4, if I did decide to make a small Linux partition, would it be worth it to go for Xubuntu rather than Lubuntu?** Would it run smoothly, and with no crashes (I think, for instance, that OS X 10.4 runs well enough on my machine), and **would I have a relatively easier time?** 
[/LIST]

Also, how big should the partition be? I know the minimum requirements: I'd like to leave Xubuntu/Lubuntu enough space to run well without stealing unnecessary space from OS X 10.4, which is rather more demanding and which is where I have my media and such.

I've run on a bit, but I thought I should make myself clear. Again, I hope I'm in the right forum. I'll be grateful to anyone who can help me.

bgriffinn

---

### Post by bgriffinn on 2014-03-08
I feel more than a little silly and apologize. I remembered that there was such a thing as Safari. I'd snubbed it for years and didn't have it in the dock. I was dissatisfied with it and took it for granted that a years-old Safari couldn't do what Firefox or TenFourFox couldn't do. I just found out it does open Google and Youtube works fine (not perfectly, but no worse than on the latest Firefox that OS X 10.4.11 can run).

**My question, though, still stands**. I'd like to be able to switch to a light OS especially for the Internet. It is not urgent, obviously, but it would be useful to me and others for future reference. Besides, I suppose at some point loading pages with my Safari 4.1.3 will become unbearably slow.

Again, I apologize.

bgriffinn

---

### Post by bgriffinn on 2014-03-09
Nope. I suppose Google has noticed that I've been logging into my usual e-mail account from Safari and now I have the same problem with Safari: I can't load Google or any Google-related page.

By the way, in case anyone is able to help me, if I installed Lubuntu on a partition of my iBook instead of trying it live, I was wondering whether it might behave better or is this exactly what I'd get (except that of course now it's slower)?

---

### Post by bgriffinn on 2014-03-10
It may well be that my problem is a hard one to solve, or one that is too specific to my case, but is there a way I could improve my chances to get help? I've done my homework as far as I could, though I'm not very knowledgeable and most documentation was over my head. I could provide more details if you ask me.

I've found a few ways to get one's touchpad recognized if it doesn't work at all, or to enable right-clicking, but no-one with my problem, which is this:

> **my touchpad** (or trackpad—the in-built thing below the space bar) **does work for dragging the cursor, but I can't click on it (left- or right-click)**. I haven't found any specific threads dealing with this: either the pad is not recognized or the trouble is only right-clicking. My problem is different.

I'll be grateful to any one who can spare the time and help me, or perhaps just tell me that I'm not likely to get rid of this problem. Using a mouse all the time is not the end of the world.

bgriffinn

---

### Post by rsavage on 2014-03-10
Replying to you in the hope that through karma somebody will reply to my messages....


Trackpad command is covered here [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_control_trackpad_and_right-click_behaviour.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_control_trackpad_and_right-click_behaviour.3F)

Pretty sure powerprefs has an option for this, certainly pbbuttonsd does ([http://pbbuttons.berlios.de/projects/pbbuttonsd/man-pbbuttonsd.html](http://pbbuttons.berlios.de/projects/pbbuttonsd/man-pbbuttonsd.html) and [http://pbbuttons.berlios.de/projects/pbbuttonsd/man-pbbuttonsd.cnf.html](http://pbbuttons.berlios.de/projects/pbbuttonsd/man-pbbuttonsd.cnf.html) ) if you want to set it up on startup so that you don't have to keep entering the command.  An alternative approach is described here [http://ppcluddite.blogspot.co.uk/2012/03/installing-debian-linux-on-ppc-part-iv.html#trackpad](http://ppcluddite.blogspot.co.uk/2012/03/installing-debian-linux-on-ppc-part-iv.html#trackpad)

---

### Post by bgriffinn on 2014-03-11
> **rsavage said:**
> Replying to you in the hope that through karma somebody will reply to my messages....


Trackpad command is covered here [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_control_trackpad_and_right-click_behaviour.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_control_trackpad_and_right-click_behaviour.3F)


Linux is still so recondite to me that it took me a while to realize that karma is not some command-line utility...

Luckily, my trackpad turned out to be ADB, so now I'm at least satisfied that **tapping can be easily enabled. I'll go for Lubuntu**, then. Xubuntu doesn't seem to have many advocates: it's not as nice as Ubuntu, apparently not nearly as light as Lubuntu. Besides, I will still have OS X 10.4.11 when I need nice.

Thank you very much.

bgriffinn

---

