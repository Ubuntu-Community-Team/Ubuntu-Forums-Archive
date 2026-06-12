---
title: "[SOLVED] Need Help With Full Screen Video"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by jivabill on 2008-01-25
When I had XP on this machine I could watch YouTube Pink Floyd videos and have total full screen no problem.

Now I am running Ubuntu 7.10, when I try to watch the save videos I get about 2/3 screen the rest is black background.  The edges of the video picture are not straight either.

I found a thread that said the solution was to download and install Flash Player 9, AFTER removing the flashplayer plugin from Firefox.

So my prolem, I am not well versed in LInux.

I don't know how to remove or even find the flash plugin from FireFox.
I tried to find the mozilla files so that I could put the downloaded flashplayer 9 parts in there but I don't understand enough about how those are organized to know what to replace or put where..  My instinct re computers is not to mess with it or I'll screw up my installation.

If anyone has patience to help on this I would appreciate any suggestions.
Thanks
Bill

---

### Post by raul_ on 2008-01-25
Use synaptic and search for flash.

Then remove tha package you want.

---

### Post by jivabill on 2008-01-26
Hi Raul, Thank you for the good idea.  I should have thought of that approach myself.  I'll give it a shot.
Regards
Bill

---

### Post by bwtranch on 2008-01-26
You could try gnash. it is an alternative to flash. and it's open source:)

---

### Post by nowshining on 2008-01-26
have u tried also disabling compiz right -  click change background on the desktop and go to the last tab and choose the first option.

---

### Post by jivabill on 2008-01-27
Hi Nowshining, thank you for the good idea.  Tried it out just now.  Went to the change desktop and the far right tab and what I found is the "simple" desktop enviornment was already enabled.  When I tried to enable the "normal" one the system said it could not enable that environment.

So I gess I am back to removing the existing flash package and installing the flash player 9 fix that I found in another thread.  We will see I recon :-).
bill

---

### Post by jivabill on 2008-01-27
Well, I used Add/Remove programs to remove the Macromedia Flash plugin.  Then I installed the debian flash player 9 update that is supposed to tune up flash.  All went well.  Went to Google Video and looked up Pink Floyd and played a video for a bit.  Same thing as before.  I do not get true full screen.  I get a window the size of the screen, task bar at top and the desktop bars at the bottom.  And the image did not fill the screen, it was about 2/3 of the screen or rather 2/3 of the window.

When I was watching this video using XP I got full screen right to the edges and the image filled the screen.  Which is what I would like to get with Ubuntu.  I imagine it can be done, but so far it eludes me.

I would have been back sooner but, well, I have a hard time turning off Pink Floyd. :guitar:

bill

---

### Post by nowshining on 2008-01-27
sorry then i'm out of ideas, :/ that may work this moment, i don't what else to ask u to try out..u'll have to wait for further input from others - so my post here will bump it up :)

---

### Post by Incense on 2008-01-27
You could try uninstalling the flash player through synaptic, and installing manually through the adobe site. 

[http://www.adobe.com/go/getflashplayer]("http://www.adobe.com/go/getflashplayer")

Then just follow adobe's instructions. 

> Install the plug-in tar.gz using Install script:

    * Unpack the tar.gz file
    * In terminal, navigate to the unpacked directory and enter:
          o $ ./flashplayer-installer
          o Click Enter and follow prompts


Maybe that will help as you will have the most recent flash plug in. Let us know if it works for you.

---

### Post by jivabill on 2008-01-27
Hi Incense, nice to meet you.  Thank you for the suggestion.  I think I may have already done that.

What I did is to uninstall the original macromedia flash plugin using add/remove programs.  Then I had found here on the forums in another thread a flash player "fix".  The info said  that when it was run it would go to the adobe site and get the latest flash player.  I did run it and it installed flash.  Here is the name of the file:

flashplugin-nonfree_9.0.115.ubuntu3_i386.deb

Guess I should check on the adobe site and see if that is the file name for the latest linux version.
bill

---

### Post by jivabill on 2008-01-27
Well, I went to Adobe and found that the version of flashplayer I have installed is the latest.  And under trouble shooting I found the following:
===============
If your system does not support hardware-scaled full-screen playback, then Flash Player will automatically change to software-rendered full-screen playback.

Visit your video card's manufacturer website to obtain new video drivers.
=================

Which may have something to do with my problem.  BUT the system did do total full screen running on XP.

Clearly I need to look further for the solution.

Oh yes, I see looking at my notes that I made a mistake typing in the file name for flashplayer that I used.  There should be an "0" between 5. and ubuntu3...

bill

---

### Post by nowshining on 2008-01-27
in firefox u can put into the url box

about:config - for settings :) more advanced

or to see what plugins u have installed and their version

```
about:plugins
```

:)

what exactly is ur video card?

---

### Post by jivabill on 2008-01-29
Hi Nowshining
Well, I did the about:config thing, got a huge list of stuff, so far I have not found an entry for a flash plugin.  It may be there but at the moment I can not find it.

But I did find the video card, the thing the system says about it is "intel 815".

But, don't forget, the video card worked fine in XP got complete full screen right to the edges and the picture was enlarged to fit that format as it should be.

In ubuntu the problem is that the picture does not enlarge all the way to fit the full screen area.  So it seems like the card is working but something in my linux set up is not quite right to render a real full screen.

---

### Post by nowshining on 2008-01-29
try  ```
about:plugins
```

srry stupid smiley :)

---

### Post by jivabill on 2008-01-30
Hi Nowshining, Bill here Jivabill
OK, First of all, I did try about:plugins, worked great.  I have installed Shokwave Flash Player 9.0 r115 which i believe is the latest greatest flash player.

Second thing, last night late I tried playing some video on youtube and VOILA total full screen like it should be.  So some of my fiddling must have fixed it OR the videos I have been trying to watch that did not play full screen were put up that way on you tube, I am assuming it is possible to load a video that only plays to a certain size.  Don't know, just seems like an answer.

So it appears, and I stress appears, that the problem is fixed with flash player 9 from the deb archive,.  I guess I should mark this thread SOLVED so as to save other taking the time to try to fix it for me again :-).

Thank you for all your good help.
Bill

---

### Post by nowshining on 2008-01-30
ur welcome, i'm happy u got it fixed :)

---

### Post by jivabill on 2008-01-30
OOOPS ! ! 
I was celebrating too soon.  Now I have a new problem.

Thing is, when I was using the older version of Flashplayer (from the Ubuntu archive) then I did not have full screen, BUT the video played correctly.

Now I notice that with the newest Flashplayer I have full screen but when viewing a video in Full Screen instead of a steady movie what I get is like a slide show: on about one second intervals the display is reloaded so what it looks like is almost like a really fast slide show rather than a movie.

So I guess I can't win.

Either this is a problem with the Linux version of flashplayer or something in my system is not set right.  Guess I should go into System Admin and check out all the video and screen settings.

BTW I did find this very problem mentioned in another thread and there was no solution offered yet.
Regards
Bill

---

