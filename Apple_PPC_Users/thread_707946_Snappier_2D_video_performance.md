---
title: "Snappier 2D video performance"
date: 2008-02-25
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-25
If you're like me, many of us don't have the world's fastest video card, not to mention using a simpler video driver.  Fancy effects are basically not even available.

Ever thought about turning off all animations, windows or otherwise?

I thought this would be handy for low-end PPC users with Gnome; I even use it on my G5 iMac since it doesn't have a lot of video horsepower.

Just hit ALT-2 (no ctrl key) and startup [B]gconf-editor
[/B]

In the gconf-editor, I made sure that

Apps > Metacity > General > Reduced Resources

was checked.

In addition, I also looked at

Desktop > Gnome > Interface > Enable Animations

was **UN**checked.

Nice little speedup for my basically 2D requirements.  Don't use sudo to start gconf-editor, otherwise you'll only change the settings for root.

Thanks to:
[http://ubuntuforums.org/showthread.php?t=216628&highlight=reduced+resources](http://ubuntuforums.org/showthread.php?t=216628&highlight=reduced+resources)

---

