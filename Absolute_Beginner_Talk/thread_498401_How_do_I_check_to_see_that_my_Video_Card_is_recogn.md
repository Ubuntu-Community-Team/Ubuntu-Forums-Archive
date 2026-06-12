---
title: "How do I check to see that my Video Card is recognised correctly?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by joelkm on 2007-07-11
Hey, there I have a 512MB Nvidia Quadro 2500M installed. All seems to be working well but in Virtual Box I am only able to share 128MB of video memory between Host and Guest.  Is this any indication that my Video Card is not configured properly to use it's 512MB?

---

### Post by dreadlord_chris on 2007-07-11
> **joelkm said:**
> Hey, there I have a 512MB Nvidia Quadro 2500M installed. All seems to be working well but in Virtual Box I am only able to share 128MB of video memory between Host and Guest.  Is this any indication that my Video Card is not configured properly to use it's 512MB?

Short answer - no.
Longer answer - the guest OS in Virtualbox is not using your GPU directly - it's using an *emulated* card. So this is just an indicates the limitations of the *virtual graphics card*

---

