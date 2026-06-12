---
title: "Warty Trackpad Tap"
date: 2005-02-24
forum: Apple PPC Users
---

### Post by Down8ve on 2005-02-24
Any ideas how to get trackpad tap working?  I'm on a Lombard using Warty.  The volume up/down, brightness up/down, and mute buttons all work by default.  Is warty using PowerPrefs to accomplish these things?

---

### Post by bwilson on 2005-02-26
This works on my iBook.  YMMV.

Press Alt-F2, then try trackpad tap. If it doesn't work, after one attempt, try again. I read (somewhere on the net) that Alt-F2 cycles through the trackpad modes.

I don't know how to make the setting stick though, so I have to do this every time I log in.  :-(

---

### Post by Down8ve on 2005-02-26
Thanks so much for the hint!  Works like a charm.

---

### Post by BeTa on 2005-03-01
And what's about enabling this feature as default ? how would we do ?

---

### Post by gruepig on 2005-03-02
I haven't tested, but it looks like you want to set TPMode in /etc/pbbuttons/pbbutonsd.conf.  Options are likely the same as those for the 'trackpad' command: notap, tap, drag, lock.

---

### Post by bwilson on 2005-03-04
Thanks gruepig!
As you suggested, I set TPMode = drag in /etc/pbbuttons/pbbutonsd.conf.  The setting is remembered each time I log in. Perfect.

---

### Post by Viro on 2005-03-05
There is an option in PowerPrefs to do this. It's in the gears tab, under the input devices tab.

---

