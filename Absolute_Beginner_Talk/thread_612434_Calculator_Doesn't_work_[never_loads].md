---
title: "Calculator Doesn't work [never loads]"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by iiviip3 on 2007-11-13
Everything in gutsy is working just fine except for the calculator. When I go to load it [Applications -> Accessories -> Calculator] it loads for a split-second as "Starting Calculator" but it disappears. I've tried re-installing it, removing ubuntu-desktop and gcalctool, then re-installing and it still does not work. Any suggestions would be greatly appreciated.

---

### Post by jordanmthomas on 2007-11-13
Does it give you any useful output if you run gcalctool from a terminal?

Also, try this:
```
 rm -r ~/.gconf/apps/gcalctool
```
in case it's something wrong with its configuration / history.

---

### Post by iiviip3 on 2007-11-13
Hey thank you for the suggestion. I get nothing from the terminal. It loads the window "Starting Calculator" for a split second again and disappears. The terminal hangs requiring a CTRL+C. I tried the remove code and then re-installed in the package manager and still the same issue. Any thoughts?

---

### Post by jordanmthomas on 2007-11-13
It's very strange...according to its manpage, you've deleted all it looks for as far as configuration goes, so that's not the issue.  Maybe you should file a bug report after making sure your system's up to date.  It's certainly nice of it not to give any sort of output, huh?

<begin non-solution>
If you need a calculator, look up qalculate.  It's probably my favorite calculator ever
</end non-solution>

Sorry I can't be of any more help, but with no errors anything I suggested would just be a shot in the dark.

**edit**
If you're running compiz, try turning it off and see if it will launch.  Could be compiz is doing something odd?  <-- shot in the dark

---

### Post by iiviip3 on 2007-11-14
haha thanks for the "non-solution" I'll take a look at it. I appreciate the effort! I've decided to get rid of it but another odd problem now exists. It did not remove itself from the Applications -> Accessories menu. I've only been using Ubuntu for 3 days now so I have no idea how to get it out of there. It's completely out of my system I've checked add/remove and the package manager. Yet the icon is still there in the menu!

In any event if you [or anyone else] can help there that'd be great. Otherwise I appreciate your time and effort! Have a good one...I will file a bug report.

---

### Post by jordanmthomas on 2007-11-14
Can you remove it if you right click on the Ubuntu logo at the top and go to the menu editor?

Also, a logout / login *should* remove it.

---

