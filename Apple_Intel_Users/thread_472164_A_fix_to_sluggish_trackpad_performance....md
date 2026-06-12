---
title: "A fix to sluggish trackpad performance..."
date: 2007-06-12
forum: Apple Intel Users
---

### Post by thully on 2007-06-12
Hi,

Today I decided to investigate the problem where MacBook (and presumably MacBook Pro) users have been having sluggish, unresponsive trackpad performance.  It seems that it all stems from one line in the xorg.conf.  Simply change:

Option "SendCoreEvents" "true"

to 

Option "CorePointer"

and things should work better. 

I also found a good set of Xorg.conf settings that I put on the MacBook wiki.  Using those, tapping and edge scrolling work great - including two-finger tapping for right-click!  However, these settings do not use two-finger scrolling, which has never worked well for me in Ubuntu as it does in OS X (except in VMware, but there I'm using the OS X drivers).

Give it all a try - I figure you'll see some improvement...

---

### Post by thully on 2007-06-12
For now, it looks like this fix is Gutsy-only - on Feisty it breaks the trackpad totally :(

---

