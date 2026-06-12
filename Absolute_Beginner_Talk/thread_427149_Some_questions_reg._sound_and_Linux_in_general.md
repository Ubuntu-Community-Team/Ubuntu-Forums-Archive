---
title: "Some questions reg. sound and Linux in general"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by wat3r on 2007-04-29
Hello!
On my laptop, I have some "function-keys", i.e., if you want to change the volume, you press the "Fn"-key and up or down on the keyboard. But my problem is that it changes the wrong volume. It changes the volume knob marked "Front" in ALSA, but I want to change it to "PCM". How do I do this?
Also, I am experiencing that my computer hangs up a lot. Everything freezes gradually, until it goes to a complete stop, where the mouse is the only thing I can move. That just happened now when I am writing this. First, nothing comes up when I write. Then Firefox stops working. Then I can't open any windows at all. It seems like its only the GUI that freezes or something, because when it unfreezes, the text that didn't come up when it started freezing up, just pops up. Also, the mp3-player kept playing, and even changed to a new song.
I just freshly installed Feisty Fawn 7.04, but I had the same problems before I did this. When I had the old installation, these errors started happening when I upgraded to Feisty Fawn.

Sorry if my english is bad.

---

### Post by gilgongo on 2007-04-29
Laptops are pretty tricky in this regard. If the firmware keys are working at all, it implies that Linux is driving them in some way - perhaps yuo can try Googling for your laptop make and Linux and see what package might be handling this and whether you can configure it accordingly. 

As to the freezing up - I too have experience this but I can't track down a cuase. It seems to happen at random intervals.

---

### Post by wat3r on 2007-04-29
> **gilgongo said:**
> Laptops are pretty tricky in this regard. If the firmware keys are working at all, it implies that Linux is driving them in some way - perhaps yuo can try Googling for your laptop make and Linux and see what package might be handling this and whether you can configure it accordingly. 

As to the freezing up - I too have experience this but I can't track down a cuase. It seems to happen at random intervals.

The keys are working, and I get up a bar that shows the increasing and decreasing of the volume, but it kind of changes the wrong volume, as mentioned in the first post. It changes A volume, but not the correct one. The volume it changes, is tagged "Front", but I want to change the volume that says "PCM".

---

### Post by wat3r on 2007-04-29
Small update: It seems it is Firefox that is the problem with the freezing, but I can't say that for sure.
Small update #2: Now I'm almost 100% positive that it is Firefox that is causing it. Because earlier, I used the computer, but not with Firefox open or in use, and it did not freeze. Now it freezes more and more often, when I use Firefox. I never had this problem with Ubuntu 6.10, so this is pretty weird.
When Firefox freezes, it just won't respond. If I try to minimize it, it works, but when I try to maximize it again, there is just a white screen that comes up. If I try to use other programs when Firefox freezes, they freeze gradually as well.
Also, I figured out how to change what volume control the hotkeys should be changing. In my case, I just went to System -> Preferences -> Sound, and selected PCM.

---

### Post by wat3r on 2007-04-29
I tried to look around a little, and I seem to have found the problem causing the freeze ups. I found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587)
Someone on that page, linked to another related bug report:
[https://bugs.launchpad.net/ubuntu/+bug/104581](https://bugs.launchpad.net/ubuntu/+bug/104581)
Basically, what is discovered in these bug reports, is that the bug does not show any more if you have a CD or a DVD in your CD/DVD-reader. This has been confirmed by many people in both pages. Let's hope the developers make a fix for this, because in my opinion, that is one of the most silly bug-fixes i've ever heard of.

---

