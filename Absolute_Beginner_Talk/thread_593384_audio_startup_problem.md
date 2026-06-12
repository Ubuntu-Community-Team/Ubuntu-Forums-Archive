---
title: "audio startup problem"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by stanlavisbad on 2007-10-27
i'm using gutsy, but also had the same problem on feisty. on startup, there is often no sound. I have to restart, sometimes several times, to get audio to work. in XP i had no problems with this, so i don't think it's a hardware issue. I thought maybe it is a driver issue, but if so then surely it just wouldn't work at all?

any ideas?

---

### Post by whoeva on 2007-10-27
I have the exact same problem. Fiesty and now Gutsy!

---

### Post by stanlavisbad on 2007-10-28
i'm glad it's not just me! is there anyone out there who can help?

---

### Post by stanlavisbad on 2007-10-30
it also seems to be worse in gutsy. i'd really appreciate it if anyone had any ideas about this, it's a very annoying problem

thanks

---

### Post by whoeva on 2007-11-01
Just our little problem then!

Well, something I noticed was that this seemed to start happening when I plugged in my USB headset. After recently rebooting 3 times and getting no sound (even though the test function in sound options was working, normal sound was not) I decided to try unplugging the headset.

I have not had the problem since so maybe you have a similar sound device attached?
Just a thought that may help.

---

### Post by thesm on 2007-11-01
Based on the fact that it occurs intermittently I doubt this will help, but it's worth a try.  Go to a terminal and type **alsamixer**.  This shows you all the volume settings, double check that none of the output is muted.

Good luck :)

---

### Post by tinaandlee on 2007-11-01
I (had) the same problem with Gutsy. For me, the problem is that sound would always start with the ubuntu drumming tune, then, more often than not, a particular part of the start-up tune would freeze with a continuous cycle of a sound slice.

I tried to change some settings and, becuase I'm a newbie who doesn't have a clue, I managed to completely rid my laptop of sound all together.

I did a complete fresh install and found that the sound worked fine. I then anabled my microphone and saw that the sound problem came back. I then remembered that my previous problems with the sound came about just after trying out some SIP sofware, which, of course, needed me to enable the mic. So as lond as I don't enable the mic. I have no iussues.

Does anyone know why I would have this issue?
Thanks in advance :-)

---

### Post by stanlavisbad on 2007-11-01
no, no and no. :-(

mute is not on.

tried unplugging all usb devices; no difference

i don't get the drumming sound at all when it doesn't work. my mic is muted unless i am using it.

---

### Post by xjgnsdof on 2007-11-04
Same problem, here. I have to restart many times before I get sound.

---

### Post by linas on 2007-12-14
Me too.

"Just restarting" is not the answer: either it works out of the box, or it doesn't. 

In my case:
lspci shows:
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

so this is not a USB device, like some of the other M2N-E boards.  According to the book, this is code name "Azalia", which the Linux kernel knows as "Intel High Definition Audio" (even though this is an AMD64 board).

lsmod shows: 
snd_hda_intel         267164  1 

plus a bunch of other gorp. So this shows that the right kernel modules is being loaded.  However, there is nothing in dmesg to indicate that this module is doing anything at all.  Hmm. I wonder if I need to turn off PCI MSI?  I haven't tried that ... don't even know if its on. 

Haven't got even a peep out of this, not by using any low-level tests, or System->Preferences->Sound or anything.

---

### Post by redneb on 2008-01-25
I had the same problem.  Running the command below will set your startup (boot) volume - to your current volume setting.  

sudo alsactl store 0

---

