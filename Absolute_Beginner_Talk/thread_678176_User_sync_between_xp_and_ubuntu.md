---
title: "User sync between xp and ubuntu"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Doormat on 2008-01-25
Is there a way to sync (and keep them synced) my documents and desktop files/folders between xp and ubuntu? I don't think its possible for windows to do this but perhaps there is a way with ubuntu.

The idea is that I want to dual boot but it would be much more convenient since I put everything on my desktop to have them synced instead of having to figure out which one its on etc.

Maybe there is a way to set my ubuntu desktop to the same location as the xp desktop?

I'm new to ubuntu and trying to get a setup that works best for me. Thanks in advance for your help!

---

### Post by PeterJS on 2008-01-25
If you have your windows parition mounting with read/write permissions you can symlink portions of you windows profile (my docs and stuff) in to your linux profile.

1) Migrate every thing out of ~/Documents to your windows documents forlder
2) Delete ~/Documents
3) Symlink in the replacement folder:
```

ln -s /media/windows/Documents\ and\ Settings/User/My\ Documents ~/Documents

```

---

