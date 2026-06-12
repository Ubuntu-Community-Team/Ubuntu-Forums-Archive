---
title: "OK, now this is WEIRD... can't start Ubuntu (kinda)"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by geezas on 2006-12-17
Help... I woke up today, ready for some more Ubuntu exploration (3rd day), and...
I enter my username and password - everything is fine.  Ubuntu starts quickly loading up.  Desktop appears with the panels which are empty (because it's still loading), except for the red turnoff button.  I can move my mouse for about two or three seconds until it stops.  Few more seconds of that nice little desktop and then the screen flickers couple times and the login screen pops up again...  I login myself and same thing happens...  I restarted - same thing.  I clicked on options and chose the degault session, I think - still the same crap... ;/

Anybody had similar experiences?  Give me some feedback people...

P.S. - last night I was changing my panels from default.  I was rearanging the panels, the buttons, the clock, etc.  Nothing serious.  I made them half tansparent.  When I was saying about empty panels when the desktop shows up, they have a default background, not the transparent one.  Can it be that when ubuntu tries to change it to my settings something happens?  Maybe this whole problem has something to do with the video card or it's drivers?  ...Cause when browsing with firefox and in couple other cases, there is problems with redrawing.  In firefox, whenever I scroll the page, half of the text disappears, so I have to press F11 or press CTRL+A to get it redrawn quick.

Sorry for the long post, but this is an "emergency" ;]
Thanks for anyone who tries to help

---

### Post by macogw on 2006-12-17
What kind of graphics card is it?  That could explain the Firefox thing (low RAM would too...so would it not knowing if you had dedicated VRAM).  I don't know about your login being kicked off though.

---

### Post by geezas on 2006-12-17
VRAM - you mean Swap?  Swap is 1 gig, RAM is 512 mb...  Video card is Savage 4 (32 mb).  I also have a pretty new radeon on my other computer which I could switch,  but Ubuntu was working the first few days...  it should work now....  I didn't loose my hopes yet ;]

---

### Post by steve.horsley on 2006-12-17
It is probably something to do with your user settings. You could try renaming your home directory and making yourself a new one that doesn't contain those settings. To do that, press Ctrl-Alt-F2 to get a text login prompt, log in with your name and password, and then use these commands (I assume your user name is geezas):
[B]cd /home
sudo mv geezas geezas-old
sudo mkdir geezas
sudo chown geezas:geezas geezas[/B]
Then Ctrl-Alt-F7 and try logging in again.

---

