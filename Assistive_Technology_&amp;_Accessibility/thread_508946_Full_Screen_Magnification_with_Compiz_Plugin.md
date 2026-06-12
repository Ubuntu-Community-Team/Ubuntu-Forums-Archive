---
title: "Full Screen Magnification with Compiz Plugin"
date: 2007-07-24
forum: Assistive Technology &amp; Accessibility
---

### Post by musther on 2007-07-24
I'm looking for decent, fast and reliable, quickly accessible full screen magnification for Ubuntu.  I know this can be done with gnome-mag, and that's fair enough, but the compiz-zoom seems much better (apart from its one big flaw, it doesn't accept input).  I've heard bits and pieces about interactive zoom plugins for compiz, but can't find anything concrete, is anyone even working on one?

This is something that would be of great use to a lot of people, does anybody know anything about it?

---

### Post by jasongrieves on 2007-07-24
First, beryl's zoom can accept user input.  I am not sure of compiz (Although i heard it can).  It has many limitations.  Look up instructions for Beryl, and play with the GUI for Zoom to accomplish this.

Kristin is working on exactly what you want :).  Her blog can be seen here
[http://dev.beryl-project.org/~kristian/category/summer-of-code/](http://dev.beryl-project.org/~kristian/category/summer-of-code/)

Once Ubuntu syncs up with the newest compiz/beryl code, we should be able to get some betas of her software into testing.  From what she says, it looks like her zoom will go ahead right into compiz-fusion....

hope this helps.

---

### Post by musther on 2007-07-25
I found Kristin's blog very encouraging, so we should be able to try out the betas of that on 7.10 as it'll be synced with the up-to-date compiz-fusion?

Thanks

---

### Post by jasongrieves on 2007-07-25
that is my hope.  If not, someone in our community will bring up some instructions on how to test it.

---

### Post by KristianLy on 2007-07-27
It's nice to see people taking interest in ezoom :)

As I just posted on my blog ([http://dev.beryl-project.org/~kristian/](http://dev.beryl-project.org/~kristian/)), ezoom just entered the "plugins-main" package repository of Compiz Fusion, which hopefully means it'll be packaged ASAP for Ubuntu Gutsy. 

Oh, by the way Jason, Kristian is a boy's name ;)

---

### Post by musther on 2007-07-27
Ah, but he didn't write Kristian, he wrote Kristin ;)

I'm glad ezoom's in there though, I'm am really looking forward to it.  Please Kristian, tell us more about it!

And does anybody fancy explaining how I can get this up to date, ezoom containing, plugins-main package installed on Fiesty?  

Thanks

---

### Post by KristianLy on 2007-07-27
> **musther said:**
> Ah, but he didn't write Kristian, he wrote Kristin ;)

I'm glad ezoom's in there though, I'm am really looking forward to it.  Please Kristian, tell us more about it!

And does anybody fancy explaining how I can get this up to date, ezoom containing, plugins-main package installed on Fiesty?  


Well, ezoom zooms without disabeling input, unlike the zoom plugin that's included in the compiz core package. It (optionally) tracks focus so if you alt tab to another window it will move the zoom area there and (optionally) adjust the zoom level to best fit to the window. Through some treacherous trickery it is also able to keep the zoomed area still while moving the mouse, something Beryl's input zoom never manged, in other words: You can zoom in on a window and interact with the window and the zoomed area won't move. 

It also has a rather simple but powerful dbus interface which I plan to use to send it at-spi information, or otherwise let other applications drive the zoom (like orca)

As for how to use it, Trevino has a Feisty repository, details about it can be found at the opencompositing forums: [http://forums.opencompositing.org/viewtopic.php?f=14&t=131](http://forums.opencompositing.org/viewtopic.php?f=14&t=131) though it hasn't caught up yet to the recent changes (his plugins-main package is from 0724). When he catches up, ezoom will be in those packages. Since I don't use his packages, I can't vouch for the quality, but it is the most used Compiz Fusion repository for Ubuntu Feisty.

---

### Post by janbockaert on 2007-07-29
> **KristianLy said:**
> ...through some treacherous trickery it is also able to keep the zoomed area still while moving the mouse, something Beryl's input zoom never manged, in other words: You can zoom in on a window and interact with the window and the zoomed area won't move. 
.

That is great,that was the reasons i did not like beryl's input zoom.

ezoom is now in my compiz configuration (trevino-repos), i can enable it, but there are no options to chose. it doesn't seems to work, and i can not find the plugin in gconf.

I guess i'll wait for another update?

---

### Post by KristianLy on 2007-07-30
> **janbockaert said:**
> 
ezoom is now in my compiz configuration (trevino-repos), i can enable it, but there are no options to chose. it doesn't seems to work, and i can not find the plugin in gconf.

I guess i'll wait for another update?

There was a minor blunder with the initial packaging causing the metadata to not be packaged, and that's what describes the options.

You can either wait for the packages to update, or download [http://gitweb.opencompositing.org/?p=fusion/plugins/ezoom;a=blob;f=ezoom.xml;h=c1232abc7d33e9b07edcadcf9379acc30ecdebff;hb=5d9f906b64b1710c1964016c02e2edb350ac4ac9](http://gitweb.opencompositing.org/?p=fusion/plugins/ezoom;a=blob;f=ezoom.xml;h=c1232abc7d33e9b07edcadcf9379acc30ecdebff;hb=5d9f906b64b1710c1964016c02e2edb350ac4ac9) manually (make sure you get the pure .xml not a html version of it) and put it in /usr/share/compiz

---

### Post by janbockaert on 2007-07-30
Thanks for the information and the plugin. Updates are almost daily, so i guess i'll wait one more day to see if ezoom arrives. :)

I'm looking forward using it. (and showing it to my mac and vista friends :) )

---

### Post by musther on 2007-07-30
So how did you go about installing this on feisty?  I've looked around, but am still somewhat unclear.

Thanks.

---

### Post by janbockaert on 2007-07-31
if you install compiz-fusion with the trevino repositories (the easy way to do it).

[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

you can activate the e-zoom in the compiz-settings. Ezoom is working as of today. (yesterday, you could not change the mouse-settings, today, the only 'bug' i found was a bad calibration of the non-scaled mousecursor)

The only thing i miss from the original desktopzoom is the "press super + right mousebutton + drag" routine to zoom in on a selected area of the desktop. I use the zoom mostly for watching flashvideo's fullscreen, and that routine was very handy.

---

### Post by musther on 2007-07-31
Thanks!  I've got it up and running now, the ezoom plugin is really, really useful!

The only thing that would be good in the future is tracking of a text cursor - such that when zoomed into a terminal or word-processor, the text cursor is followed when typing.  -  Is that possible?

Thanks again!

---

### Post by KristianLy on 2007-07-31
> **musther said:**
> Thanks!  I've got it up and running now, the ezoom plugin is really, really useful!

Thanks :)

> 
The only thing that would be good in the future is tracking of a text cursor - such that when zoomed into a terminal or word-processor, the text cursor is followed when typing.  -  Is that possible?


This is being worked on as we speak, and is the last big part of the enhanced zoom project I'm working on for Summer of Code (for Ubuntu).

This requires information from AT-SPI, however. The ezoom plugin has the interface already to be run from external applications, like Orca, so the last part is to implement it in Orca and/or a little script for those who don't want to run all of Orca for something so apparantly trivial. My goal is to have a script included in Compiz Fusion along with ezoom, that ezoom can start automatically if the user wants it.

---

### Post by jasongrieves on 2007-08-01
Kristian, 

Sorry about the wrong name and use of pronouns :).  Can I blame it on not seeing your name clearly? :).  

Your work has been great.  I will be presenting your progress to Virginia Tech's Assistive Technology Center in the coming weeks!

---

### Post by musther on 2007-08-01
I second that, your work has been really awesome!

This plugin is going to make *the* difference to many users who are not blind, visually impaired.  

I doubt I'll be using it on my desktop much, but on my 14" screen laptop it's an absolute lifesaver.

I, like Jason, will be publicising this to my visually impaired friends as a way to open up Ubuntu, and more generally linux to them.

Thanks again.

---

### Post by jasongrieves on 2007-08-02
Are there docs or videso of how to control all of the settings?

1) how goes the dual monitor support?
2) zoom specific windows?
3) great work on the mouse!


thanks,

Jason Grieves

---

### Post by musther on 2007-08-03
If you install compiz-fusion as per:
[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

Then you can go 'System>Preferences>CompizConfig Settings Manager' and double click on the ezoom plugin, you can configure all of the control keys and things in there.

---

### Post by jasongrieves on 2007-08-03
Yeah I see those.  Its a nice GUI, but I am not sure I see anything dealing with zooming specific windows.  The specific zoom regions are great too.

---

### Post by jasongrieves on 2007-08-03
I just spent some time playing with all of the options.  Zooming per application works very well!  I am amazed at the speed and accuracy.  Not only do you bring focus correctly but you maximize the application to fit the zoomer. 

You have finally convinced my admins here to devote some machines in our lab to showcase unix.  GREAT job!

---

### Post by musther on 2007-08-03
I see from your signature that you're a 'low vision user' as am I.  I suspect you'll agree that this one plugin has taken away the one barrier for visually impaired users of Ubuntu and other distros (of course that doesn't count for users who are so visually impaired that they need speech, they're still stuck...  ...for now).

I am absolutely thrilled, and you mentioned the speed - the performance of ezoom is far, far better than any commercial screen magnifier for windows, I'm sure this is because of the hardware acceleration, and the great base provided by Compiz-Fusion.  When the text cursor following is added, it will be complete in my eyes (no pun intended).

Once again Kristian great work!

---

### Post by RKCole on 2007-08-06
I agree with the others here, Kristian.  I just installed Compiz Fusion today, and am beginning to work with the ezoom plugin.  It is amazing!!

Thank you for the work you've put into this, and are putting into it.

---

### Post by RKCole on 2007-08-06
Okay...I must reiterate on this...This is simply amazing.  It beats some other commercial magnifiers...out of the water.  I cant' believe how much faster my system runs with this magnifier.

One question...Is there a way to keep the pointer centered?

Thanks so much again for this.

---

### Post by KristianLy on 2007-08-10
I've been away for a week so a little slow on the replies, but here goes:

First; thanks for the support :)

> 
1) how goes the dual monitor support?


Currently ezoom will treat each head separately. It is a small matter to treat them as one, if that is wanted. 

I've been pondering combining what we do with the clone plugin (which, for those who don't know, is a way to display the same output on two heads) with ezoom; That would mean having one head always zoomed out, displaying the desktop, while the other can be used to zoom. Sort of using the second head as a map. 

This is beyond the scope of the current project, however. And I'm not sure how useful it will be. 

> 
2) zoom specific windows?


I take it you already discovered this? Either way I believe <Super>R is the default binding to fit the zoom level to the window. It works, if I may say so my self, quite well.

> 
One question...Is there a way to keep the pointer centered?


Not currently. I should be able to implement this quite easily, however, as it's just a matter of using the existing mouse panning code and dynamically increasing the margins so we're left with 1x1 pixel in the middle where the mouse can "move" before the zoom area pans. Or similar. Point being that the mechanism for implementing this already exist.

Would it be desirable to "block" the cursor from leaving the center when you reach the edges too? This is technically not easy without the same nasty method you see with "restrain cursor": Moving the cursor when it moves outside the specified area. 

I'm curious about what settings you choose to use. Specially those who are actually visually impaired, so far much of my user base have been user with good eyesight. Or any sort of tweaks.

I've already received a request for combining the lock/unlock bindings into a single toggle binding, which makes perfect sense and will be implemented tonight or tomorrow. Anything you feel is missing or could be better would be a great help. However small, or big.

---

### Post by RKCole on 2007-08-10
Well...I have all of the default settings, except that I enabled the option to scale the mouse pointer.  This one is a great help to me as I'd be lost without the enlarged mouse pointer. :)

I will say one thing:  this beats ZoomText out of the water.  Things ran slower while ZoomText was running, but with the eZoom plugin, my computer runs just as well as if nothing was being used.  It is simply amazing.

Oh...the reason why I asked about a centered pointer is that sometimes if the cursor is at the sides or the top/bottom of the screen, I sometimes have trouble finding it. :)

---

### Post by KristianLy on 2007-08-10
> **RKCole said:**
> Well...I have all of the default settings, except that I enabled the option to scale the mouse pointer.  This one is a great help to me as I'd be lost without the enlarged mouse pointer. :)

I will say one thing:  this beats ZoomText out of the water.  Things ran slower while ZoomText was running, but with the eZoom plugin, my computer runs just as well as if nothing was being used.  It is simply amazing.

Oh...the reason why I asked about a centered pointer is that sometimes if the cursor is at the sides or the top/bottom of the screen, I sometimes have trouble finding it. :)

Ah, there is a binding to center it but I haven't actually tested this with "sync mouse" turned on, when you mention it. The water plugin does have that "wave" function that helps you locate a mouse, but I'm not a big fan of it myself  (specially since it requires fragment_program). 

How are you (anyone reading this) finding the annoyance of the disappearing cursor if you enabled scaled cursor, hide original cursor and disable "mouse sync"? Personally I find that the effect you get with those options makes the temporary disappearing cursors a burden I can bare, but I'm curious about how serious others consider this issue?

---

### Post by RKCole on 2007-08-10
I have the options set to sync the mouse pointer and to scale it, but I have the option for hiding the pointer disabled.  I don't know...I am just used to using the mouse pointer to keep track of where I'm at while reading; I guess its presence is something I've gotten used to ever since I started using a screen magnifier  Also..at one point the mouse pointer disappeared permanently when I zoomed out completely.  I didn't know how to get ti back. :)

I actually just htought of something..not related to these options.  It's not too important to me anymore, though, but I am just curious.

When I used Windows (ZoomText), there was an option for a horizontal split-screen magnification where the bottom portion of the screen would be regular size and the top half would be magnified.  This used to be my default setup, but when I came to Linux I began to love full-screen magnification.  I don't really know why I never used it before now. :)  I was just curious as to whether or not a split screen magnification setup was possible, though.

---

### Post by KristianLy on 2007-08-10
> **RKCole said:**
> I have the options set to sync the mouse pointer and to scale it, but I have the option for hiding the pointer disabled.  I don't know...I am just used to using the mouse pointer to keep track of where I'm at while reading; I guess its presence is something I've gotten used to ever since I started using a screen magnifier  Also..at one point the mouse pointer disappeared permanently when I zoomed out completely.  I didn't know how to get ti back. :)


This is, unfortunately something that has been known to happen due to XFixes rather flawed implementation, I've never seen it myself though. I do, however, have invisible cursors while firefox loads (which would otherwise cause an animated cursor).

> 
I actually just htought of something..not related to these options.  It's not too important to me anymore, though, but I am just curious.

When I used Windows (ZoomText), there was an option for a horizontal split-screen magnification where the bottom portion of the screen would be regular size and the top half would be magnified.  This used to be my default setup, but when I came to Linux I began to love full-screen magnification.  I don't really know why I never used it before now. :)  I was just curious as to whether or not a split screen magnification setup was possible, though.

This is technically possible, but would fit under what I mentioned earlier with regards to multihead. You'd simply set compiz up so it thought one monitor was two (or the plugin could do it for you, this is fairly trivial).

---

### Post by kakashi on 2007-08-13
hi guys. 
i am on gutsy and have the latest update. i enabled ezoom  but i can't get it to accept input while zoomed. in fact it behaves almost exactly like the older zoom plugin. should i be doing something to enable input.

also none of the shortcut like <super>+V etc work.

---

### Post by KristianLy on 2007-08-13
> **kakashi said:**
> hi guys. 
i am on gutsy and have the latest update. i enabled ezoom  but i can't get it to accept input while zoomed. in fact it behaves almost exactly like the older zoom plugin. should i be doing something to enable input.

also none of the shortcut like <super>+V etc work.

Are you sure it is enabled, and not the original desktop zoom?

The way this works is that you never have to technically do anything to enable input; input is enabled by default. The original desktop zoom plugin takes step to DISABLE input, steps that are not taken in ezoom (we do, however, apply some tricks to emulate input redirection).

---

### Post by musther on 2007-08-13
I don't think ezoom is in gutsy yet (I tried the tribe 4 release the other day).

I hope it is before the release though (I think it's supposed to be).

---

### Post by kakashi on 2007-08-13
this is a screen shot of the setting. 
[http://img57.imageshack.us/img57/2121/screenshot2kj4.png](http://img57.imageshack.us/img57/2121/screenshot2kj4.png)

is this right.
edit

ahh never mind. apparently it needed a restart.

---

### Post by KristianLy on 2007-08-13
> **musther said:**
> I don't think ezoom is in gutsy yet (I tried the tribe 4 release the other day).

I hope it is before the release though (I think it's supposed to be).

It is and it is.

The updated compiz-fusion-plugins-main package of 20070810 includes it.

---

### Post by KristianLy on 2007-08-13
> **kakashi said:**
> this is a screen shot of the setting. 
[http://img57.imageshack.us/img57/2121/screenshot2kj4.png](http://img57.imageshack.us/img57/2121/screenshot2kj4.png)

is this right.

This looks right, what settings does enhanced zoom offer for you? There was an incident when ezoom entered plugins-main when no information about options was included in the package, does this apply to you?

---

### Post by musther on 2007-08-25
I just got an update from Treviño's repos, and now there's no key binding page for the ezoom plugin, and my old keybindings arn't working.

---

### Post by KristianLy on 2007-08-25
> **musther said:**
> I just got an update from Treviño's repos, and now there's no key binding page for the ezoom plugin, and my old keybindings arn't working.

Which version of compiz, ccsm, compizconfig, compizconfig-python and plugins-main are you using, exactly?

The entire key and (mouse)button framework has changed, so there might be something out of sync in Trev's packages. This is not likely to be included in gutsy, however, as I assume we'll go with 0.6 for Gutsy.

---

### Post by musther on 2007-08-27
Ok, here are the versions:

compiz 0.5.5-git20070820+3v1ubuntu1
ccsm - couldn't get it to give me a version, -v or --version didn't work, and no package with this name
compizconfig 0.5.2-git20070821+3v1ubuntu1
compizconfig python 0.5.2-git20070822+3v1ubuntu1
plugins-main 0.5.2-git20070823+3v1ubuntu1

---

### Post by KristianLy on 2007-08-27
Ok, we are in the middle of a transition from one way of doing actions to another, and I was late in updating ezoom master for this, focusing mostly on 0.6.

My guess is you ended up with a build of trev's which contained the new action system but not all plugins were updated for it, making it seem like there were no key/mouse bindings.

In other words: Stand by for another update.

---

### Post by RKCole on 2007-08-27
I just updated to the latest version fo Compiz Fusion from trevino's Repository and I was wondering if anyone else noticed this:

When I move the mouse over one of my panels, I have to keep pulling to get the mouse pointer to leave that particular area.  This also seems to happen if I try to move my mouse pointer outside the bounds of any given window.  My screen just look slike ti si shaking, and ti takes a second to get the mouse pointer away from windows and panels.  Any ideas on this one?

EDIT:  I was slightly incorrect on the above.  after a little further investigation, I found that this does not occur with windows, but rather when I move the mouse too close to the top, bottom, and sides of the screen.  It seems like the pointer is pulled there fi it gets too close, and I have to move my mouse away from the mentioned area for a second ro so for to to free itself.  this only seems to happen whiel zoomed in.

---

### Post by RKCole on 2007-08-27
I am wondering if this may have anything to do with it or not...this is from running
```

compiz --replace

```
in a terminal:

```

bob@bandgc:~$ compiz --replace
^XGConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


```

Hope maybe this can help to resolve whatever si going on.  I'll do what I can to help.  Other than this, everything si running perfectly.

Thanks and take care.

---

### Post by RKCole on 2007-08-30
I am unsure as to whether or not a more simplified solution is available for the above problem, but I ran a complete uninstall of all of the Ccmpiz Fusion components and then reinstalled.  The problem with "initiate_edge" seems to be gone now. :)

---

### Post by musther on 2007-08-30
Well my problem (with key bindings) is gone now due to another update, maybe that fixed you too, and the timing was just a coincidence.

---

### Post by Will B-R on 2007-10-15
In the other zoom plug in I could draw a region to zoom in on, say a flash game. Can I do that with eZoom but be able to play it?

Also what about holding down a modifier like super and panning around the screen?

---

### Post by musther on 2007-10-15
As far as I know (and I now user ezoom daily), there is no function to do what you want, but it might be a nice feature so you should suggest it.  

As for panning, the default behaviour for ezoom is to follow the mouse, and there are keybindings for locking the zoom position and also for moving it with the keyboard.

Hope that helps.

---

### Post by Will B-R on 2007-10-17
Where do I need to suggest it?

---

### Post by musther on 2007-10-17
Best bet, contact Kristian (who wrote ezoom), his email address is on this page:
[http://dev.compiz-fusion.org/~kristian/about-the-author/](http://dev.compiz-fusion.org/~kristian/about-the-author/)

He's very friendly to chat too.  :-)

---

