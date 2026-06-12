---
title: "Creative Sound card, no sound for some things"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Stunned_flounder on 2008-02-18
Hey everybody,

I've had Ubuntu for about a week now, (Gutsy) and I've been trying to figure out what I've done wrong with my sound card.

I have a Creative Audigy SB2 SE, and while Rhythmbox and Movie Player play sound, I can't figure out how to make sound work in Skype and on Firefox (videos on Youtube, etc...)

I looked through a lot of the other sound help threads, and followed some of the guides, but it's still not working.  Is there something I missed?

---

### Post by Arthur Archnix on 2008-02-18
The fact that sound works means you've likely just not configured skype correctly. If you go into your sound properties {>system >preferences >sound} you'll see a bunch of drop down boxes and a test button. They should all be set to autodetect, but you can try different ones and hit test. This way, you'll learn a bit more about your sound system, what works, what doesn't. 

Now you can go into Skype, get into the Options, and click on the Sound Devices tab on the left. Sound out is what you hear, Sound in is what you say. They're both probably on "default device", but if not change them to that and test. Keep changing the Sound Out and hitting test until you hear a sound.

If you don't hear a sound from Skype, but you can hear a sound from RythymBox, then maybe you ought to try upgrading to the latest version of Skype. You can download the latest version (with video support!) from their website. If you already are using the latest version, then try removing that version and installing the version through apt.

As for hearing sound on YouTube, that's probably a flash issue. Can you hear sound in any flash? Try going to different sites and seeing if any of them give you sound with flash. If not, you need to either confirm your install (or else reinstall) the flashplugin-nonfree, as well as the mozilla flash plugin. Both those are available through synaptic if you search for flash.

---

### Post by Stunned_flounder on 2008-02-18
I noticed that in my sound preferences, the only device that would create a beep was ESD (Elightened Sound Daemon) and not my sound card (ca0106).  Did I not install the sound card right?  Somehow Rhythmbox and Movie Player both work, but everything else doesn't.

---

### Post by Arthur Archnix on 2008-02-18
Well, esd doesn't work at all on my system. So why not change everything there to ESD, then try setting things in Skype like I suggested and see what happens. If you still can't get sound, post back with the output of:
```
lspci | grep Audio
```

---

### Post by Stunned_flounder on 2008-02-18
The thing with ESD is that it's only being detected in sound preferences.  I have no idea what it is that put it there, but it's not an option with Skype's device detection.

Is there a step that I might have skipped when I was setting up my sound card?  I thought I followed the guide on the forums pretty closely, but now I'm getting the feeling that I didn't.

---

### Post by Arthur Archnix on 2008-02-18
I can't say, not without seeing what card you have and what guide you followed. It sounds like some extra work was required on your part to get the sound going? If so, please post details of what you did, the link for the instructions you followed, and any other details you think might be useful.

---

### Post by Stunned_flounder on 2008-02-18
I used the Comprehensive Sound Problem Solutions Guide ([http://ubuntuforums.org/showthread.php?t=205449&highlight=creative+sound+blaster+driver](http://ubuntuforums.org/showthread.php?t=205449&highlight=creative+sound+blaster+driver)) and got to about step 4 in the general help area where it starts talking about alsamixer when I stop being able to get things to work.  I just might have not understood the instructions well enough.

By using ```
lspci -v
``` I have a Creative SB Audigy LS card as my multimedia audio controller,  The readout for it is:

01:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 64, IRQ 23
        I/O ports at 9800 [size=32]
        Capabilities: <access denied>

I think that my motherboard also has an onboard sound card, but when I was using Windows I just had it run everything through the Creative card.  Is there a way I can make the Creative card the default for everything?

I think

---

