---
title: "bootup text is jagged with new lcd"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by mattismyname on 2008-02-18
I just got a new LCD and the text mode (kernel messages etc at bootup) is somewhat garbled.  I suspect it has to do with some resolution scaling filter in the monitor itself but I don't really know.  However, I do know the monitor is capable of displaying decent text-mode text because the bios messages look fine.  It's only the text from grub & linux that looks bad.

Any idea?

I've attached a photograph of the text in question.

---

### Post by dcstar on 2008-02-19
> **mattismyname said:**
> I just got a new LCD and the text mode (kernel messages etc at bootup) is somewhat garbled.  I suspect it has to do with some resolution scaling filter in the monitor itself but I don't really know.  However, I do know the monitor is capable of displaying decent text-mode text because the bios messages look fine.  It's only the text from grub & linux that looks bad.

Any idea?

I've attached a photograph of the text in question.

Pause Grub and use your monitor's "Auto adjust" function when it is displayed.

---

### Post by mattismyname on 2008-02-20
dcstar- thanks.  I know the feature you're talking about but unfortunately my monitor doesn't have that feature.  I guess it assumes it's smart enough to figure out the video mode by itself.

Any other suggestions out there?

---

