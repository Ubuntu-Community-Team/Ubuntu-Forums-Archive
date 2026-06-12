---
title: "[SOLVED] Started using Compiz Fusion. Got a few questions"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-08-03
First of, Compiz Fusion is very cool. It has all that Beryl had, plus a few more.

1) In Beryl, i could rotate my cube with my mouse scroll wheel. I can't in CF. Does anyone know where to set this option?

2) What is emerald exactly? Just a theme over Beryl and compiz?
I tried installing emerald when I first installed Ubuntu and Beryl, but it borked my system. So now I have a bad taste with it. Should I install it for Compiz Fusion? What additional features does it give over standard compiz-fusion ?

3) My pop ups, like right click menus and even the application menus are a little transparent, how can I make them totally opaque ?

4) Lastly, Beryl allowed to focus on the cube caps, but CF doesn't. meaning, when I make the cube cap as the face i want to show, it goes back to one of the side faces. Not that it matters, since you could hardly do anything on that face, but it sure kept my pesky cousins from doing anything on my machine even if I forget to lock my computer ;). This ain't important, just wanted to point out a difference :)

---

### Post by Inxsible on 2007-08-03
Another question I have is,

5) In the application switcher, i have Alt + Tab listed as for the next window. but it skips one window and take me to the next. like if i have 2 windows open, it just skips the other app and keeps coming back to the same window. If i have 3 different windows open, then it still skips, but atleast since its an odd number, i can eventually toggle between all windows.

Doing a Alt + Shift + Tab does not have this problem, however.

Does anyone else see this?

---

### Post by sir_tal on 2007-08-03
First off, I have compiz-fusion-extra installed, giving me several more plugins.  If you don't have what I'm describing, I recommend that you go through the package manager and install the fusion extras.  :)

3. Under General Settings, there are some Opacity settings, but I've not looked closely enough at them to be able to tell you what exactly to do, though that might point you in the right direction.

4. In Cube Rotate, there's an option to snap to the caps.

I can't help you wirh the rest.  :)  Hope this helps.

---

### Post by Inxsible on 2007-08-03
> **sir_tal said:**
> First off, I have compiz-fusion-extra installed, giving me several more plugins.  If you don't have what I'm describing, I recommend that you go through the package manager and install the fusion extras.  :)

3. Under General Settings, there are some Opacity settings, but I've not looked closely enough at them to be able to tell you what exactly to do, though that might point you in the right direction.

4. In Cube Rotate, there's an option to snap to the caps.

I can't help you wirh the rest.  :)  Hope this helps.
I have already tried different opacity settings. even disabling it. doesn't seem to work.

thanks for 4). at least I know what the issue was :)

---

### Post by atomkarinca on 2007-08-03
1) i've been looking for that for days now but i couldn't find it yet.
2) emerald is just a windows decorator like metacity. a little bit fancier i should say. it worked fine with beryl but i guess compiz doesn't like it very much.
5) i guess it's a bug. when i first installed fusion i got the same problem. i don't have it now. maybe with recent updates they fixed it. i used this guide: [http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

---

### Post by Inxsible on 2007-08-03
> **atomkarinca said:**
> 1) i've been looking for that for days now but i couldn't find it yet.
2) emerald is just a windows decorator like metacity. a little bit fancier i should say. it worked fine with beryl but i guess compiz doesn't like it very much.
5) i guess it's a bug. when i first installed fusion i got the same problem. i don't have it now. maybe with recent updates they fixed it. i used this guide: [http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

So installing emerald gives problems. what kind of problems?

So are you saying that after using that guide the problem disappeared for 5?

I used Vorian's sticky in the desktop enhancement section. maybe i should do a
sudo aptitude update

---

### Post by atomkarinca on 2007-08-03
> **Inxsible said:**
> So installing emerald gives problems. what kind of problems?

not giving problems per se but i couldn't get window decorations using emerald. this is for me of course, i have seen many people got it working quite well. you can install and switch back and forth to try it out. no harm done.

> So are you saying that after using that guide the problem disappeared for 5?

yes, now i don't have that problem anymore. but again it should be solved by the updates. vorian's repos are not updated that frequently i guess.

---

### Post by Inxsible on 2007-08-03
Do you think i should re-install it then using the link you provided ?

will i have to remove my existing install to do that

---

### Post by smah77 on 2007-08-03
1.  Viewport mouse switch is the plugin you're looking for.

---

### Post by Inxsible on 2007-08-03
> **smah77 said:**
> 1.  Viewport mouse switch is the plugin you're looking for.Sweet !!!

thanks

---

### Post by Lord Illidan on 2007-08-07
I managed to change the opacity of the menus.

From Opacity Settings, select Window Opacities, and set the Window Opacity Values to 100. There is a bug in the slider, so type it in.

---

### Post by Inxsible on 2007-08-07
Thanks, I shall try that tonight ! :)

Now, only if someone could answer Q5 about the Alt + Tab bug ....

---

### Post by UMDGaara on 2007-08-07
I have the same problem with Alt+Tab skipping windows (but not Shift+Alt+Tab). It sure is annoying.

---

### Post by Inxsible on 2007-08-07
> **Lord Illidan said:**
> I managed to change the opacity of the menus.

From Opacity Settings, select Window Opacities, and set the Window Opacity Values to 100. There is a bug in the slider, so type it in.
Hey Illidan, could you point out where it is?

I have attached the CCSM that I have for Opacify

---

### Post by Inxsible on 2007-08-07
Never mind. I found it under General Options and Opacity Settings. 

Had to edit the rule and change the opacity to 100 which was defaulted to 89. Works now :)

---

### Post by Inxsible on 2007-08-08
Solved the alt + tab bug, by going to System --> Preferences --> CCSM --> app Switcher.

Go to Actions Tab. Double click on the Next Window, (NOT Next Window (all windows) )
Click on reset to default button which will change the value from alt + tab to ctrl +alt + tab.

So the bug is that altho the default is ctrl + alt + tab, CCSM is shipped with alt + tab which conflicts with the alt +tab of Next Window (All Windows)

All problems solved :)

---

### Post by UMDGaara on 2007-08-09
You are a hero among men.

That worked perfectly, thanks!! I like my alt-tab to be for All Windows, so this is perfect.

Cheers

---

### Post by Paul133 on 2007-08-14
Should that be filed in a bug report and/or stickied?

---

