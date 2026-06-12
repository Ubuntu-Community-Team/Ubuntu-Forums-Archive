---
title: "[SOLVED] Magic Lamp for Compiz"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by FAMUgolfer on 2008-04-04
Thank you all for your your time and support with us noobs.

I have CCSM configured properly first off with cube, burn, splash, etc, working perfectly except for when i minimize any of the windows.  

I would like to set it to magic lamp.  
What I did in CCSM: -->Animations --->Minimize Animations---> double-click on the first option (Zoom) --->click on Minimize Effect and choose Magic Lamp --->Clicked OK

I'm not sure what I did wrong because its not even working.  I don't think the default Zoom option was working either because when I minimize a window, that window just disappears  into the panel with no apparent effect.  I also made sure the Fading Window option was unchecked.

Your help (again) will be greatly appreciated.:confused:

---

### Post by wormser on 2008-04-04
I had some issues when doing this.  It got it working with the following.  I had to delete all the other effects and just left the Magic Lamp.  The Window Match settings: 
> (type=Normal | Dialog | ModalDialog | Utility | Unknown)

---

### Post by FAMUgolfer on 2008-04-04
Thank your for your quick reply but I just figured out what was wrong.
I cleaned up my panel by removing Window List and replaced it with Window Selector.  By doing this, none of the minimizing effects will work.

By placing Window List back on the panel will the effects work properly (right click panel---->Add to Panel--->choose Window List---> click OK) 

I like the Window Selector option in my panel because it takes up less space.  It would be nice though if the minimizing effects were compatible with this option:)

---

