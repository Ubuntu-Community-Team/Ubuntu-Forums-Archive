---
title: "How to figure out what's crashing my system?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Depressed Man on 2007-09-04
I know system logs exist on the computer, but is there anyway to identify what is randomly crashing my system? I typically have alot of programs open (including Compiz Fusion but my system has froze up too sometimes without running it). And I'd like to identify what's causing my random system lock ups.

It's completely freezing my system at times on my desktop. I can move my mouse but keyboard is dead, my system will be dead (all I can do is move my mouse cursor...clicking does nothing).

---

### Post by Jimmyfj on 2007-09-04
Other than look for any error messages in your system log you could take a look at the power saving settings/screen saver settings. If those settings are ok you might wanna run a check on your system RAM.

---

### Post by K.Mandla on 2007-09-04
Sometimes you can switch to the first virtual console and see error messages there. But if your keyboard is dead, there's not much luck in that. 

I'm guessing you know about the logs in /var/log/ ... have you tried starting programs in terminal windows, and watching for error messages when things lock up?

From what I've seen, full desktop lockups like you describe are sometimes linked to video drivers. Can you switch drivers and possibly avoid the lockups?

You could also redirect error output from X into a file; if I remember right, you can do that by starting X from a terminal window and appending the 2> flag to the startx command. Something like this. ...

```
startx 2>errlog.txt
```
That might not be exactly right, but it's something along those lines. With any luck, last-minute error messages will be written into that file, and you'll have something to inspect on restart. ;)

---

### Post by Depressed Man on 2007-09-04
I'll keep that in mind. I doubt it's a RAM issue because my Windows XP installation is solid (they're both on the same HDD too). Can't be Power settings or screensaver either since I'm using the system while it freezes up.

I am using the open source drivers right now. I could try switching to the restricted ATI ones, but that would require getting Compiz Fusion working with it. >.<

---

### Post by t4thfavor on 2007-09-04
Same problem with the regular free drivers. Switched to the ATI ones and it seems to have stopped. I had a 9600XT (rv350). It worked great with beryl,  although the pc is no longer being used.  I would recommend the restricted ATI drivers, it will probably fix your issue.

---

### Post by K.Mandla on 2007-09-05
Agreed. Try the proprietary drivers and see if you get any better results. Post back here in either case; my curiosity is piqued. ;)

---

