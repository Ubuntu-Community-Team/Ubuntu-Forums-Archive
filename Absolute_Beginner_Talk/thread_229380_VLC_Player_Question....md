---
title: "VLC Player Question..."
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by margni on 2006-08-04
I'm running Stream Tuner (thanks to automatix).  I have edited the player types from the preferences dialog in streamtuner to:

Play an mU3 file = wxvlc %q   Starts VLC when I open this type of file.
Play a stream = wxvlc %q  Starts VLC when I open a stream to listen to...

Problem is:  When I change streams a new instance of the player starts INSTEAD of just changing streams in the current instance of the player.

I tried editing the lines to use realplayer instead with little luck...

Anyone out there seen this behavior?  Any ideas of a fix for this, OR a different player to configure?

Thanks!

Margni

---

### Post by it.henrik on 2006-08-04
try %s instead of %q ... 

:)

---

### Post by margni on 2006-08-04
> **it.henrik said:**
> try %s instead of %q ... 

:)

Thanks!  Trying right now...

---

### Post by margni on 2006-08-04
Nope... the %s gets the player up, but it is not playing and it won't play by clicking the play button...  Going back to %q...

???

---

