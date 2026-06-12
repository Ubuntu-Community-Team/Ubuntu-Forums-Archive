---
title: "skype icon distorted"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by darek1176 on 2007-07-18
I just switched on my laptop today and noticed that the skype icon in the gnome-panel is totally distorted and blurred. It was not the case yesterday. I am running Feisty with compiz-fusion. Skype is Beta 1.4. Anyone knows the reason?

---

### Post by happy-and-lost on 2007-07-18
It's probably not using a suitably sized PNG file, and instead using a scaled down SVG which is the cause of the apparent blurring.

---

### Post by expatCM on 2007-07-18
I have noticed that the icon which appears in the system tray has changed at least twice in the last day.  The green circle / white tick is the same but the background making up the square has taken a different form.  For example at present there is a horizontal white line with the top a gray gradient and the bottom half is black.   I am certain that was not the case earlier in the day ....

---

### Post by darek1176 on 2007-07-18
This is happening to me as well

---

### Post by expatCM on 2007-07-18
very strange ....  in the time it took to make this post it changed again ... now it is a pale yellow background.  I did not notice it change but .... it did...

---

### Post by satkata on 2007-07-18
It happened the same to me, too, just after I installed the backported qt 4.3 packages this morning.
It must have something to do with that as It wasn't so till yesterday, when I had qt 4.2.3 installed.

-----
Well, I just disabled all the gui effects with qtconfig-qt4 and now the skype systray icon has a white background, while my panel is transparent, so it doesn't look beautiful. :(

Hoping the next Beta Update will resolve this.

---

### Post by nike984 on 2007-07-18
I'm in the same boat. :(

---

### Post by darek1176 on 2007-07-18
I am not sure it is connected with installing anything. I did install nothing yesterday and the icon was fine. Now it is in a strange black box... and no way to resolve it

---

### Post by soro2005 on 2007-07-18
same here. I go with the upgrade of the qt backport for an explanation.

---

### Post by robbie75 on 2007-07-19
Same problem for me too... :-(

---

### Post by cool_penguin on 2007-07-19
Exactly the same problem on my Ubuntu as well as my friend's Ubuntu. Someone please help. I noticed this today after some Ubuntu update this morning.

Any help would be greatly appreciated.

Thanks a lot in advance.

Kind Regards,
Harry

---

### Post by cool_penguin on 2007-07-19
I also tried to re-install Skype twice using Synaptic Package manager, but the problem persists. :(

---

### Post by robbie75 on 2007-07-19
take a look here guys: [https://bugs.launchpad.net/feisty-backports/+bug/126766](https://bugs.launchpad.net/feisty-backports/+bug/126766)

---

### Post by nike984 on 2007-07-19
[https://bugs.launchpad.net/feisty-backports/+bug/126766](https://bugs.launchpad.net/feisty-backports/+bug/126766)

It seems that a fix has been uploaded,
let's wait for a little bit more or you can revert back to qt 4.2.3

[http://forum.skype.com/index.php?showtopic=91928](http://forum.skype.com/index.php?showtopic=91928)

---

### Post by expatCM on 2007-07-20
yes but from a practical stance whilst it does not look too pretty does it actually do any harm?  What does not work as a result of this?   At the end of the day this is beta software and happiness will no doubt follow the stable release :)

---

### Post by satkata on 2007-07-20
I have installed an update of the backported qt 4.3 packages and everything seems fine now.

So, it wasn't skype fault and I am happy, that the ubuntu guys reacted so fast. :)

---

