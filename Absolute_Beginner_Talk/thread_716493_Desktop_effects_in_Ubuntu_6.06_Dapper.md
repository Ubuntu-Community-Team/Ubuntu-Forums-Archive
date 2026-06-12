---
title: "Desktop effects in Ubuntu 6.06 Dapper"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Crafty Kisses on 2008-03-06
Is that possible anymore? Because I've been trying lately, and it hasn't been working, any ideas?

---

### Post by Shazaam on 2008-03-06
I don't see why not since compiz is in the repo's. Did you install everything compiz related?

[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

---

### Post by Crafty Kisses on 2008-03-06
> **Shazaam said:**
> I don't see why not since compiz is in the repo's. Did you install everything compiz related?

[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

Yep, then I try to run compiz in terminal and then I get the following error:
```
compiz.real: No composite extension
```
I also added the line in my Xorg so this would supposedly fix this error, the lines I put in were:
```

Section "Extensions"
          Option  "Composite" "Enable"
EndSection
```

So any ideas? This is on a intel based laptop as well.

---

### Post by Shazaam on 2008-03-06
I looked at a few google links inputting your error and Ubuntu and a good percentage refer to blacklisting. It MIGHT not apply but have you seen this?

[http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112)

---

### Post by Crafty Kisses on 2008-03-06
> **Shazaam said:**
> I looked at a few google links inputting your error and Ubuntu and a good percentage refer to blacklisting. It MIGHT not apply but have you seen this?

[http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112)

Thanks for the help.

---

### Post by Crafty Kisses on 2008-03-06
Anyone else got any info on this, because I really like Ubuntu 6.06, I don't want to switch, so any help would be greatly appreciated. I have 7.10 on my desktop running desktop effects just fine, just trying to get my laptop to run them, so is there any packages I can download, looked everwhere! Thanks guys.

---

