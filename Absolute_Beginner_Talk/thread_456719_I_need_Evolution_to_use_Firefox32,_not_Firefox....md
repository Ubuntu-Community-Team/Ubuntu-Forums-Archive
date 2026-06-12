---
title: "I need Evolution to use Firefox32, not Firefox..."
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-05-28
Hi,
I'm on Ubuntu Amd64 and so I had to do a fix to get Adobe Flash Player to run on 64amd Ubuntu. 

I got the fix done, but one part of the process is that you have to upgrade or switch from Firefox to Firefox32 in order for this to work. But my Evolution email program, if I'm accessing a link sent by email, seems to automatically use Firefox and not Firefox32.  Therefore, if the link to which I'm going has flash on it, I can't read it, because Firefox was used by Evolution and not Firefox32.

Is there any way to change this so that Evolution uses Firefox32 for links and browsing? I've searched through the 'Preferences' area of Evolution and could not find anything.

I appreciate any help on this. Many Thanks, Frank Bright

---

### Post by freebird54 on 2007-05-28
I think that is a 'system-wide' preference, not a Firefox one.  Look under System->Preferences->Preferred Applications   - mine reads:

```
/opt/swiftfox/firefox "%s"
```

Change yours to pull up the copy you want to run....

---

### Post by Brightbelt on 2007-05-28
Thanks FreeBird54, I think that solved the problem! I appreciate your help...Frank Bright

---

