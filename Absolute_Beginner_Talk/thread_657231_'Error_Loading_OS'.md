---
title: "'Error Loading OS'"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by yamfox on 2008-01-03
I installed Ubnuntu on a external hard drive, with Windows XP on my internal. Everything seemed to go fine (no installation errors, etc.) until I restarted. It simply gives me a black screen telling me 'Error Loading OS'. What am I doing wrong??

---

### Post by yamfox on 2008-01-03
Bumpidy Bump Bump

---

### Post by yamfox on 2008-01-03
PLEASE!! I NEED HELP!!! 
Help, I need somebody,
Help, not just anybody,
Help, you know I need someone, help.

When I was younger, so much younger than today,
I never needed anybody's help in any way.
But now these days are gone, I'm not so self assured,
Now I find I've changed my mind and opened up the doors.

Help me if you can, I'm feeling down
And I do appreciate you being round.
Help me, get my feet back on the ground,
Won't you please, please help me.

And now my life has changed in oh so many ways,
My independence seems to vanish in the haze.
But every now and then I feel so insecure,
I know that I just need you like I've never done before.

Help me if you can, I'm feeling down
And I do appreciate you being round.
Help me, get my feet back on the ground,
Won't you please, please help me.

When I was younger, so much younger than today,
I never needed anybody's help in any way.
But now these daya are gone, I'm not so self assured,
Now I find I've changed my mind and opened up the doors.

Help me if you can, I'm feeling down
And I do appreciate you being round.
Help me, get my feet back on the ground,
Won't you please, please help me, help me, help me, oh.

---

### Post by kellemes on 2008-01-03
This is not the way to ask for help..
Please be patient.

---

### Post by ~LoKe on 2008-01-03
Is your external hard drive USB?  Do you have your BIOS set to boot from the USB device?

---

### Post by yamfox on 2008-01-03
A-HAH!! After messing with the BIOS enough, I got it right. See, the installer put GRUB on my internal hd somehow, and all I had to do was put my internal higher up on the boot list. It now gives me an option to boot from Ubuntu or WinXP. PROBLEM SOLVED!!!

---

### Post by ~LoKe on 2008-01-03
> **yamfox said:**
> A-HAH!! After messing with the BIOS enough, I got it right. See, the installer put GRUB on my internal hd somehow, and all I had to do was put my internal higher up on the boot list. It now gives me an option to boot from Ubuntu or WinXP. PROBLEM SOLVED!!!

Ah, I see.  It was looking for grub on the external hard drive, but it was really on the internal.  Odd.  Glad it all worked out!

---

### Post by Sbarton on 2008-01-03
Glad you got it fixed, a litle look around works wonders.
Hey! I Liked your poem and humour! A little patience is important!
regards

---

