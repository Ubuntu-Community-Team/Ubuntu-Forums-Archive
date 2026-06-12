---
title: "Pre-mount harddrive--can't burn a livecd"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by charlierooster on 2008-02-25
All This is before running gparted.

Completely new and clean HD. Gateway computer. On powerup, PC doesn't recognize HD. Changed bios to boot from CD--that works fine. 

Downloaded gparted-livecd-0.3.4-11 onto another XP pc. Burned CD, but noticed message at start of burn that said some files might not transfer. 

Put CD on PC with new HD. Doesn't run gparted-livecd-0.3.4-11. CD just spins. 

Found web help that said to burn gparted livecd with InfraRecorder. So I ran IR, but it won't burn to blank CDs, just doesn't recognize the CDR.

Any hints for an absolute beginner? I think first step is just to get gparted-livecd-0.3.4-11 to run? Looked at recent GaFFy post, but that doesn't seem to apply here.
Thanks.

---

### Post by chewearn on 2008-02-26
Ok, you might already know this; apologies if that is the case.

When you burn the gparted-livecd, you should use "write cd image" command (or similar, depends on the burning software you are using).  You should not use "create data cd", then copy the gparted-livecd.iso into it.

Secondly, from your post, I gather the new PC is has a completely blank HD, no Windows, and no other OS in it.  If such is the case, you don't need to run gparted-livecd.  Immediately run ubuntu-livecd and install.

---

### Post by charlierooster on 2008-02-27
Thanks, AstalaVista--I did attempts to write image CDs. Same problem--error says to put in a blank CD, which I do of several makers and styles. Same error. So even if I don't need to run gparted, the image CDR I burn with unbuntu gets the same message when burning with the Windows based cd writer--some files might not be transfered. When doing install--cd just spins, and completely no recognition of a HD in the system. I think I'm back to the original question--is there something in burning a linux based CD that I might be missing? Thx.

---

### Post by chewearn on 2008-02-27
You can try any other cd burning software you can find; I'm not sure about the InfraRecorder you mentioned; never use it before.

The last time I actually burn a disc in windows, which was quite some time ago now, it was using the bundled software that came with the dvdr drive I bought.

---

