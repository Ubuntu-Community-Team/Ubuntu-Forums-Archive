---
title: "how to slow down qjoypad?"
date: 2010-11-14
forum: Assistive Technology &amp; Accessibility
---

### Post by emmdarakis on 2010-11-14
Hi all and thanks for the great work,

I am trying to help my sister to use a joystick for mouse input. I've fount qjoypad the best solution so far. 

The joystick she is using is an arcade type of joystick by Logic3. It's axes work in a kind of digital mode (they are either on or off - nothing in between) so that I have to use the "Gradient" mode in qjoypad.     

The problem is that even at the lowest speed (1 out of 100) the mouse pointer moves far too fast for my sister to control it accurately, especially when she tries to do small movements. 

I have tried the different options that qjoypad offers (linear, quadratic, power function etc) but nothing really changes. I have also tried (just in case) to slow down my mouse speed settings from System->Preferences without luck.  

So my question is is there any way to make the speed of the joystick/mouse pointer slower? If possible, it would also be great if an acceleration function could be defined to keep the speed low (improve accuracy) for small movements while larger movements can be done faster. 

Any help more than welcome. Thanks a lot in advance....

---

### Post by emmdarakis on 2010-11-18
Anybody??

---

### Post by BryanFRitt on 2011-03-31
(I didn't make QJoypad, just another user)

Ideas/Stuff you could try:

Get a higher resolution display, or if your monitor, and video card, etc... support it, set the resolution up higher.
(if QJoypad movement is based on pixels, and not fraction of screen, this will increase the time it takes to move the cursor across the screen.) 
Possible side effects: things get smaller, and more things fit on the screen at once, and it's just as hard to hit the target.

Maybe you could make the icons, fonts, etc... bigger, so it's not so hard to hit them.
Possible side effects: Less stuff on screen, things look uglier, etc...

Try a different joystick/controller. Maybe it'll work differently. 
Possible side effects: It's worse instead of better.

Try editing the source code. Maybe you'll be able to figure out how to change it to fit your needs.
Possible side effects: lots of time wasted, with no results, and all sorts of other issues, if you mess up the code. ?may have to manually delete /usr/local/bin/qjoypad, etc... from command line, or use a rescue CD? <- just using my imagination on this one.

Make your own program.
Possible side effects: lots of time wasted with no results. you have to use a rescue cd, or command line, to fix computer, basically same as previous idea, but probably more time spent.

Try doing any combinations of the above ideas. Although, side effects tend to add up.

---

