---
title: "messed up login..."
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by crispy_420 on 2006-10-01
Ok i first have to say this is a repost. I originally posted in desktop help but I never got a reply so I thought I would try here.

Here is my problem:

I can login just fine and use Ubuntu with my desktop of choice (eg Gnome, KDE, etc.). No problems here at all. My issue is when I logout either to change my desktop or to secure my computer. On logout I just get a black screen with no option to login. I can't even get to command line. It is like my login is gone.

Did I mess something up? Can it be fixed?

If you need more info on how to help me, post back. I've been a happy ubuntu user since 5.4 and I want to fix this annoyance.

---

### Post by scrattox on 2006-10-01
Can you not even get a command prompt by hitting Ctrl-Alt-F1 ?

Or Ctrl-Alt-Backspace?

---

### Post by crispy_420 on 2006-10-01
No command line at all. My keyboard seems to be dead when this happens. All I can do is shutdown the system by holding down the power button.

I thought that was the issue and I could just restart X, but no.

---

### Post by scrattox on 2006-10-02
OK.  So it sounds like something really is crashing.  Is this a standalone PC or is it on a network.
If it is on a network you might be able to "ssh" (i.e. open a remote shell) into the machine and see what is going wrong, but it's not for the fainthearted.

Out of interest, what graphics hardware do you have?  It might be a video driver crash.

---

### Post by scrattox on 2006-10-02
Just did a bit of Googling (or "searching on Google" as Google's Image-istas would have it :p ) and found [this]("http://forums.gentoo.org/viewtopic-t-485123-highlight-.html?sid=5c2d078fc95ac00c65ea99118c63bffc").

If you're using ATI hardware it might well be the answer, but even if not, it is probably worth a try:

---

### Post by crispy_420 on 2006-10-02
I do have ATI. I'll try it in a minute. Right now I'll installing 6.10 Beta on the same system but a different swappable drive. I'll post back in a few minutes with my results.

---

### Post by crispy_420 on 2006-10-03
Hey that worked....

Thanks. If you are ever in Tucson, I'll buy you a beer.

Off topic question you may know: What is that boot screen that lists drivers loading called? The one that has Ubuntu/Kubuntu with text scrolling under it.

---

### Post by mzembe on 2006-10-03
Thats the 'splash' screen right? (I think)

---

### Post by crispy_420 on 2006-10-03
You may be right. Just needed the name so I know what I want to tweak. Thanks!

---

