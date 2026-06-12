---
title: "Trying to test Edgy Eft (ISO's too large)"
date: 2006-08-23
forum: Assistive Technology &amp; Accessibility
---

### Post by Declan Moriarty on 2006-08-23
I read the post in alt.comp.blind users and clicked on the link to get the ISO for Ubuntu.  This was the Edgy Eft release in development.  The ISO for AMD64 processors was 708Mb and the one for desktop systems was 702Mb.  These won't fit on 700Mb CD's.  I have so far only found large CD's in a pack of 10 at Maplins and they will only sell me the pack not one disk for £11!  I have been advised by the shop I bought my computer from that the drive I am using may not be able to detect the large CD.  Would it be possible to generate DVD ISO's?  I have tried to burn the Edgy Eft ISO to DVD but to no avail.  I am loath to over burn as this can cause damage (well Nero in Windows gives dire warnings about it).  Large CD's may have the smae problem?

The advice on burning CD's was general and was stuff I knew already.  There was no warning in the original post in alt.comp.blind-users that the images would be larger that 700Mb.

I think that what you are doing is vital.  These reched live CD's without magnifiers/screen readers are dreadful.  At work we have an internet cafe for people to use web mail since it is blocked normally.  The machines all use eLearnix.  This uses the Gnomme Desktop and there is an Accessiblity pannel.  But when you activate the magnifier it says it is not intalled!  Thank god they don't use this at my local library.  Live CD's are dreadful because if you wanted to install the magnifier you couldn't because the OS is on a CD!

ALL live CD's should have Accessibility installed, indead it is a requirement in the US if the computer is being used by the government under Section 508 of the rehabilitation Act.  We also have the DDA in the UK but it has less teeth.

Thank you very much for your attention.

Declan Moriarty.

---

### Post by mlind on 2006-08-24
Have you tried overburning ? Every cd should contain at least 5-10 MB extra.

---

### Post by Henrik on 2006-08-24
Hi Declan,

The daily live CDs are automatically built, in part just to ensure that the whole build process works from day to day. The quality of those ISO is a bit random and do indeed seem to be oversized at the moment. 

You are better off trying one of the regular trusted releases, such as [http://cdimage.ubuntu.com/releases/edgy/knot-1/](http://cdimage.ubuntu.com/releases/edgy/knot-1/) because these get more manual monitoring in the build process. 

Later in the release cycle when the changes are smaller the daily builds also become more reliable.

Thanks for testing the development version! and please stick with us as it hopefully settles in over the next few weeks.

---

### Post by Declan Moriarty on 2006-08-25
Thank you very much.  I downloaded the AMD64 desktop release of Dapper Drake.  I managed to get Gnopernicus running, but there was an oblong white area in the centre top of the screen in portrait orientation.  It wasn't magnifying anything.  It partially obsured the logout box.  Was this the magnifier not magnifying at all?  I have an NVIDIA GeForce 7300 LE graphics card.  When I say the magnifier wasn't magnifying at all, I mean that the white oblong was completely white, there wasn't even a normal unmagnified image in it.  There wasn't an image in it at all.

Another idea I thought of is why not put a vertual screen in the Xfree86Config file allowing full screen magnifnication (without tracking) on the live CD.  There is a key combination (that eludes me now) that allows you to change screen resolutions.  In Ubuntu this virtual screen could come up in the VGA menu at the begining.  If Gnopernicus apsolutely fails this would be a backstop.

---

### Post by Declan Moriarty on 2006-08-25
The virtual screen resolution would be 320x240.  Sorry for not putting it in the last post.

---

### Post by Henrik on 2006-08-25
Yeah sorry, those default magnifier settings are terrible. The Gnopernicus settings panel is actually hiding uder that box making it even worse.

You have to left click on the taskbar entry and select move to move it -- or Alt-Tab to it and press Alt-space + M to move.

Only then can you get to the settings where you can change the position of that window. Once in a sensible position it should also show some content.

Have you tried installing kmag? It doesn't have tracking yet, but is otherwise quite good.

I see your point about the screen resolution option. It's a real hack though; I thing I would rather try to get magnification working properly.

The Orca reader/magnifier is already better in many ways, though you would need to install Edgy to try it. In a few days it should appear on the (by then smaller) Live CD ISOs.

---

### Post by Declan Moriarty on 2006-08-25
Thank you very much for replying so quickly.  I did manage to move the preferences menu, and got the magnifier settings up.  Changing the placement of the magnification "window" I was able to move it to the left.  The dimentions were identical to the original, even though I changed the "Right" and "Bottom" parameters(that should have changed the shape of the box?).  I was able to start speech (eventually).  However I think it is dying silently.  I could not get it to work apart from a few words when starting it.  Then I tried to re-enable it.  It then reverted back to saying speech was unavailable.

The magnifier throughout remained a white box with no border as if it was a window on a program that was dying, and the window space hadn't been updated.  Are there any issues with GeForce graphics cards or the 64-bit version?

---

### Post by Declan Moriarty on 2006-08-26
Trying it again.  If you logout after changing the position of the window and log back in again, the magnification window moves to the new position and changes shape.  However it is still a white oblong.  There is no magnified image in it.  Also the speech option doesn't work.  I tried to use the "Blindness" option today, and I had to relogin to get the speech.  It still didn't work properly.  It spoke the layer key but nothing else.  It also promptly became "Unavailable".  I suspect that the Gnopernicus package on this CD isn't working properly on my system.  I shall try the 32-bit version to see if that is any better.

---

### Post by Declan Moriarty on 2006-08-26
I haven't tried overburning because it may cause damage to my DVD drive (according to Nero).  I also have another computer with a DVD writer, and that was having problems verifying data, and I had done overburning on that machine in the past.  I replaced the DVD drive in that machine but to no avail.  I have since bought a new box and the verification problem has gone away.  So I am reluctant to overburn.  Also the new drive appears not to be able to write large CD's at the advertised speed for particular CD's.  E.g. writing perfectly at 16x on a rated CD of 52x.  But failing using the same brand at 48x (which is less than 52x).

---

### Post by alecjw on 2006-09-04
Just get a normal dapper CD and replace all occurences of "dapper" IN THAT CASE with "edgy" in /etc/apt/sources.list then:
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

