---
title: "[SOLVED] Google Earth jumps to startup screen"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by nuddernuby on 2007-08-08
On Feisty 7.04 : Installed Google Earth (from Medibuntu) with no error messages.

When running the application, the splash screen comes up and then jumps to a start-up screen (first line  :  **Starting kernel log**     last line  :  **Running local boot scripts**....),
then jumps to the log-on screen.

When logged on the cycle just repeats itself.

Have uninstalled and re-installed - no luck
Have tried to run from terminal in order to pick up messages - no luck

I saw in other threads that Graphic drivers (3D) might be an issue.  Can anyone please advise?

(This is a simple setup - graphics: SiS M650 chipset)
Thank you in anticipation.

---

### Post by 3rdalbum on 2007-08-08
Please post the results of the command:

```
glxinfo
```

into this thread; it does sound a lot like graphics drivers are the issue. Another thing: Are you using Beryl or Compiz at the time?

---

### Post by nuddernuby on 2007-08-08
Thank you for your response.
Compiz is installed.
The code
```
glxinfo
```
results in exactly the same action as when starting Google Earth.

Sadly, I don't yet know how to copy the text from the (black and white) screen to this thread.
Any suggestions?

---

### Post by Fextivo on 2007-08-24
i have the same problem too, anyone help us?

---

