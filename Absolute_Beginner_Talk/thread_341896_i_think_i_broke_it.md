---
title: "i think i broke it"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by badtubist on 2007-01-19
Hi All,
   I haven't a clue what happened exactly, but some update on synaptic had me remove my nvidia driver.  Everything was running well until that happened.  I was happy to reformat and put ubuntu on again, but now there's no sound going to my speakers now.  I tried using headphones.  I've looked to see if I have a driver for the sound, synaptic says that there's asla installed.  When I hit play on rythmbox or try click on a youtube video, it closes down that application.  Any help would be greatly appreciated.
-Ray

---

### Post by mikewhatever on 2007-01-19
So, you reinstalled Ubuntu because of nvidia driver problem and after that there is no sound, right?

---

### Post by badtubist on 2007-01-19
correct

---

### Post by davebgimp on 2007-01-19
Were you using an Nvidia driver not from the Ubuntu repos? I had that problem recently because i was using the Seveas Nividia driver and it wasn't compatible with the latest kernal update. I removed and reinstalled the driver from the Ubuntu repos and was back up.

---

### Post by badtubist on 2007-01-19
i think so, i used automatix.  i'm not real hip on this stuff, does the nvidia driver affect the sound?

---

### Post by davebgimp on 2007-01-19
Hmm, try completely removing and reinstalling the driver with automatix. if that fails, try the one in the Ubuntu repos. Not sure, but I think that automatix uses the same driver from the same repo anyway.

---

### Post by badtubist on 2007-01-19
okay, i did that and restarted.  still nothin.

---

### Post by davebgimp on 2007-01-19
> **badtubist said:**
> okay, i did that and restarted.  still nothin.

Hmm, did you have Beryl or some other fancy eye-candy installed prior to this happening?

---

### Post by badtubist on 2007-01-19
before my reinstallation I did.  I don't understand why it's not working now that I've installed it again fresh.

---

### Post by mikewhatever on 2007-01-19
Assuming that after the reinstall only the sound is not working, here is the guide: [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

Before you start reading, try checking that your volume is up in alsa settings.

---

### Post by badtubist on 2007-01-19
that's the picture of the speaker on my desktop?

---

### Post by RomeReactor on 2007-01-19
Yes. Or, open a terminal (Applications-->Accessories-->Terminal) and write:

```
alsamixer
```

to check the volume levels. Press ESC twice to exit. Then, still in the terminal:

```
rhythmbox
```

and post the errors (if any) it shows there.

---

### Post by badtubist on 2007-01-19
(rhythmbox:5817): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running
Segmentation fault (core dumped)

---

### Post by badtubist on 2007-01-19
i must head to class, i appreciate everyone's help and hope to resolve this issue at a later time.  adieu

---

### Post by badtubist on 2007-01-19
okay, so what is this MDNS service?  i'm guessing i need that for my sound to work?

---

### Post by RomeReactor on 2007-01-19
I'm guessing this error has to do with listening to radio on Rhythmbox; when i run it from a terminal it gives me the same error, yet i can hear my mp3's . So that's not the problem. Is this the only error Rhythmbox shows before closing? Also, do you have another sound card on your pc?

---

