---
title: "click lock on gnome ubuntu"
date: 2007-07-04
forum: Assistive Technology &amp; Accessibility
---

### Post by sach87 on 2007-07-04
Hi everybody!

It's been quite a bit since i moved from win to lin/ubuntu, and i'm really happy about it, except for  the fact that I can't find anything similar to clicklock (win xp function). **To make long story short, having mobility problems, i need the left mouse button to be held without keeping it clicked** so that i can make drag&drops and such much more easily.

is there any solution?? thanks

sach

---

### Post by frafu on 2007-07-06
Hello, 

Have you already considered using dwelling? You can find it included in the [mousetweaks]("https://wiki.ubuntu.com/Accessibility/Specs/MouseTweaks?highlight=%28mousetweaks%29") that are currently being developed. 

[Here is the blog]("http://gerdk.blogspot.com/") of the developer, where you can find version 0.1.0 of the mousetweaks. 

I will attach the current version 0.1.2 to this post. 

Dwelling with a window to choose click type seems to work correctly; however dwelling with gestures has a few issues at the moment. But please keep in mind that this software is currently in development and consequently may not work properly. If you decide to use it, it is at your own risk. 

If you need help installing the mousetweaks, do not hesitate to ask, as you have to compile it yourself. (There is no package available yet.) 

Have a nice day. 

Francesco

---

### Post by sach87 on 2007-07-06
Wow! :D i'll give it a try immediatly! 
Hope to be able to compile it myself, otherwise, i'll give you a call ;)
thanks a lot in the meantime!!!

---

### Post by sach87 on 2007-07-06
Ok I give up... :(

here's the problem:

when i launch the configure script of mousetweaks the result is that i don't have gconf 2.0.
i downloaded gconf 2.18, but i'm missing another 3-4 dependencies, such as glib 2.9.0.
i downloaded glib 2.9.6 and installed it streight, but still gconf won't find it.
And this is where i gave up...

Any suggestion to make it simpler? because typing all that stuff in the shell is taking a bit too much of my time... typing with only one finger...you know...:)

Thanks for your time and help!

---

### Post by frafu on 2007-07-06
I have open a thread for the [feedback of the mousetweaks]("http://ubuntuforums.org/showthread.php?t=494037"). Please don't hesitate to post any issues, comments and suggestion.

---

### Post by frafu on 2007-07-06
Hello, 

Sorry, I overlooked your last message. 

I have it running on my system, but I am not very knowledgeable about it. I will have a look to figure out what is needed and keep you informed... 

Have you installed the build-essentials package? Moreover, you have also to install the packages that ends with "-dev". 

Finally, I always use the Synaptic Package Manager to install new packages... I think that less typing is required this way. 

Francesco

---

### Post by frafu on 2007-07-07
Hello sach87,

You have to install the following packages:

libgconf2-dev
libglade2-dev
libpanel-applet2-dev
libatspi-dev
libdbus-glip-1-dev

I used the Synaptic Package Manager to install them, as it also installs their dependencies. 

From your previous post, you seem to know that you have to type the following in the terminal: 
cd <to the directory containing the mousetweaks>
./configure
make
sudo make install 

If you try it again, could you please tell me whether it worked? 

Francesco

---

### Post by sach87 on 2007-07-09
hey Francesco!
i've just seen your post and tried out what you suggested... and it worked in first place!
the program is really nice!
the only bad thing i found, for me, is the timer on the dwell function... can I disable it keeping the function activated?
thanks again for your precious suggestion!

---

### Post by frafu on 2007-07-10
> **sach87 said:**
> hey Francesco!
the only bad thing i found, for me, is the timer on the dwell function... can I disable it keeping the function 

I am glad that it works for you too and to hear your feedbacl. 

Sorry, but I don't understand what you mean: the timer is necessary to specify to the dwell function how long it has to wait after the pointer stops moving before automatically doing the click.

Could you please tell me how you want it to work without the timer? 

Francesco

---

### Post by sach87 on 2007-07-10
sure! sorry I haven't been clear as i thought....
What I meant is more or less this:
the timer is really useful if you cannot click by yourself, but if you can do it, the fact that it automatically clicks after a certain time may be a bit annoying. i.e. if you are on a webpage reading an article and you leave the pointer on a link, you are gonna click it, even if you didn't want to. 
So what i meant was that i would be more comfortable if i could click by myself but with the dwell activated. 
I'll give you an example of how i'd like it to work:
let's suppose i have to drag an object from the desktop to a folder. So i click on the drag function and then i look for the object i have to move. with the timer, if i stop to move the pointer while i try to find where the object is, after 2 seconds it will click and then go back to the left click option, and i'll have to do it again.  but if there wasn't any timer i could have waited as long as i wanted and then, once i found what i had to move, i coul have clicked on it, activating the drag function, moved it where i wanted and then clicked again to release it and go back to the left button.
Hope now i've been clearer...

---

### Post by frafu on 2007-07-10
Hello, 

What about these functions that are already present in mousetweaks: 

- there is a pointer capture applet shipped with the mousetweaks; if you move the pointer above the pointer capture area, it remains stuck until you release the pointer with a predefined way. Do a right click on the upper panel to get to the functions to add applets to the panel. you should find it among the accessibility applets. 

- for the drag&drop problem: you might try to get the habit to first locate the item to drag and afterwards set the dwelling to right click. 

- though it still has issues (for example it does not work in the Applications menu; but as you are able to click it may not matter), dwell click with gesture might also be useful to you

Anyway, I will suggest the following to the developer:

- Add none to the menu of the gestures in dwelling with gestures, so that it is possible to only activate specific click types instead of all

- Add a way to do the different click types, even if the user is only able to do a single left click; for example having a window with the different click types, and when the user does a left click, the clicktype selected in the clicktype window is simulated. These should also be useful to your specific problem. 

Francesco

---

### Post by critterbash on 2009-03-16
> **sach87 said:**
> Hi everybody!

It's been quite a bit since i moved from win to lin/ubuntu, and i'm really happy about it, except for  the fact that I can't find anything similar to clicklock (win xp function). **To make long story short, having mobility problems, i need the left mouse button to be held without keeping it clicked** so that i can make drag&drops and such much more easily.

is there any solution?? thanks

sach

Is there any solution to this, because I too have mobility problems and I'm in need of 'click lock' (as described above). I've tried 'dwell click', but sadly it doesn't suit my needs.

I use a Logitech Trackball with 3 buttons.

Please? Anybody?

---

### Post by TheWitness on 2009-05-05
I have the same issue.  I have just upgraded from Windows XP to Ubuntu 9.04 and the dwell ckick is not the same as ClickLock.  My concern for the gnome guys is that when in Windows, ClickLock has TitleCaps set on it which generally means "patented technique".  Microsoft does not make me happy.  Something like this should be available for all.

TheWitness

---

### Post by frafu on 2009-05-06
Hi, 

I have been told that it might already be possible to have click lock working in Ubuntu, once you know how to set it up. 

In fact, Ubuntu normally uses the evdev driver for the pointer and the keyboard, and the man page says that it supports the options "DragLockButtons" "L1 B2 L3 B4" and "DragLockButtons" "M1". 

Unfortunately, I don't know how to set it up. Maybe somebody with more knowledge about how to configure evdev can provide more help. 

By the way, could you please tell me if there are other use cases  for the click lock, apart the dragging of items? 

Cheers, 

Francesco

---

