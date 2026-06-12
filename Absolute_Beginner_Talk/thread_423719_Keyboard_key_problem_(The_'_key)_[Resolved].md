---
title: "Keyboard key problem (The ' key) [Resolved]"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Sef on 2007-04-26
I clean installed to Feisty and I have one problem with my keyboard.  The key which gives me the ' or the " is not working right.   When I press it without pressing the space bar, I get this:  &#347;.  It puts the apostrophe above the s instead of before it.  When I press it and the space bar, I get this: 's.  It's fine.  How can I reset that key, so it runs right.  Otherwise I can find no keyboard problems.

---

### Post by Bachstelze on 2007-04-26
Check your keyboard setting in your xorg.conf (the "XkbLayout" anx "XkbVariant" options, particularly).

---

### Post by Sef on 2007-04-26
I figured out what was going on.  I have different languages set on this computer.  If I keep it on us, it does that.  If I keep it on kr (korean), it does not.  Thanks Hymn To Life for the suggestion.

---

