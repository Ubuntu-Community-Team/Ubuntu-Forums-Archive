---
title: "Oops. Problems with panels"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-04-13
I've recently installed KDE, you know, to try it out again. So, I installed it, and logged out and back in to KDE. I tried to customize the bars, then gave up and logged back into GNOME. Now all my panels seem to be slightly too big, so now my panels seem to stack. I've tried to shrink the panels, but they are already as small as they can be(28) Here's a screenshot.

 [IMG]http://i68.photobucket.com/albums/i2/Super-noob/Screenshot-2.png[/IMG]


 How do I fix this?

---

### Post by SanjoEel on 2007-04-13
It looks like you need to adjust your resolution, have you tried that yet?

---

### Post by ZeroWing on 2007-04-13
Just tried. Didn't work.

 [EDIT] By the way, all of the sudden my fonts are now black, on a black background. [/EDIT]

---

### Post by SanjoEel on 2007-04-13
Did you set gnome as default?

---

### Post by ZeroWing on 2007-04-13
> **SanjoEel said:**
> Did you set gnome as default?

 Yep.

---

### Post by ZeroWing on 2007-04-13
I looked at another post about changing panel sizes, and I found that the minimum allowed size for the panels in pixels is around the lower-twenties. My panels are at 28. Minimum. How can I change this?

---

### Post by ZeroWing on 2007-04-13
You know what? I've had linux for 'round a month, and it still isn't mine. All I've got on here is a couple videos, all backed up, but it still isn't mine. What do you think about just wiping it? Formatting all the non-windows partitions, and using the free space.

 Is it worth it, or can I easily fix this?

---

### Post by SanjoEel on 2007-04-13
Hehehe, I've been using Ubuntu about the same amount of time as you, Zero. I was just suggesting what I would have tried first. This is probably easily fixed and you and others could learn something from figuring it out and fixing it, but theres nothing wrong with just starting from scratch again sometimes, that's for sure, especially when if you've been messing around with it a lot. :D  Maybe someone else has some ideas?

---

### Post by adriantry on 2007-04-14
> **ZeroWing said:**
> You know what? I've had linux for 'round a month, and it still isn't mine. All I've got on here is a couple videos, all backed up, but it still isn't mine. What do you think about just wiping it? Formatting all the non-windows partitions, and using the free space.

Is it worth it, or can I easily fix this?

And you've probably also installed the gtk-qt-engine.

This program formats you're gtk apps so they look more consistent with kde, but it also has some unexpected effects when you log back into gnome.

You can either uninstall this package, or turn it off in the KDE Control Centre, and I think you're problem will vanish!

Is it worth it? Of course it is!!! If you stop experimenting you'll get less problems like this, but also have less fun and learn a lot less.

Adrian

---

### Post by kvonb on 2007-04-14
It might be the panel background image that you are using which is limiting the size.

You need to run gconf-editor, simplest way is to just type that in a term, or you can edit your menu (right click on the start button), then enable it in the system sub-menu.

In gconf, select Apps->Panel->Toplevels, then for each sub entry in there, open it and click on Background, then click the little box named "Fit" and magically your panels will look tons better :)

---

### Post by ZeroWing on 2007-04-14
Did both of those. Reset the x-server. Still the same. 


 This sucks....

---

### Post by ZeroWing on 2007-04-14
Bump :(

---

### Post by N Clement on 2007-04-14
Well, if you are looking for opinions...or if you aren't, here's mine:

1)  I would copy all files that I wanted to save to another partition or hard drive or even a zip drive if you don't have much.

2)  If you have any desparate ideas about how to fix the problem, this would be the time to try them.

3)  Use [this tutorial]("http://www.howtoforge.org/the_perfect_desktop_ubuntu6.10") to install a fresh install of Ubuntu 6.10 (not Kubuntu, cause I'm falling more in love with gnome every day).

*anecdote* My friend once launched KDE on top of Gnome by accident and it was pretty epic.  This might remove some stress, but I wouldn't try it; just get joy from imagining it.

---

### Post by ZeroWing on 2007-04-14
> **N Clement said:**
> Well, if you are looking for opinions...or if you aren't, here's mine:

1)  I would copy all files that I wanted to save to another partition or hard drive or even a zip drive if you don't have much.

2)  If you have any desparate ideas about how to fix the problem, this would be the time to try them.

3)  Use [this tutorial]("http://www.howtoforge.org/the_perfect_desktop_ubuntu6.10") to install a fresh install of Ubuntu 6.10 (not Kubuntu, cause I'm falling more in love with gnome every day).

*anecdote* My friend once launched KDE on top of Gnome by accident and it was pretty epic.  This might remove some stress, but I wouldn't try it; just get joy from imagining it.

 Seriously? I have to reinstall?

 Well, that sucks.

 So there are *no* other options...? Bummer.

 [EDIT] Aw, someone changed my title... [/EDIT]

---

### Post by kvonb on 2007-04-14
Create a new user account from the system menu, it will be completely standard.  See if you can change the menu sizes on that one.

---

### Post by ZeroWing on 2007-04-14
> **kvonb said:**
> Create a new user account from the system menu, it will be completely standard.  See if you can change the menu sizes on that one.

 *Oh, come on!* I just reinstalled! Why the *hell* didn't I think of that!? Son of a....

 Nevermind... I'm fine. I'll just re-customize everything...

 Sorry, I'm used to the Windows tradition: make an unstable operating system with tons of problems, and make it damn hard to fix them.

 I'm okay...

 [img]http://www.laptopdesk.net/images/exploding-laptop2.jpg[/img]

---

### Post by adam.tropics on 2007-04-14
reducing your panel font size allows you to make the panel smaller.

---

### Post by kvonb on 2007-04-15
Haha, sorry, I was maybe a few minutes slow on the reply!

I like the pic of the burning laptop!  That must be the new Microsoft anti-piracy policy in Vista, hahahah.

I'm starting to like Vista :D

---

### Post by ZeroWing on 2007-04-17
> **kvonb said:**
> Haha, sorry, I was maybe a few minutes slow on the reply!

I like the pic of the burning laptop!  That must be the new Microsoft anti-piracy policy in Vista, hahahah.

I'm starting to like Vista :D

 Actually, it's Vista new default anti-virus software. When you get a virus, the computer tries to burn it out.

 That computer had alot of virii...

---

