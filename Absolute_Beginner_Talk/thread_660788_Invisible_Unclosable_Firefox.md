---
title: "Invisible Unclosable Firefox"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by ColinWS on 2008-01-07
All worked well until I started to get the message""Firefox is already running. To open a new window,you must firstclose the existing Firefox process, or restart your system" 

This occurs each time I try to open Firefox even after restarting a new session. thus I cannot use Firefox in UBUNTU at present.
 
Restarting does not help.

I cannot find how to open another window by the means suggested as probably there is no other window to open

 I cannot find how to reveal which applications are running nor how to close them - such as the cont-alt-delete in the usual OS. 
I expect to have to delete and reinstall Firefox but I would appreciate altermatives and some insight how it happened so that I can prevent recurrence.

Simple language please- thanks
Suggestions please. 
Thanks in anticipation

---

### Post by mister_pink on 2008-01-07
Try typing in terminal:
ps -A | grep firefox

Then type "kill" and any of the process numbers that came up before, in particular the one for "firefox-bin". Sounds like theres more to this though, but that ought to at least temporarily do something.

---

### Post by philinux on 2008-01-07
Fire up System>Admin>System monitor. Keep it running and click the processes tab. Look out for any firefox occurrences.

You can then highlight them right click and end process. 

There's normally two

Firefox and
Firefox-bin

You need to be rid of both to restart firefox.

Maybe you did something in sessions?

---

### Post by jeffus_il on 2008-01-07
Is it possible that Firefox is running in another workspace, look at the right bottom next to the trashcan, you can change your workspace.

When you  log out your session may optionally be saved, It may have been closed and saved with Firefox running so it opens it when you run a new session. Close or kill the Firefox program as below, the save your session using:
System>Preferences>Sessions>tab - SessionOptions

---

### Post by mirexastan on 2008-01-07
Hi, the same thing happens also in widohs, but there's the 'run firefox in safe mode thing.
It runs okay. Haven't encounter this in ggibbon as yet...

---

### Post by billgoldberg on 2008-01-07
just go to a terminal and type

```
pkill firefox
```

problem solved

---

### Post by snickers295 on 2008-01-07
> **ColinWS said:**
> All worked well until I started to get the message""Firefox is already running. To open a new window,you must firstclose the existing Firefox process, or restart your system" 

This occurs each time I try to open Firefox even after restarting a new session. thus I cannot use Firefox in UBUNTU at present.
 
Restarting does not help.

I cannot find how to open another window by the means suggested as probably there is no other window to open

 I cannot find how to reveal which applications are running nor how to close them - such as the cont-alt-delete in the usual OS. 
I expect to have to delete and reinstall Firefox but I would appreciate altermatives and some insight how it happened so that I can prevent recurrence.

Simple language please- thanks
Suggestions please. 
Thanks in anticipation
type pkill firefox in a terminal.

---

### Post by lvleph on 2008-01-07
Try this
```
rm -v ~/.mozilla/firefox/[Profile name]/*lock
```

Most likely Firefox just thinks it is still running, and so you have to delete the lock on it.

---

### Post by mouseboyx on 2008-01-07
```
killall firefox-bin && firefox
``` -- This might work.

---

### Post by caravel on 2008-01-07
I've had firefox crash in gutsy also.  I didn't have any problems in Dapper or Edgy and I haven't really used feisty enough to know.  I've also had to kill the firefox-bin process.  I also get a problem after shutting down and restarting Ubuntu where when starting firefox up again I get the "quit unexpectedly" problem every time.

---

### Post by melopsittacus on 2008-01-07
This problem happened to me when Firefox was not able to find it's settings directory (because I had moved it). Try ```
cat  ~/.mozilla/firefox/profiles.ini
``` and see wether the profile path is really where it is pointed to.

---

### Post by ColinWS on 2008-01-07
> **philinux said:**
> Fire up System>Admin>System monitor. Keep it running and click the processes tab. Look out for any firefox occurrences.

You can then highlight them right click and end process. 

There's normally two

Firefox and
Firefox-bin

You need to be rid of both to restart firefox.

Maybe you did something in sessions?

Dear Phiinux,

This one worked immediately

- thanks ColinWS

-and thanks to all who responded!!

---

### Post by billgoldberg on 2008-01-07
No thanks, but still pkill firefox is faster.

I use it alot since flash players crash firefox alot and it works when it's still running in the background.

---

