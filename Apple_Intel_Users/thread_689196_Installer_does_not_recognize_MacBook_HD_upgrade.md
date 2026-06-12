---
title: "Installer does not recognize MacBook HD upgrade"
date: 2008-02-06
forum: Apple Intel Users
---

### Post by hajk on 2008-02-06
Wooh, upgraded my original CD MacBook to a 160GB Samsung SpinPoint SATA HD, reinstalled Mac OS~X and then, when trying to reinstall Gutsy, ran into Bug #158166. So, it's over and out for now as far as my use of Ubuntu or Debian on this MacBook is concerned. May be I'll be back when Hardy gets released... 

That this should happen after almost two years of happy GNU/Linux use on this MacBook is a shame. There should be a Sticky about it, as this problem apparently has been known for some time and while many original MacBook owners are thinking of upgrading to this popular HD product.:mad:

---

### Post by cyberdork33 on 2008-02-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/158166](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/158166) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 It is a documented Bug, and it has been discussed here several times. In fact, there is a solution in the filed bug.

It would likely be most helpful if you could download the latest Hardy LiveCD and see if it will recognize your disk, and if not be sure to add to the bug, but I think this should be fixed already in Hardy. Now is the time to get involved in bug squashing to get fixes in a new release.

---

### Post by hajk on 2008-02-06
Yeah, yeah... just needed to blow off some steam after wasting half a day on this. I'm downloading the Hardy alternate daily build right now, we'll see how that goes.

---

### Post by cyberdork33 on 2008-02-06
> **hajk said:**
> Yeah, yeah... just needed to blow off some steam after wasting half a day on this. I'm downloading the Hardy alternate daily build right now, we'll see how that goes.
probably should just stick to the set releases (Alpha 4 was just released) daily builds could have all kinds of unknown issues. On top of that, unless you are sure you want to install, the alt cd is not well suited for "testing out" Ubuntu on some hardware.

---

### Post by hajk on 2008-02-06
Now he tells me... the Hardy installer crashed with a dbootstrap error. :(

The good news is that the HD is recognized and can be partitioned thru the Hardy installer.:)

So, I'm calling it a day for now and I'm going to enjoy some iTunes content (that's why I needed that larger HD).:popcorn:

---

### Post by hajk on 2008-02-07
Right, Hardy Alpha4 installed fine!:guitar:

---

### Post by cyberdork33 on 2008-02-07
> **hajk said:**
> Right, Hardy Alpha4 installed fine!:guitar:That's good news. Can you post to that bug and say that you have verified that it works in Hardy, and didn't Gutsy. Oh, and mark as solved if you would.

---

### Post by hajk on 2008-02-07
Consider it done!

---

### Post by cyberdork33 on 2008-02-07
> **hajk said:**
> Consider it done!
and things happen:
[quote=BugReport]Thank you so much for testing and providing feedback.  I'm going to go
ahead and mark this report as "Fix Released" against the Hardy kernel.
It's unlikely that a fix will be backported to the 2.6.22 kernel so I'm
going to close that task as well.  Thanks.[/quote]Don't you feel like you contributed something now? Hopefuly, they don't break it now in future changes!

---

