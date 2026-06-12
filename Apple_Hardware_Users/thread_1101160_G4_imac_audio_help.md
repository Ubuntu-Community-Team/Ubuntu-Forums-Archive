---
title: "G4 imac audio help"
date: 2009-03-20
forum: Apple Hardware Users
---

### Post by Slappey on 2009-03-20
Ok, so i've tried searching, and reading around the forums, to try to get my audio to work, but unfortunately I've yet to get it working. Any chance someone could walk me through it step by step on how to get it working?

I tried running alsa mixer from terminal, but nothing happened, then i tried running sudo modprobe snd-powermac, which made it so when i hit backspace, it would beep at me, but otherwise, i couldn't get a single sound out of the machine.

Any suggestions?

Thanks in advance for your help, 
~ Teh Slapz

---

### Post by tiresia on 2009-03-20
which version have you installed?
When you load the module snd-powermac can you hear also music if you insert a music cd?

---

### Post by Slappey on 2009-03-20
> **tiresia said:**
> which version have you installed?
When you load the module snd-powermac can you hear also music if you insert a music cd?

8.10, I don't know, I haven't tried, Gimme a sec to find a cd, and see if it works.

/edits

Yes, I can, is there a way where I could manage the audio levels though?

---

### Post by tiresia on 2009-03-21
> **Slappey said:**
> Yes, I can, is there a way where I could manage the audio levels though?

If that module works for you, add it to the list of module that the kernel loads at boot up.
```
sudo nano /etc/modules
```
Exit (ctrl-X) and save (say 'Yes')
Restart the computer to check it is working

To manage audio and volume control:
alsamixer (in a terminal)
volume control (in GNOME System > Preferences > Volume Control)

---

### Post by Slappey on 2009-03-22
thanks, got it working after the restart.

thanks for your help,

~ Teh Slapz

---

