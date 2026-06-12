---
title: "iBook G4 Delete Key Doesn't Backspace"
date: 2012-04-05
forum: Apple Hardware Users
---

### Post by PkgMafaw on 2012-04-05
I installed Ubuntu 12.04 on my iBook G4 and I have noticed that the delete key no longer backspaces. It use to work with 10.04 LTS but now has stopped. I have 2 G4's and both do the same thing. I have searched the forum and FAQ's but have come up empty for a solution to restore it's functionality. Does anyone have a fix for this. Your help would be greatly appreciated.:(

---

### Post by MisterGaribaldi on 2012-04-06
I don't think this is a NumLock numeric keypad overlay issue. The only thing I can think of is maybe it's a keyboard/layout/region issue. Check to see what keyboard is set up for your computer. You could also hook up an external keyboard to see if you get the same behavior.

---

### Post by ikkeT on 2012-04-07
I upgraded our G4 powerbook two days ago, and hit the same issue. It was working fine before that, I don't recall when I updated the last time. It has been updated within few weeks anyway, and it's always been 12.04, so it's definately regression.

The keyboard in 12.04 is **cked anyway, hardly any special keys work anyway in Finnish layout. But the backspace/delete/arrow keys really should work as they did still few days ago. And it's only gnome-terminal that has the problem.

Please join this bug I created for it:

[https://bugzilla.gnome.org/show_bug.cgi?id=673697](https://bugzilla.gnome.org/show_bug.cgi?id=673697)

---

### Post by PkgMafaw on 2012-04-09
I agree that the issue is with Ubuntu Terminal. I tried an external keyboard with Terminal and SciTE Text Editor. Same result. SciTE had no trouble but Terminal did. I also tried both programs with the G4 keyboard and got the same result. Arrow keys do the same for me as well. I joined the bug report and I saw that it has a "resolved" at the end of the thread but I'm a little stumped on what to do with the "resolved": 
[https://bugzilla.gnome.org/show_bug.cgi?id=673409](https://bugzilla.gnome.org/show_bug.cgi?id=673409)

Thanks

---

### Post by ikkeT on 2012-04-10
It is resolved as being a duplicate of this bug:

[https://bugzilla.gnome.org/show_bug.cgi?id=673409](https://bugzilla.gnome.org/show_bug.cgi?id=673409)

Please join that one to confirm the bug.

---

### Post by PkgMafaw on 2012-04-11
> **ikkeT said:**
> It is resolved as being a duplicate of this bug:

[https://bugzilla.gnome.org/show_bug.cgi?id=673409](https://bugzilla.gnome.org/show_bug.cgi?id=673409)

Please join that one to confirm the bug.


Done.

---

### Post by rsavage on 2012-04-12
Thanks to all those who contributed to the various bug reports.

The fix is now in Ubuntu.  Upgrade to the latest libglib2.0 packages (2.32.0-1ubuntu3).

---

