---
title: "Will my sound still work in Gutsy?"
date: 2007-10-21
forum: Apple Intel Users
---

### Post by Dingbats on 2007-10-21
I'd love to upgrade to Gutsy, but I'm feeling unsure whether my sound will still work.  I'm on a Mac Pro on Feisty, with ALSA 1.0.14.   I got help from the very helpful nicfagn on here to make my sound work.  I did what he said in [this post](http://ubuntuforums.org/showpost.php?p=2978364&postcount=41) (patched ALSA and recompiled it configured for the HDA Intel chipset) and [this post](http://ubuntuforums.org/showpost.php?p=3195541&postcount=53) (changed a line in the patch and recompiled), which made it work. 

But what I'm afraid is, will an upgrade to Gutsy void what I've done, making my sound not work?  I'm feeling very unsure...

---

### Post by cyberdork33 on 2007-10-21
> **Dingbats said:**
> I'd love to upgrade to Gutsy, but I'm feeling unsure whether my sound will still work.  I'm on a Mac Pro on Feisty, with ALSA 1.0.14.   I got help from the very helpful nicfagn on here to make my sound work.  I did what he said in [this post]("http://ubuntuforums.org/showpost.php?p=2978364&postcount=41") (patched ALSA and recompiled it configured for the HDA Intel chipset) and [this post]("http://ubuntuforums.org/showpost.php?p=3195541&postcount=53") (changed a line in the patch and recompiled), which made it work. 

But what I'm afraid is, will an upgrade to Gutsy void what I've done, making my sound not work?  I'm feeling very unsure...

Just try the live cd, and if sound is broken, then you would need to do something more... Also, the same patch might work in Gutsy too!

---

### Post by MichaelSwengel on 2007-10-21
Well, if it's any indication, I just installed Gutsy on my Macbook Pro, and the sound works perfectly. Of course, they have different hardware...but I think you'll probably be ok.

---

### Post by Dingbats on 2007-10-22
> **cyberdork33 said:**
> Just try the live cd, and if sound is broken, then you would need to do something more... Also, the same patch might work in Gutsy too!
I will try that.  Haven't there been any changes to ALSA or something in Gutsy though, that may complicate things?

---

### Post by nicfagn on 2007-10-22
If after the upgrade the sound doesn't work, you can try to do what is suggested in this [post]("http://ubuntuforums.org/showpost.php?p=3552607&postcount=16").

---

