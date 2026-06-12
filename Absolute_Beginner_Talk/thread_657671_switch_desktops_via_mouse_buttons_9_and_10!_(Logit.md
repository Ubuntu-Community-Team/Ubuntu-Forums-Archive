---
title: "switch desktops via mouse buttons 9 and 10! (Logitech MX510)"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by MTiN on 2008-01-03
Hey there!
I am using the Desktop Wall (compiz) and wanted to be able to switch to the next/previous desktop with my Mouse Buttons 9 and 10 (Logitech MX510, the buttons above and below the scroll wheel)
But no matter what I enter in ccsm->Desktop Wall->Actions->Move Left/Move Right it just doesn't work!
I think I already tracked down two problems:

the first thing is, that I can't assign ANY mouse button to this action! for example, when activating Cube and Rotate Cube I can use Mouse Buttons 1-8 perfectly fine to rotate the cube, but I cant use them to "Move Left" or "Move Right"
the next problem is, that it seems like my mouse Buttons 9 and 10 don't work at all for the actions in ccsm, also not for rotating the cube as I just said. While looking at the output of xev I noticed that pressing these two buttons (used for scrolling up and down) produces much more then just a ButtonPress/Release Event for their specific Button number (9 or 10) additionally, the Button 9 produces Button 4 (Scrollwheel up) outputs if I hold it and Button 10 gives Button 5 Messages (Scrollwheel down)...and there are also a few KeyPress/Release events listed...
so, yeah, since that didn't look good at all I almost abandoned this approach already, but maybe someone of you can help me there!

The next thing I tried is setting up xbindkeys and xevkbd to do what I want. This almost seemed to work, xbindkeys is succesfully capturing the events from the Buttons 9 and 10 (and they don't produce that scrolling anymore) but it seems like the key combinations sent by xevkbd dont get read by that compiz-stuff or whatever!
this line:
"xvkbd -xsendevent -text "\[Control]\[Prior]""
works perfectly fine in Firefox (previous tab), but if I set the Action "Move Left" in ccsm to Control + Page Up and press the same mouse button nothing happens!!!!!!! If I use the keyboard to press Control+PageUp then it works...in firefox as well as to change desktops...

aaargh well I've been fiddling around with this damn mouse for a while now and its starting to get on my nerves :roll:
just installed ubuntu a few days ago so I'm not really into all that linux-stuff and its pretty late here now, I hope I didn't just mix up something stupid :mad:
but anyway I'd really appreciate some help guys :)

---

### Post by MTiN on 2008-01-04
hey, I still have this problem! it just wont work, no matter what I try...can't someone please help me?

---

### Post by notepad on 2008-02-26
apparently imwheel is the go. how far did you get with this?
im looking into it now so i can change desktops quickly while i am using virtualbox in fullscreen mode on say desktop 3 and change to other desktops. i realise i will need to use a keyboard keey at the same time to 'uncapture' the mouse.
let me know if youre still keen so if i work it out i can tell you how i did it.

---

### Post by MTiN on 2008-02-26
that would be great if you'd find something!
I didn't look into this any further, enabled desktop switching if I move my mouse to the screen border...but it would definetly be a great advantage if I could use these mouse buttons!

---

### Post by notepad on 2008-03-01
i setup btnx to take mouse clicks and send them as key sequences. i configured my mouse buttons 8 and 9 to switch desktops left and right. while gnome is still loading, the mouse button desktop switching works. as soon as gnome is finished loading, the mouse button thingy stops working.

it sounds to me like what youve done would work for you if my btnx thing would work for me. something is stopping our mouse button events being sent as key sequences. this is odd because the btnx thread starter (and maker of btnx)  [http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656) refers to a post within the thread [http://ubuntuforums.org/showpost.php?p=3812017&postcount=550](http://ubuntuforums.org/showpost.php?p=3812017&postcount=550)
that told me how to configure btnx to send mouse clicks as the key sequence to switch desktops. one assumes the writer of that post was able to use his mouse to switch desktops.

---

### Post by notepad on 2008-03-02
okay this is just ridiculous. using xev i can see all of my mouse buttons working perfectly and in fact they always were. btnx did nothing to change that and any editing ive done to xorg.conf has made no difference other than to change button numbers and which buttons work as the scroll wheel.

i can configure my side buttons to work as the scroll wheel, and i can configure my scroll wheel to switch desktops. but no matter what, i cant get the side buttons to switch desktops (except during gnome loading).

the scroll wheel desktop switching works perfectly but it works all the time. i mean if i want to scroll a document, it begins to scroll and then my desktop switches. 

the dumb thing is that i can get my side buttons to become scrollers and my scroller to act like i want the side buttons to behave, but that setup is hopelessly unergonomic. 

note also that without btnx, my side buttons work as forward and backward in firefox without any configuration whatsoever. even with btnx configured to switch desktops with the side buttons, firefox still reads the side buttons as forward and backward. no idea how its doing it but plenty of other users reported this being the case with their microsoft intellimouse explorers.

---

