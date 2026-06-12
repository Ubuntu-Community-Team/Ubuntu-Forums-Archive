---
title: "No sound, Any help would be superly appreciated"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by nintennuendo on 2007-09-30
So I want Ubuntu.  Everything I do in windows I have to do with a professional program because windows can't do it naturally.  Thus, people call me a pirate and accuse me of stealing food out of the mouths of people like metallica and KISS.  Whatever.  I have no sound.  As far as I know, from a topic I made back in Feb, my sound card is Audio: AC'97 2.3 Compliant Audio; Built-in Speakers.   I've never gotten sound to work, no music, movies, system beeps, nothing in alsa mixer helped, but, since i'm not worried about looking a fool, I am not sure I used it right.  I went to the one that was muted, or off, and I press m, it said it came on, but when I closed and went back in, it said it was still muted.  

I really hate windows, especially lately.  It crashed my 320gb external HD and now its crashing itself, just going so much slower than it used to, and I keep it in good shape.  For windows, anyway.  Is there anything I could do, or maybe something in the new beta or the new full release that would help?

---

### Post by Pumalite on 2007-09-30
Try:

 sudo lshw -C sound

---

### Post by Pumalite on 2007-09-30
[http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)
[http://www.daniweb.com/forums/thread38853.html](http://www.daniweb.com/forums/thread38853.html)
[http://ubuntuforums.org/showthread.php?t=26567](http://ubuntuforums.org/showthread.php?t=26567)
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by nintennuendo on 2007-09-30
Heres the output of that command:

  *-multimedia            
       description: Audio device
       product: MCP51 High Definition Audio
       vendor: nVidia Corporation
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

---

### Post by sizzam on 2007-10-02
I'm having the same problem.   The output of the command 'lshw -C sound' is exactly the same as nintennuendo's.

---

### Post by Pumalite on 2007-10-02
[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)

---

