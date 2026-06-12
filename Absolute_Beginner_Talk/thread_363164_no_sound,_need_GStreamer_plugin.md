---
title: "no sound, need GStreamer plugin"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by J-me on 2007-02-16
HI I used Linux for a few weeks last year was loving it but it kept just turning my pc off randomly, so I gave up.

I'm back for round 2 gonna give it another go, hasn't turned of yet. 

K my problem I tried running Linux of the live cd fine and it all worked with sound but i did a full install now the sound has gone. When I click on the sound icon at the top it says i need GStreamer plug in.  So I went onto synaptic packages manager and did a search for this add on and downloaded 10 files with this word in it. None solve the problem.

Any ideas?:confused:

---

### Post by jonathan.lees on 2007-02-16
I had this problem, it turned out that my User Privileges had got messed up. Perhaps it's the same on your system. Here's what I did:
Open System> Users and Groups and highlight your Username, click on Properties and click the User Privileges tab, make sure everything has a tick in the box especially Use Audio devices.

---

### Post by old_geekster on 2007-02-16
If you have Alsamixer GUI or Gnome ALSA Mixer, check to assure that the correct sections are not "Muted".  I was getting sound only from my front speakers and two of the boxes weren't ticked.

---

