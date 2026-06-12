---
title: "Mouse wheel"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by antiwindows798 on 2007-01-26
In Windows, when I press and hold my mouse wheel, I can "drag" a picture in Firefox, for example, and move it around. I can do that in Ubuntu, although I can scroll through pages in Ubuntu but not "grab" a page/picture.

How to solve this? I have tried to edit xorg.config but that doesn't help.

---

### Post by citizenofnowhere on 2007-01-26
I grab pictures and drag them by holding down my left mouse button - does that work for you? (middle click on some systems is reserved for the clipboard, cutting and pasting links etc.)

---

### Post by antiwindows798 on 2007-01-26
No, I don't mean "drag and drop", I mean holding down the mouse wheel, or for that matter, clicking it once (if you do so under Windows a circle displays on the screen where you have pressed your mouse button, with four arrows in it) and when you move you mouse, the page automatically scrolls.

I want to be able to do that in Ubuntu.

---

### Post by citizenofnowhere on 2007-01-26
I see :) Try to be a little more specific next time.

In that case, go to your Firefox preferences (Edit->Preferences). In the advanced section look for auto-scroll and see if it's on. Mine wasn't on my default, after I did that middle clicking to autoscroll worked fine.

If that doesn't help, it's likely to do with what I mentioned above - the clipboard thing. Try typing in about:config in your url bar, and look for middlemouse.contentLoadURL and set it to false.

Hope that helps!

---

### Post by antiwindows798 on 2007-01-26
Yes that helps! And thanks! But wait, while I'm happy that I can do that in Firefox now (why wasn't that enabled by default in the place? Oh nm), I want to be able to do that in Ubuntu, not just Firefox.

---

### Post by citizenofnowhere on 2007-01-26
My pdf reader (Evince) does it by default. So does gimp. Most applications should have that supported. If they don't, it's probably somewhere in the settings.

Don't ask me why it isn't enabled :) I'm still wondering why FF2.0 doesn't force new windows into tabs the way 1.5 used to. Oh well...

---

### Post by antiwindows798 on 2007-01-26
Dude, just click on a link with your mouse wheel and Firefox will open it in a new tab :).

And yes, Firefox 2 is indeed different than Firefox 1.5. Actually, I have just switched to Ubuntu and I'm not very happy with Firefox (although it beats the **** outta Firefox 1.5 (which I used on Fedora)).

Should FF be more functional in Linux than in Windows? Click on the Bookmarks menu in FF in Windows, and drag and drop a bookmark in FF. It works, the Bookmarks menu doesn't disappear, but in Ubuntu, it does. There are some more issues with FF in Ubuntu.

BTW, thanks :)

---

### Post by citizenofnowhere on 2007-01-26
Chick, actually. ;-) 

And yes, I'd do that except some people like to open new windows using javascript. And when I'm on the laptop i have to hold down both left and right click to simulate middle click which isn't worth it - to each his own I suppose.

---

### Post by antiwindows798 on 2007-01-26
Oh cool, a chick that uses Ubuntu :D I wish there were more girls like you!

And yes, that sucks indeed on a laptop.

---

### Post by citizenofnowhere on 2007-01-26
Thanks. Geekiness runs in the family. You should see what my mum can do with my router settings ;)

Happy Ubuntu-ing

---

### Post by antiwindows798 on 2007-01-26
Cool. Unfortunately I can't say the same about my family (except about my mom too, lol). They are all a bunch of noobs (in everything, ROFL).

> Happy Ubuntu-ing

Thanks, but not quite yet. Do you by any chance know a way to configure Ubuntu to make me able to use *normal* character short cuts?

By "normal" I mean that the following should work, for example:

Alt + Ctrl + c = copyright notice
or
Alt + Shift + c = copyright notice
or
Ctrl + Shift = copyright notice.

Replace "c"  with "5" and that should get me the Euro sign. And so on. In other words:

c = copyright
t = trademarked
5 = Euro sign.

And so on.

---

### Post by citizenofnowhere on 2007-01-26
Same person, different thread dude :) Still can't help you any more than that.

---

### Post by antiwindows798 on 2007-01-26
ROFL! I didn't notice that, ROFL. Well, thanks again anyways. I'm too busy getting things to work here to think straight, ROFL.

---

### Post by sympeltun on 2007-02-04
I had the same problem, read this thread worked like a charm! thanks citizen

---

### Post by Steve H on 2007-07-02
Thanks for the heads up about the auto-scroll, that has been bothering me for a while....

I kind of missed it

Thanks again

:p

---

### Post by buster8079 on 2007-11-28
Instead of auto-scroll, you may be interested in the Firefox extension: [**Grab and Drag**]("https://addons.mozilla.org/en-US/firefox/addon/1250")

---

