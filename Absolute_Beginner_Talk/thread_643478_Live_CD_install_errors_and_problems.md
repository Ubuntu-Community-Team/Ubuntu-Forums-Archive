---
title: "Live CD install errors and problems"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by averyh on 2007-12-17
Computer specs:
Intel Q6600 2.4 quad
nvidia 7600 gs 512 mb
2.5 gigs of ram
Intel board
Win vista

While trying to install Ubuntu for the first time (I've allocated room for the install already 30 gigs) I run into a few problems and errors.  After the Ubuntu loads up and ask me to pick an option I pick the first one for Run and Install Ubuntu.  When I do that it starts to load like normal.  At the end though it pops up with an error message saying "Could not allocate enough..." I couldn't catch the rest. Right after that it sends me to BusyBox with
 <Initramfs> sitting there like an old dos/command prompt.  

What can I do to complete the installation.  Is there something I have it doesn't support?  The q6600 processor?

If there are some commands I could use to finish the install from the Initramfs I'd gladly go that way, but all the commands I had (pretty good dos user first time linux) didn't seem to lead me anywhere.

Thanks guys.

---

### Post by Sef on 2007-12-17
1) Did you md5sum the download? (Makes sure the download is good.)

2) Did you burn at 4x or less? (Faster can corrupt the burn.)

3) Did you check the disk?  (Go down to check disk at the menu options.)

---

### Post by averyh on 2007-12-17
The copy is legit and not corrupt.

I checked the disk and it went right to the same Initramfs screen without the error message before hand.

I'll try a new one at 4x or so.

So I am guessing if it goes to that screen I'm screwed... can't install from there?  Is that pretty much the command promt of Linux?

---

### Post by alienexplorers on 2007-12-17
You could try loading with the alternate CD to see if that loads.  make sure you burn it a 4x and check the md5 checksum.

---

### Post by xeth_delta on 2007-12-17
I agree with Sef and alienexplorers. I have seen cases where a CD written at a high speed has created problems

---

### Post by averyh on 2007-12-18
Okay.  I have done all above.  I am still getting the "cannot allocate enough memory" error right after the 'Loading Linux Kernel' screen.

I did with the Kubuntu and Ubuntu... same thing happened with both.  Burned about 6 different disc at lowest speeds and different programs.  All downloads are full and not corrupted.  Anything else I could try.

My computer is fast enough I know that.  What would be giving me a memory error read?  I have 2 1gig sticks in dual channel and a 512 just floating in another channel, all three are brand new.

Thanks guys.

---

### Post by averyh on 2007-12-18
Okay, found out the first problem.  My g-card isn't support.  I still am sent to the Busybox command prompt with the <Initramfs> just sitting there.  The ctrl alt f7 shortcut is that screen.  If I ctrl alt f2 it takes me to a screen that I just left saying Loading...  On my machine with 2.5 gigs of ram is it really going to take over 15 minutes to load?

I waited for about 10 minutes and nothing happened.  Any ideas?  Anything I can do in Busybox when the Initramfs comes up.  Any command to get straight to the install or gui screen?  I don't need gui, just not familiar with linux.  Give me some commands I'll learn them if I need commands.

Thanks,
Avery

---

### Post by rkd on 2007-12-18
It isn't clear whether you tried alienexplorers' suggestion to download and burn the alternate CD and do the install from it.  The alternate CD runs in text mode, so the type of graphics card doesn't matter with it.

---

### Post by averyh on 2007-12-18
> **rkd said:**
> It isn't clear whether you tried alienexplorers' suggestion to download and burn the alternate CD and do the install from it.  The alternate CD runs in text mode, so the type of graphics card doesn't matter with it.

Yeah... I'm actually trying to alternate one now.  I just saw that up there.  I saw the checksum, but looked completely over that. That was before i knew what the alternate version was.  I took that as... trying another version so I went and tried Kubuntu at 32 and at 64bit (since I got a 86-64 processor).

With it taking 30 minutes to download this spanned into the next day and I got an early morning for work.  Hopefully I'll have it installed soon after work.  Looking to learn me some linux today lol.

---

