---
title: "amsn crashing"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by gverrilla on 2008-04-04
hey,I have just runned amsn for the first time
and it crashed (2 offline messages are blinking)
how to fix it?
what should I do when something crashes on ubuntu?
cheers

---

### Post by northern lights on 2008-04-04
When something crashes and leaves some graphical remains, for instance, it's got to be force quit.

If you prefer the mouse, it's helpful to add the "Force Quit" app to your panel. Right click on any panel and choose "+ Add to panel", select "Force Quit".

In the commandline "killall ..." does the job. If I was to run ```
killall firefox
``` for instance, I'd have write this again...

---

### Post by herbster on 2008-04-04
Open a terminal (Applications > Accesories > Terminal) and run the program from there:

```
amsn
```

Then paste the output here in a post, using the [code] tags.

---

### Post by Mazza558 on 2008-04-04
Have you tried emesene? It's (IMO) a much better MSN replacement, and fits in better.

---

### Post by gverrilla on 2008-04-04
klupus@Luther:~$ killall amsn
amsn: no process killed

:/



> **herbster said:**
> Then paste the output here in a post, using the [code] tags.
what do you mean with output?

---

### Post by herbster on 2008-04-04
amsn's process is probably called "wish" from what I recall. Try

```
ps aux | grep wish 
```

By output I mean the text displayed in the terminal when amsn is running until it crashes. Terminal output is what is used to diagnose problems when programs aren't behaving correctly.

---

### Post by northern lights on 2008-04-04
mkey, you got us wrong.

I meant to tell you how to exit an application if it has frozen.

The next post asks you to post the output of ```
amsn
```i.e. simply start the application from the terminal/commandline.

---

