---
title: "I need some help with sound."
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by grte on 2006-01-21
I have an Audigy 2 Value soundcard.  It was working fine, until I opened up alsamixer and messed with the volume levels to get sound working in a program.

But now I have no sound at all.  Is there some way to restore the volume levels to defaults?

---

### Post by patrick295767 on 2006-01-21
[QUOTE=grte]I have an Audigy 2 Value soundcard.  It was working fine, until I opened up alsamixer and messed with the volume levels to get sound working in a program.

But now I have no sound at all.  Is there some way to restore the volume levels to defaults?[/QUOTE]
try : ```

xterm
sudo alsamixer
```
  
Press m for mute /on /off
 Also, tab to get ALL stuffs
  
And try to start music, and try all possiibiliities with ur alsamixer 
put volume at max for everthg first, press m to unmute everthg
in ur alsamixer
  
let us know if u managed !

---

### Post by grte on 2006-02-18
Yup, I got it working, thanks for the tip.

---

