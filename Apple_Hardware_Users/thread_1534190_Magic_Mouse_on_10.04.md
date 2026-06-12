---
title: "Magic Mouse on 10.04"
date: 2010-07-19
forum: Apple Hardware Users
---

### Post by Jratz91 on 2010-07-19
I'm sure this question has been beaten to death, but is there a simple way to get the Apple Magic Mouse to play nice with 10.04?  I've seen a few things that seem to work that I don't understand, and a lot of others that just go in circles.  I'm fairly new to Ubuntu, so I don't understand how a lot of this works.  Heck, if someone can point me to a good walkthrough, that'd be helpful too.

---

### Post by DoubleClicker on 2010-07-19
> **Jratz91 said:**
> I'm sure this question has been beaten to death, but is there a simple way to get the Apple Magic Mouse to play nice with 10.04?  I've seen a few things that seem to work that I don't understand, and a lot of others that just go in circles.  I'm fairly new to Ubuntu, so I don't understand how a lot of this works.  Heck, if someone can point me to a good walkthrough, that'd be helpful too.

I haven't had any trouble.  Have you checked, that you have bluetooth configure correctly, and working?

---

### Post by Jratz91 on 2010-07-20
I suppose I should elaborate.  It clicks, it points, it doesn't scroll or work with MultiTouch.

---

### Post by Twiggy794 on 2010-07-30
> **Jratz91 said:**
> I suppose I should elaborate.  It clicks, it points, it doesn't scroll or work with MultiTouch.

I maintain a backport of the Magic Mouse drivers for Maverick here: [http://github.com/scottferg/multitouch](http://github.com/scottferg/multitouch)

Just run ```
$ dpkg-buildpackage -rfakeroot -b
``` to get a deb and you should have horizontal and vertical scrolling.  Multitouch would require an Xorg driver and I don't believe anybody has stepped up to the plate to work on that yet.  Or at least not in the Lucid world they haven't.

---

### Post by Jasev on 2010-08-01
I just got my magic mouse and was expecting problems, but to my delight scrolling works out of the box. I'm running an up to date 10.10 (alpha?) with kernel 2.6.35-13. I guess all the drivers have been inserted into the new kernel. Haven't tried  any 2-finger zooming etc as yet.

---

### Post by Twiggy794 on 2010-08-01
> **Jasev said:**
> I just got my magic mouse and was expecting problems, but to my delight scrolling works out of the box. I'm running an up to date 10.10 (alpha?) with kernel 2.6.35-13. I guess all the drivers have been inserted into the new kernel. Haven't tried  any 2-finger zooming etc as yet.

Yeah the package I posted up above is a backport from Maverick, so everything should work smoothly for you.  Let us know how true multitouch features work, since Maverick also includes the multitouch Xorg drivers.

---

### Post by nilsja on 2010-08-17
pleaaaaaase let us know if or how multitouch works

---

### Post by carmelosantana on 2010-08-23
> **nilsja said:**
> pleaaaaaase let us know if or how multitouch works

Also very curious. I'll be order a keyboard and mouse this afternoon and would love to know if the Magic Mouse multi touch is also working.

Update: [https://wiki.ubuntu.com/Multitouch/AppleMagicMouse](https://wiki.ubuntu.com/Multitouch/AppleMagicMouse)

---

### Post by Twiggy794 on 2010-08-23
> **carmelosantana said:**
> Also very curious. I'll be order a keyboard and mouse this afternoon and would love to know if the Magic Mouse multi touch is also working.

Update: [https://wiki.ubuntu.com/Multitouch/AppleMagicMouse](https://wiki.ubuntu.com/Multitouch/AppleMagicMouse)

This is great! Unfortunately my backport is kernel drivers only and I'm sure that PyMT depends on the Xorg driver.  Either way, this does mean that we'll have a gateway to multitouch functionality in Maverick, which is awesome.

As for my kernel driver, I'm trying to get a PPA setup.  Been a bit busy though, sorry for the delays.

---

### Post by Twiggy794 on 2010-08-23
Hardcore hacks ahoy.  If you use my kernel driver and follow [these]("http://pymt.eu/wiki/DevGuide/InstallPymtUbuntu") [instructions]("https://wiki.ubuntu.com/Multitouch/PyMT") you can get PyMT up and running on Lucid.  PyMT requires an application to be running on the desktop, but continues to accept input whether or not the app has focus (or is minimized).  Because of this, I was able to hack together a rough implementation of multitouch gestures for the desktop.

Swiping left/right with two fingers will rotate the cube.  Swiping down with three fingers will call up Expose.  In order to use this you will need the Dbus, Scale, and Rotate Cube plugins enabled in Compiz.  I also had to be a little dirty and apply:
```
$ sudo chmod a+r /dev/input/event7
```
in order to run the app as the current user.  Without this, Dbus can't connect to the running session.

Here's the Python file: [http://gist.github.com/546779](http://gist.github.com/546779)

PyMT installation instructions for Lucid: [http://pymt.eu/wiki/DevGuide/InstallPymtUbuntu](http://pymt.eu/wiki/DevGuide/InstallPymtUbuntu)
PyMT configuration instructions for Ubuntu: [https://wiki.ubuntu.com/Multitouch/PyMT](https://wiki.ubuntu.com/Multitouch/PyMT)

---

### Post by carmelosantana on 2010-08-26
Well I've updated to 10.10. Got a bit sketchy with the nvidia drivers. After setting the ServerFlags I was able to successfully log into my system.

MultiTouch does work out the box on 10.10, but so far my mouse performance is ... mediocre. I feel like theres an awkward dead spot or something when I move the mouse left or right it'll sometimes "hang" but it may just take some serious getting used to. Its much smaller then I expected.

So far - multi touch is working scrolling is working. Not sure what else is enabled aside from scrolling. 

Is there a way to change the update threshold for a BT connection?

Anything I should look for, try, etc?

---

### Post by Twiggy794 on 2010-08-26
> **carmelosantana said:**
> Well I've updated to 10.10. Got a bit sketchy with the nvidia drivers. After setting the ServerFlags I was able to successfully log into my system.

MultiTouch does work out the box on 10.10, but so far my mouse performance is ... mediocre. I feel like theres an awkward dead spot or something when I move the mouse left or right it'll sometimes "hang" but it may just take some serious getting used to. Its much smaller then I expected.

So far - multi touch is working scrolling is working. Not sure what else is enabled aside from scrolling. 

Is there a way to change the update threshold for a BT connection?

Anything I should look for, try, etc?

When you say multitouch is working, what's working?

---

### Post by carmelosantana on 2010-08-26
> **Twiggy794 said:**
> When you say multitouch is working, what's working?

I guess by multitouch I mean surface scrolling. Thats all I've been able to successfully use at this time. I plan on moving some files around and doing a fresh install of 10.10 and giving it a solid try. Should be a LONG day for me.

---

### Post by Twiggy794 on 2010-08-26
> **carmelosantana said:**
> I guess by multitouch I mean surface scrolling. Thats all I've been able to successfully use at this time. I plan on moving some files around and doing a fresh install of 10.10 and giving it a solid try. Should be a LONG day for me.

Yeah, that's not multitouch (and neither is the left/right clicking on the magic mouse).  Multitouch would mean reading multiple touches simultaneously and doing something interesting.  Fortunately, that's easy to test and should work out of the box :D

Follow these instructions: 

PyMT installation instructions for Lucid: [http://pymt.eu/wiki/DevGuide/InstallPymtUbuntu](http://pymt.eu/wiki/DevGuide/InstallPymtUbuntu)
PyMT configuration instructions for Ubuntu: [https://wiki.ubuntu.com/Multitouch/PyMT](https://wiki.ubuntu.com/Multitouch/PyMT)

See if PyMT works.  If it does (and I imagine it will) then yeah, multitouch works out of the box.  Make sure to download my script if it works for you. Multitouch gestures for the desktop :)

---

### Post by carmelosantana on 2010-08-26
> **Twiggy794 said:**
> Yeah, that's not multitouch (and neither is the left/right clicking on the magic mouse).  Multitouch would mean reading multiple touches simultaneously and doing something interesting.  Fortunately, that's easy to test and should work out of the box :D

Follow these instructions: 

PyMT installation instructions for Lucid: [http://pymt.eu/wiki/DevGuide/InstallPymtUbuntu](http://pymt.eu/wiki/DevGuide/InstallPymtUbuntu)
PyMT configuration instructions for Ubuntu: [https://wiki.ubuntu.com/Multitouch/PyMT](https://wiki.ubuntu.com/Multitouch/PyMT)

See if PyMT works.  If it does (and I imagine it will) then yeah, multitouch works out of the box.  Make sure to download my script if it works for you. Multitouch gestures for the desktop :)

Ya we're on the same page now. Surface scrolling wasn't working on 10.04 so that was nice to see on 10.10. 

Whats the story on the track pad? I'm thinking I may exchange this for a track pad. I'm not exactly excited about the ergonomics of this ether. I would imagine without multi-touch a trackpad would be difficult to use.

---

### Post by Twiggy794 on 2010-08-26
> **carmelosantana said:**
> Ya we're on the same page now. Surface scrolling wasn't working on 10.04 so that was nice to see on 10.10. 

Whats the story on the track pad? I'm thinking I may exchange this for a track pad. I'm not exactly excited about the ergonomics of this ether. I would imagine without multi-touch a trackpad would be difficult to use.

Yeah scrolling was actually just a driver thing.  Basically telling the kernel what a scroll actually was.  My backported drivers will do that in Lucid, and I would be willing to be that PyMT won't work in Lucid without my drivers either.

I would think with the track pad it should be the same experience.  As long as you have the appropriate driver for the device you should be good to go.

---

### Post by carmelosantana on 2010-08-26
The multi touch demo did not work correctly. This 10.10 install isn't working correctly, I have a few things crashing and not working 100%. I'll be moving files around - and perform a fresh install of 10.10 this afternoon. 

I think I'll end up with the trackpad if my announce with the mouse continues.

---

### Post by Twiggy794 on 2010-08-26
> **carmelosantana said:**
> The multi touch demo did not work correctly. This 10.10 install isn't working correctly, I have a few things crashing and not working 100%. I'll be moving files around - and perform a fresh install of 10.10 this afternoon. 

I think I'll end up with the trackpad if my announce with the mouse continues.

Awesome, thanks for the report!

Maverick is still pre-beta so it makes sense things might not work just yet.

---

### Post by carmelosantana on 2010-08-26
> **Twiggy794 said:**
> Awesome, thanks for the report!

Maverick is still pre-beta so it makes sense things might not work just yet.

Ya I figure things might have gotten garbled up during the install. I had some stuff setup in 10.04 that might have messed up 10.10. I'm no expert in linux but I'm comfortable in terminal. 

Still learning, thats what this is all about ...

But this mouse .. its just awkward. I try to resize a window and when I slow down to go ahead and click on the corner to resize its like the mouse stops moving horizontally but will continue to move vertical. Not sure if its Ubuntu, my BT receiver, or the mouse it self but its very VERY inconvenient.

Update: Has anyone else experienced this?

---

### Post by Twiggy794 on 2010-08-26
> **carmelosantana said:**
> Ya I figure things might have gotten garbled up during the install. I had some stuff setup in 10.04 that might have messed up 10.10. I'm no expert in linux but I'm comfortable in terminal. 

Still learning, thats what this is all about ...

But this mouse .. its just awkward. I try to resize a window and when I slow down to go ahead and click on the corner to resize its like the mouse stops moving horizontally but will continue to move vertical. Not sure if its Ubuntu, my BT receiver, or the mouse it self but its very VERY inconvenient.

Update: Has anyone else experienced this?

Are you using a BT keyboard or is the BT receiver far away when it happens?  I use an Apple BT keyboard along with my Magic Mouse and it gets wonky when they're right next to each other.

---

### Post by carmelosantana on 2010-08-26
> **Twiggy794 said:**
> Are you using a BT keyboard or is the BT receiver far away when it happens?  I use an Apple BT keyboard along with my Magic Mouse and it gets wonky when they're right next to each other.

BT receiver is literally inches from the mouse. Its plugged in on the right USB port of a wired apple keyboard. I tried 2 different receivers with the same result.

Update: Not sure what changed but I performed a complete install and it seems the mouse isn't as jerky. I'll be up testing and working for awhile. I need to enable scrolling in 10.04 just unsure how exactly to begin.

---

### Post by carmelosantana on 2010-08-26
> **Twiggy794 said:**
> This is great! Unfortunately my backport is kernel drivers only and I'm sure that PyMT depends on the Xorg driver.  Either way, this does mean that we'll have a gateway to multitouch functionality in Maverick, which is awesome.

As for my kernel driver, I'm trying to get a PPA setup.  Been a bit busy though, sorry for the delays.

Any update on your PPA?

Update: I Ran the .deb and on your github, but don't know whats necessary to get this working. Any help is appreciated, thanks.

---

### Post by Twiggy794 on 2010-08-26
> **carmelosantana said:**
> Any update on your PPA?

Update: I Ran the .deb and on your github, but don't know whats necessary to get this working. Any help is appreciated, thanks.

Wow so I totally forgot I even had the file available for download up there.  Just updated it, so I would recommend using that one.

Anyways, once it's installed just reboot.  You'll know it's working because you'll have horizontal scrolling and vertical scrolling across the entire surface of the device.

As for the PPA, just been lazy and it's unfortunately not a totally simple process to get setup.  Let me get cracking on that again.

---

### Post by carmelosantana on 2010-08-27
> **Twiggy794 said:**
> Wow so I totally forgot I even had the file available for download up there.  Just updated it, so I would recommend using that one.

Anyways, once it's installed just reboot.  You'll know it's working because you'll have horizontal scrolling and vertical scrolling across the entire surface of the device.

As for the PPA, just been lazy and it's unfortunately not a totally simple process to get setup.  Let me get cracking on that again.

I was doing a lot last night. After the restart everything worked correctly. I ran the -fakeroot command but was unsure what exactly was happening with that. After the restart the original files did work. It was just too late to update this. 

It would be great instead of scrolling try to use the surface of the mouse as a trackpad. I would be very interested in this functionality.

---

### Post by Twiggy794 on 2010-08-27
> **carmelosantana said:**
> I was doing a lot last night. After the restart everything worked correctly. I ran the -fakeroot command but was unsure what exactly was happening with that. After the restart the original files did work. It was just too late to update this. 

It would be great instead of scrolling try to use the surface of the mouse as a trackpad. I would be very interested in this functionality.

If you use the broken packages currently available in Lucid this is exactly how it works :D

---

### Post by carmelosantana on 2010-08-27
> **Twiggy794 said:**
> If you use the broken packages currently available in Lucid this is exactly how it works :D

Whats the best way for me to try this? Would it be possible to switch packages?

---

### Post by Twiggy794 on 2010-08-27
> **carmelosantana said:**
> Whats the best way for me to try this? Would it be possible to switch packages?

Add that xorg-edgers PPA and run an update I think.  Not entirely sure, since as soon as I encountered the bug that was when I went and got in touch with Chase Douglas and backported his patches.

---

### Post by carmelosantana on 2010-08-27
> **Twiggy794 said:**
> Add that xorg-edgers PPA and run an update I think.  Not entirely sure, since as soon as I encountered the bug that was when I went and got in touch with Chase Douglas and backported his patches.

I'll give it a try in the next few days. Redoing my system put me behind in client work but set me with a nice clean HD. I was able to purge my system a bit now I can setup a simple raid with my 2 500GB HDs and get nice steady backup going, well over due.

---

### Post by carmelosantana on 2010-08-27
Unsure how to go about fixing this, but theres a small issue with NetBeans. While scrolling it seems to act as if I'm clicking both left and right click at the same time. It makes it difficult to scroll through 5000+ lines of code :lolflag:. Thoughts?

---

### Post by Twiggy794 on 2010-08-27
> **carmelosantana said:**
> Unsure how to go about fixing this, but theres a small issue with NetBeans. While scrolling it seems to act as if I'm clicking both left and right click at the same time. It makes it difficult to scroll through 5000+ lines of code :lolflag:. Thoughts?

Weird, haven't experienced this.  Is it with my driver + my script?

---

### Post by carmelosantana on 2010-08-27
> **Twiggy794 said:**
> Weird, haven't experienced this.  Is it with my driver + my script?

I installed your driver from github and updated after you put the latest online. 

I don't have your desktop multitouch hack installed yet. 

Netbeans is the only program that reacts this way.

---

### Post by rkevsmith on 2011-04-12
Dear Fellow and Brave newbs:

I read the thread and understood that I didn't understand.

Then I read this: [http://blog.subutux.be/2011/02/21/the-magic-mouse-under-ubuntu/](http://blog.subutux.be/2011/02/21/the-magic-mouse-under-ubuntu/)

Now, I'm happily scrolling on 10.04 and hoping that I can continue to make Ubuntu work for me--- seems great, and I'm loving it, but there's just a long list of things to get my new(ubuntu)/old(still running my old OS on the other partition) machine me-friendly.

Enjoy your ride, 
K

---

### Post by rkevsmith on 2011-04-13
How can I make the magic mouse connect automatically when ubuntu starts?

Thanks for any pointers, 
K

---

