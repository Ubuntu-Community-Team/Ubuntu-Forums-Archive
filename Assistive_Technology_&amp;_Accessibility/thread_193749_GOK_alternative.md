---
title: "GOK alternative"
date: 2006-06-10
forum: Assistive Technology &amp; Accessibility
---

### Post by ashrack on 2006-06-10
On our school I turned 4 WXP PCS into DAPPERS. But the GOK's keyboard is very bad. First of all its not a true QWERTY keyboard. And some letters like CAPSLOOCK arent even fully seen. And its working very slowly and also when pressing SHIFT and then clicking on a letter it will still be lower case letter in OOO.

Are there any alternatives that would be similar to functionality as is WinXP's on screen keyboard, dont care even if they cost money.

---

### Post by Henrik on 2006-06-11
Yes I agree that GOK is weak in many ways. I did a review of it here: [https://wiki.ubuntu.com/Accessibility/Reviews/GOK](https://wiki.ubuntu.com/Accessibility/Reviews/GOK) some months ago where I point out some flaws, but you might have found others.

Sadly, I don't think there are any alternatives available for Linux, even for money.  GOK also doesn't look that easy to fix. To get around that we have started a new project, the Simple On-screen Keyboard (SOK). You can read the specification here: [https://wiki.ubuntu.com/Accessibility/Specs/SOK](https://wiki.ubuntu.com/Accessibility/Specs/SOK)

I'm working with a Google Summer of Code student (Chris Jones) on this, so we hope to make good progress in the next few months. We would of course welcome suggestions, testing, code review and help in writing plug-ins. I'll post some bounty ideas in the Launchpad bounty tracker and so if you do have some sources of funding you might be able to help out there.

---

### Post by frafu on 2006-06-11
@ashrack

I have been told that there is another input-method than onscreen keyboards. It is called Dasher and you can find it here: 
[http://www.inference.phy.cam.ac.uk/dasher/](http://www.inference.phy.cam.ac.uk/dasher/)

As I haven't tried it yet, I can't tell you much about it. But maybe it can help you. 

frafu

---

### Post by ashrack on 2006-06-12
[QUOTE=frafu]@ashrack

I have been told that there is another input-method than onscreen keyboards. It is called Dasher and you can find it here: 
[http://www.inference.phy.cam.ac.uk/dasher/](http://www.inference.phy.cam.ac.uk/dasher/)

As I haven't tried it yet, I can't tell you much about it. But maybe it can help you. 

frafu[/QUOTE]
just looked over some pics of DASHER and I find myself asking, what the heck is that??

---

### Post by Henrik on 2006-06-12
Hehe. It is actually a text entry system, and I think it can ve quite efficient. The kids might enjoy it. It's a bit like a video game :) 

It's also easy to install in Ubuntu dapper, just search for it in 'Add Applications'. One problem is that it enters text into its own field, not another program, though I think that should be quite easy to change.

It takes a little while to learn how to use it, and after a while it adapts to your usage. It's also woth adjusting the settings for better individual performance.

---

### Post by frafu on 2006-06-12
As far as I have read/heard it is used to type by using the pointer; but I can't tell you more as I could not try it yet.

---

### Post by tukster on 2006-07-24
try xvkbd (it's in repos).
works ok for me since it's simpler than gok.
i use it for text input on my tablet pc

[screenshot]("http://homepage3.nifty.com/tsato/xvkbd/xvkbd-normal.gif")

web: [URL="http://homepage3.nifty.com/tsato/xvkbd/"]http://homepage3.nifty.com/tsato/xvkbd/
[/URL]

---

### Post by Henrik on 2006-07-24
SOK is also ready for testing now. See: [https://wiki.ubuntu.com/Accessibility/Projects/SOK](https://wiki.ubuntu.com/Accessibility/Projects/SOK)

Download: [https://wiki.ubuntu.com/Accessibility/Projects/SOK/dev](https://wiki.ubuntu.com/Accessibility/Projects/SOK/dev)

Just download the .deb and click on it to install with gdebi.

---

### Post by tukster on 2006-07-24
> $ sok
Traceback (most recent call last):
  File "<string>", line 1, in ?
ImportError: No module named scripts.sokSettings
Traceback (most recent call last):
  File "/usr/bin/sok", line 3, in ?
    s = Sok()
  File "/usr/lib/sok/sok.py", line 62, in __init__
    gtk.main()
KeyboardInterrupt


hmm when i start it, i see only a blank screen, do i need to configure it somehow?

---

### Post by Henrik on 2006-07-24
Yes, sorry. Please run 'sok-settings' first. That creates a .sok directory. Select the 'ubuntu' keyboard and close the window. Then run 'sok'.

---

### Post by dabear on 2006-07-24
There seems to be a dependency of a virtkey module not present in my system..

I didn't manage to solve the issue by examining the source, but two other questions arose:
-Is there any reason you are using tabs for indenting?
-Is there any reason you are using old-style classes?

---

### Post by tukster on 2006-07-25
ok thx got it working, but ... :D 
i'm not able to type in any text. i fire up gedit, start sok and when i try to type anything nothing really happens in gedit. am i being stupid here?

edit:
i'm being stupid, somehow i've messed up window focusing with xgl/compiz
sorry ppl lol

---

