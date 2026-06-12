---
title: "Drag'n Drop causes Ubuntu to crash"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-03-27
Hi,

nowadays my Ubuntu 7.10 frequently crashes when I try to drag'n drop items. I don't think that issue was there before, on some days the computer crashes up to 4 times, sometimes even if I accidently move the mouse while the button is pressed. 
The applications that are especially "sensitive" are Firefox, Miro, Songbird and such, Nautilus and other GNome application are not afflictled. So, it doesn't seem Ubuntu itself is the villain but is there anything I can do to make it more stable?


Andreas

---

### Post by c-ron on 2008-03-28
What kinds of items, and from where and to are you dragging and dropping them?

---

### Post by Djalmahal on 2008-03-28
Normally drag'n drop of such things of code that i drag from a firefox window into a terminal window works, even though i had it crash on me with such actions. More often it happens with elements that i (accidently) touch while press on the  mouse button and move it which are not "meant" to be dragged. It's unfortunalty that Ubuntu totally crashes in such situations, at least, on my computer.

Andreas

---

### Post by napolperro on 2008-03-30
I am having that same problem too, whenever I try to (or accidentally) drag an image or text from Firefox, or other programs... I have tried a couple fixes but to no avail.

Also the keyboard stops responding. I have 7.10.too.

---

### Post by jmw5098 on 2008-03-31
I'm also experiencing the same thing.  If i click and drag (not even objects) too fast, ubuntu will freeze and only move the cursor. Also running 7.10

Anyone have any updates?  If not, I'll wait until Hardy Heron comes out...

---

### Post by MattinTucson on 2008-04-04
I am having problems with 7.04 and nautilus.  I had Banshee and EasyTag open along with nautilus, having just changed the tags so that Banshee can find the cover art (I really hate how Banshee implements this, as I have to change all my tags).  Something got messed up, and now whenever I open the folder that contains those files with nautilus, it crashes.  Looking at the info on top, it uses ~100% of my processor (though I have dual core) while the memory starts out at only a few percent, less than 5.  However, over ~15 minutes the memory will get eaten up.  However, I can and have moved the files using the command line, and opened the folder with Thunar without trouble -- even renaming them.  I have even put the files on a USB drive, transferred them to another folder with another computer, and brought them back.  Nautilus still doesn't work.  It is an extremely annoying problem.

---

### Post by Tomatz on 2008-04-04
8.04 is out in the next few days hopefully an upgrade will fix the issue :)

---

### Post by XanderKaplan on 2008-04-17
not that we need more people reiterating the problem... but I've got the same here and I just want to say it's pretty much anything that involves a drag (text, tabs, links, icons...) I haven't done too much experimentation, as it's usually five or six minutes per restart... I'm definitely with you in hoping that hardy fixes this

---

### Post by napolperro on 2008-04-17
Hey, just posting this to let you know (if someone is still having this problem) that I have fixed it in my computer.

Well, I couldn't find a solution on the internet, just people with the same problem, and then somewhere I found a reference that Compiz may be the culprit... so I disabled all the visual effects, and now I can drag 'n drop normally in Firefox! (and other apps that were affected) I know it is not the kind of solution we (or at least I) would like, but hey, at least my computer does not crash every 15 minutes :)

As I said, I dont know if someone had already found out that.. I would not be surprised if that was the case anyway.   :P

Now I have to maybe wait for hardy to see if I can enable the nice effects again..  :confused:

---

### Post by XanderKaplan on 2008-04-23
**found a definitive solution to Ubuntu freezing when you drag items**


Hey! you're right, it was compiz... but being the meticulous person i am, I went through and checked the various plugins and found reflection(under effects, icon is a striped window) to be the culprit. I'm now happily dragging, dropping, and crash free :)

---

