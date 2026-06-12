---
title: "Multimedia keys recognised by &quot;Keyboard Preferences&quot;, don't work in Rythmbox"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Graphite on 2007-08-27
Hi all,

I have a slightly odd problem with multimedia keys in Ubuntu Dapper. My keyboard (a Memorex 5500RF) has a row of custom keys along the top. I've managed to assign functions to all of them using System>Preferences>"Keyboard Shortcuts", which detects them with no problems. 

All of the keys I've assigned funtions to (launching programs, master volume control) work perfectly, except: Play/Pause, Stop, Previous Track and Next Track. WhenI tried to asign them in Keyboard Shortcuts they were recognised correctly as:
XF86AudioPlay
XF86AudioStop
XF86AuidioPrev
XF86AudioNext

...however, RhythmBox and various other players don't respond to the keys.

I've searched the forums, but couldn't find a case where media keys are recognised by Keyboard Shortcuts but RhythmBox fails to respond. Does anyone have any suggestions?

Thanks,
Graphite

---

### Post by felicity on 2007-08-27
You might try assigning these functions to those keys:

rhythmbox-client --previous   # Skip backwards in playlist
rhythmbox-client --next       # Skip forward in playlist
rhythmbox-client --play-pause # Pause if playing, play otherwise
rhythmbox-client --pause      # Pause

---

