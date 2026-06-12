---
title: "Not booting to GUI"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Mr lerame on 2007-09-01
Last time I used computer, everthing was ok. Now it appears there's a problem. I'm not sure what it all means and I don't even know what question to ask! I'm not computer literate and need some guidance on what to do. As far as I'm aware nothing has changed to cause this...I've not adjusted anything, no updates have been downloaded. Nothing. Can anyone help?

---

### Post by taurus on 2007-09-01
Looks like there are some corruptions on your root's partition, /dev/hda2.  Did you remember to shutdown it down first before you turn off the machine?  Also, do you happen to have Windows on /dev/hda1 and perhaps tried to access Ubuntu, /dev/hda2, from it?

You need to fsck your /dev/hda2.

```
fsck /dev/hda2
```

---

### Post by Mr lerame on 2007-09-01
> **taurus said:**
> Looks like there are some corruptions on your root's partition, /dev/hda2.  Did you remember to shutdown it down first before you turn off the machine?  Also, do you happen to have Windows on /dev/hda1 and perhaps tried to access Ubuntu, /dev/hda2, from it?

You need to fsck your /dev/hda2.

```
fsck /dev/hda2
```

Yes, did shut down correctly before turning off. Yes, I have got Windows on hda1 but not logged onto it for several weeks. 
I fsck'ed my thing and it spat out some text to which I replied 'yes' and it's all burst back into life.
Thanks buddy, your assistance is apprecitated!

---

