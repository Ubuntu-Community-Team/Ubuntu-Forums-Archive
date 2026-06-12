---
title: "My windows are opening behind the active window??"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2007-01-21
Hello, I have a strange new error happening. Whenever I open an app, like my thunar file system, or my trash can, the app keeps opening behind the app that I'm currently on, instead of on top of it.

Like for instance, I'll be in a folder, and open a file with mousepad, and instead of mousepad opening on top of the folder (thunar), it will open behind my folder??

Also, if I minimize the app to my task bar, and then re-open it, it will hide my task bar behind Firefox's page.

This just started happening the other day and I don't know why or how to fix this.

---

### Post by kvonb on 2007-01-21
Sounds like a Beryl problem, try it with it disabled.

I get the pop-up descriptions (ie mouse overs) and panel menus being drawn underneath each other now and then :rolleyes:.

Regards, KEv :)

---

### Post by crimesaucer on 2007-01-21
Yeah, it worked perfectly with xfwm4. Must be the latest Beryl 1.5-svn upgrade.

Damn...I forgot how quick xfwm4 is compared to Beryl.

---

### Post by wylie98 on 2007-01-22
I have exactly the same problem. It was fine until the last beryl upgrade, now all the new windows/ dialogue boxes open behind the active window.  Any one have any suggestions?

---

### Post by yoburtu on 2007-01-22
Hello,

This is not a bug, Look for FSP (focus stealing prevention) in beryl-settings -> general. Set it to none.

For more information:

[http://bugs.beryl-project.org/ticket/19]("http://bugs.beryl-project.org/ticket/19")

Best regards.

---

### Post by wylie98 on 2007-01-22
That did the trick. I had a feeling it would be something like that but wasn't sure what it was. Everything in the world is beatiful again.

---

### Post by crimesaucer on 2007-01-22
Thank you, that worked perfectly.

---

### Post by Helyyx on 2007-02-03
OMFG!  Yep, that fixed it, but damn I can't believe they did that.  If it wasn't working properly then why was it set to 'Extreme' by default at install.  At least it was default set when I installed it.  I looked up and down through the Beryl manager for that setting for DAYS until I finally found this thread with the answer.

---

### Post by danblack on 2007-03-25
FPS setting worked!  Thanks!

---

