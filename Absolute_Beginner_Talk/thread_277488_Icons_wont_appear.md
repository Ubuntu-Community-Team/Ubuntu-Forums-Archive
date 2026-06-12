---
title: "Icons wont appear"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-10-14
Ya so when I first installed Kubuntu everything was fine I had no problems and then out of the blue, suddenly my window icons wont appear, like the back, forward, reload, etc. They do in my internet browser but not in Konqurer or Kopete, Look at the screenshots. See up where you would normally see back and stuff, well I got these stupid little arrow things, I want my buttons back. Please help.

---

### Post by taurus on 2006-10-14
I guess you forgot to attach your screenshots!!!  ;)

---

### Post by Narcoleptic_Insomniac on 2006-10-14
oops lol. there

---

### Post by Narcoleptic_Insomniac on 2006-10-14
Why does nobody help me out ever its really annoying, my problem is that the back, forth, reload, etc. icons in windows, NOT my internet browser, do not appear. Look in the screenshot. In the window were you would see the back button, nothing is there, how do I fix this.

---

### Post by Sef on 2006-10-14
Have you checked in view to see if they are turned off?

---

### Post by UnknownVariable on 2006-10-14
It's not that "nobody's helping you," it's just that you're expecting answers right away. That's not going to happen. Give it some time, and if your thread moves to the second or third page of threads, give it a bump up, but ONLY if it drops down a few pages. Just give it some time. ;)

Anyhow, if you ask me, it looks like you dragged the address bar up or to the left to hide the buttons. See the little dots that are shown in the circle I made? Those usually note the end of a toolbar that can be dragged. Try clicking and dragging around there and see if any of the buttons appear.

---

### Post by d3v1ant_0n3 on 2006-10-14
Try right clicking on a toolbar in Konqueror, and selecting 'Toolbars'. Make sure 'Location bar' is checked.

---

### Post by aysiu on 2006-10-14
**About the thread**: > **Narcoleptic_Insomniac said:**
> Why does nobody help me out ever its really annoying Because you waited only three hours... on a Saturday.

People have lives. They're perfectly willing to help you, but we're all volunteers here--fellow Ubuntu users. If someone spots your thread, she'll help out.

I'm on these forums probably more than anyone else, but even I didn't spot your thread. A simple > bump would be appropriate after a day or so. A separate thread complaining about the lack of help is totally unnecessary and pretty much a double-post, so I'm merging the two threads together.

**About your problem**:
I don't know why this has happened to you, but if you paste this command in the terminal, it'll reset your KDE preferences and probably bring your icons back, I'm guessing: ```
mv ~/.kde ~/.kde.old
``` You might have to restart Konqueror or log out in order for the changes to take effect. If you find that doesn't solve your problem, and you want to get your old preferences back, do this: ```
rm -r ~/.kde
mv ~/.kde.old ~/.kde
```

---

### Post by iovar on 2006-10-14
That's not a configuration thing, it's probably a bug or something.
I've had it once, too, after extensively playing with themes, colors, etc.
If you look the screenshot, the browser bar on the left should have icons too.

Unfortunately, I cannot help you , since it happened to me on a temporary
account and a simple rm -rf ~/.kde fixed it. But that's not what you want
to do on a normal installation (you'll lose all your configuration).

Perhaps you can migrate your settings incrementally by backing up like aysiu said.

---

