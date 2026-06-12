---
title: "A Simple Problem with Kubuntu Themes"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by sr243 on 2007-06-12
I configured my Kubuntu 7.04 to almost the way I like it, with one small fault still bothering me.

In Windows, moving the mouse to the very top right corner of the screen in a maximized window is where the close button is.  Yet, in my Kubuntu box, the close button is about 2 pixels away from that point, making it overly annoying to close a window.

Is there a way (maybe a new theme for KDE) that has the close button working when clicking at the top right corner of the screen?

---

### Post by kittyhawk63 on 2007-06-12
If I understand your problem, how about using your monitor adjustments? Narrow the screen width.
kh

---

### Post by sr243 on 2007-06-12
No, it's not about the monitor.

The thing is, when I move the mouse to the top corner of the screen (e.g. at 1024,1 on a 1024x768 screen), I want the close button on a maximized screen to be active when I click.  The issue is that the window border is too thick, and when I click there, it thinks I want to adjust the size of the window instead.

I'm not sure how to describe this without pictures, but I hope this makes it more clear.

---

### Post by kittyhawk63 on 2007-06-12
> **sr243 said:**
> No, it's not about the monitor.
I'm not sure how to describe this without pictures, but I hope this makes it more clear.

Do you know how to make a screen shot and put it in a thread as a managed attachment?

---

### Post by xthund3rh3adx on 2007-06-12
seems like a problem with your resolution

---

### Post by notwen on 2007-06-12
Might you be using Compiz or Beryl?

---

### Post by sr243 on 2007-06-12
It's definitely not a problem with my resolution.  Let me figure out how to post a screenshot that has the mouse first, though.

---

### Post by kittyhawk63 on 2007-06-12
Just a shot in the dark if the resolution suggestion does not work. Remove the "close" icon by right clicking and choosing "remove from panel." Then add a new one by right clicking the panel and choosing "add to panel." Look for the "close" icon and drag it up to the panel where you want it. Once located, right click the icon and choose "lock to panel."

Just another suggestion to see if we can help.
kh

---

### Post by sr243 on 2007-06-12
okay, here are some pictures

[IMG]http://img169.imageshack.us/img169/6065/screenag3.png[/IMG]

When I move my mouse to the top corner of the screen, I want to close the window, but the close window button is not at the very top.

-----------

In Windows, the close button doesnt look like it is at the very top corner either, but when I move to the top corner of the screen and click, it still closes a maximized window.

[IMG]http://img169.imageshack.us/img169/8249/screen2jn3.png[/IMG]

---

### Post by sr243 on 2007-06-12
a few clarifications:

the close buttons work, it's just that I want them to be located further up and right on a maximized window.

i'm not using beryl, but I do have it installed.  Activating it makes no difference.

it doesn't let me remove the close button by right clicking on it.

---

### Post by sr243 on 2007-06-12
ok, i even rebooted into my windows partition to get a screenshot from my own desktop.

[IMG]http://img117.imageshack.us/img117/1976/windowsqq5.jpg[/IMG]

Even though I couldnt capture the mouse, it is at the very top right corner of the screen.  And it'll close the window when I click on it.

The close button in Kubuntu is about 2-3 pixels away...

Hmm...

---

### Post by sr243 on 2007-06-12
...?

---

### Post by Princey on 2007-06-12
I use Kubuntu and I don't have the problem you describe. I think it's the theme you're using. See my screenshot I've attached. FYI, I use the Quartz style for my window decorations.

---

### Post by kittyhawk63 on 2007-06-12
Okay, try this. Using your "monitor" settings, widen your screen and raise it more to the top. That should push your "Close" icon to the corner. Let us know if that works. It worked for me.
kh

---

### Post by sr243 on 2007-06-12
I tried switching to Quartz, but it didn't help...


KH, could you elaborate on how to change the monitor settings?  I don't see such an option in the KDE control center (I'm using a laptop, with ATi)

---

### Post by kittyhawk63 on 2007-06-12
> **sr243 said:**
> I tried switching to Quartz, but it didn't help...


KH, could you elaborate on how to change the monitor settings?  I don't see such an option in the KDE control center (I'm using a laptop, with ATi)

The monitor settings on my monitor are "push" buttons. Look at your actual monitor. It is "not" a program in Linux. You should have some way to tweak your monitor just like you can make adjustments on some television sets. Sorry that I may have confused you.
kh

---

### Post by HotShotDJ on 2007-06-12
Oh for pete's sake... go to system settings --> appearance --> window decorations
Change the border width and/or title bar height .

Or, learn to point at the X.  :roll:

---

### Post by sr243 on 2007-06-12
I tried changing the borders, it didn't help.

And I booted into the Kubuntu live-cd, and guess what? It worked fine there!

Is there something that I installed that could have done this? Maybe beryl?

---

### Post by HotShotDJ on 2007-06-12
> **sr243 said:**
> ..Maybe beryl? Pretty likely.  You didn't mention that before.  Beryl is Beta software, and can really mess up KDE.  I strongly urge you to remove it.  It will save you all kinds of trouble... and possibly fix this issue.

---

### Post by Bohlio on 2007-06-12
I'm really not getting why this is a problem, cant you just click on the X? Its not that hard!

---

### Post by sr243 on 2007-06-12
sure i can click on the X, but it is really annoying, because i'm soo used to clicking at the very corner without looking at the mouse to close the application.

i'll uninstall beryl and see if it helps.

---

### Post by Bohlio on 2007-06-12
If you absolutely have to have the X in the exact corner, look for a theme that fits your needs. Im sure theres gotta be a theme out there that sticks it up in the corner. Just hunt around, try them out, and see what works. If its not there with your current theme, your probably not going to be able to change it. Edit, Also, If you can see your mouse go completely off the screen when you to to the top right, Its probably because of beryl or something. I know with compiz i can go off the screen.

Edit: dont uninstall beryl, Just disable it.

---

### Post by kittyhawk63 on 2007-06-12
> **HotShotDJ said:**
> Oh for pete's sake... go to system settings --> appearance --> window decorations
Change the border width and/or title bar height .
Or, learn to point at the X.  :roll:

HotShot,
It's comments like yours that turn off newbies to Linux. If you can't be constructive, don't enter the thread.
Sorry, but your kind of reply really irks me.
kh

---

### Post by HotShotDJ on 2007-06-12
> **kittyhawk63 said:**
> HotShot,
It's comments like yours that turn off newbies to Linux. If you can't be constructive, don't enter the thread.
Sorry, but your kind of reply really irks me.
khYou didn't find my step-by-step instructions (not to mention, my follow-up) useful?  Sorry about that.  You should demand your money back.

---

### Post by sr243 on 2007-06-12
hmm, turned off and uninstalled beryl, but problem still there...

---

### Post by HotShotDJ on 2007-06-12
> **sr243 said:**
> hmm, turned off and uninstalled beryl, but problem still there...I don't know what to tell you.  On my machine (I'm using the exact same widget style that you do) I put the pointer in the top right corner and I'm able to close the window.  Is this REALLY important enough to tear your system apart or ultimate reinstall just so you don't have to get used to something different?

---

### Post by mainalisuyog on 2007-06-12
> HotShot,
It's comments like yours that turn off newbies to Linux. If you can't be constructive, don't enter the thread.
Sorry, but your kind of reply really irks me.
kh

I don't understand why you are irked. His was the most helpful post in this thread. I was going to suggest the same thing myself.

---

### Post by sr243 on 2007-06-12
this is bugging me so much, i'm going to reinstall the whole o/s

---

