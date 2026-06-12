---
title: "BIOS Bug Found on Startup"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by gaelfx on 2007-08-29
When I startup my computer (it has an AMD Turion 64 processor) running Feisty for 32-bit, there is a line that shows up saying "...PCI BIOS Bug #81...found" and I'm not sure if this is simply related to the fact that I'm running 32-bit on a 64-bit processor or if it is something else entirely. I can startup my computer again and write down the exact phrase that shows up if needed, but I don't want to bother if it's nothing to worry about. My computer seems to work just fine, save for a problem running KTorrent in Gnome and the fact that my internal microphone has never worked (even when I had windows installed).

Can anyone tell me this is nothing to worry about?

---

### Post by bobplano on 2007-08-29
i'm getting the same message(got the same processor and bit version) and so far there's nothing worng that i can see. by the way the message is basically this

 [18.957712] MP BIOS bug 8254 timer not connected to IO-APIC
[0.056745] PCI: BIOS bug #81 [49345000] found

---

### Post by FuturePilot on 2007-08-29
From what I've heard about those errors, they're really nothing to worry about. Linux detected a bug in the BIOS and has found a workaround for it.

---

### Post by nosfed438 on 2007-08-30
i have the same thing too
18.957712] MP BIOS bug 8254 timer not connected to IO-APIC
[0.056745] PCI: BIOS bug #81 [49345000] found

---

### Post by Hobo Joe on 2007-08-30
I find it's useful at times like these, to ask myself, "Do I notice anything wrong", if the answer is no, I just ignore it! :)

---

### Post by Paulmd on 2007-08-30
> **gaelfx said:**
> When I startup my computer (it has an AMD Turion 64 processor) running Feisty for 32-bit, there is a line that shows up saying "...PCI BIOS Bug #81...found" and I'm not sure if this is simply related to the fact that I'm running 32-bit on a 64-bit processor or if it is something else entirely. I can startup my computer again and write down the exact phrase that shows up if needed, but I don't want to bother if it's nothing to worry about. My computer seems to work just fine, save for a problem running KTorrent in Gnome and the fact that my internal microphone has never worked (even when I had windows installed).

Can anyone tell me this is nothing to worry about?

Does updating the bios remove this message?

---

### Post by gaelfx on 2007-09-02
I will try updating the BIOS, but I'm not sure if I'll have an easy time. My computer has a number of quirky things about it (such as it is supposed to have bluetooth but does not, it lacks card reader that is also supposed to have, etc...) because I bought it in China. 

Also, just because I can't notice anything wrong does not mean that there is nothing wrong. KTorrent crashes all the time, amongst other things, and though I doubt that this is unrelated, it still bothers me to see an error pop up anywhere. I just want my computer to be content :D One thing I think it could be is that I'm running the 32-bit version of Ubuntu on a 64-bit processor.

---

### Post by Paulmd on 2007-09-02
> **gaelfx said:**
> I will try updating the BIOS, but I'm not sure if I'll have an easy time. My computer has a number of quirky things about it (such as it is supposed to have bluetooth but does not, it lacks card reader that is also supposed to have, etc...) because I bought it in China. 

Also, just because I can't notice anything wrong does not mean that there is nothing wrong. KTorrent crashes all the time, amongst other things, and though I doubt that this is unrelated, it still bothers me to see an error pop up anywhere. I just want my computer to be content :D One thing I think it could be is that I'm running the 32-bit version of Ubuntu on a 64-bit processor.

You have a lot a little problems? Yes, there could indeed be a common cause.

Do you happen to know the make and model of the computer (or motherboard)?

---

### Post by jw5801 on 2007-09-02
It's not an issue at all. If you ever get a kernel oops or a kernel panic or if it starts freezing then I'd investigate it further.

By the way, I hve the same processor, but I only get the first message:
MP BIOS bug 8254 timer not connected to IO-APIC
because I run 64-bit :p

---

### Post by gaelfx on 2007-09-15
Sorry it's been so long on this one, but here ya go:

My computer is a Compaq Presario V3000 that I bought in China. The wireless goes a little haywire sometimes, KTorrent is constantly crashing, Realplayer has never seemed to work right (though I doubt it would anyways), and, as is a common problem with these ones often, the internal mic has never worked (this includes when I had windows installed when I first got the computer. The hardware is AMD64 Turion, NVidia card, and the MCP51 bridge set for the audio. 

Right now, KTorrent is my only concern, but perhaps I just need to update it? (It's 2.1 now, as complies with the Synaptic listing currently).

On a side note, are they actually releasing Gutsy in October? Perhaps this will fix it? I just hope ALSA 1.0.1.14 isn't included, that messes up Skype pretty good for me.

---

### Post by VraiChevalier on 2007-09-15
I get a BIOS bug message at startup. Haven't been quick enough to read the whole thing though. "Pause" screen button doesn't pause it.

This is on a Gateway notebook with AMD Athlon 64 X2 running 32bit OS.

Even if there are no apparent problems I would still like to know exactly what this BIOS bug is (curiosity).

Would this message be logged in a log file? If yes, any suggestions as to which one I should peruse?

---

### Post by CrazY^ on 2007-09-15
hi there .. i'm new and i have  windows .. imake a boot disk for linux ubuntu 7.04 and when i try to instal him he gave me a error ..

-MP-BIOS Bug : 8254 timer not connected to I0-APIC
-Kernel panic - not syncing:I0-APIC +timer doesn't work ! Boot with apic=debuger and send a report , then try booting withthe 'noapic' option.

Plz tell me what to do to instal ubuntu ..

---

### Post by dptxp on 2007-10-19
I also get some BIOS bug.
Says can not allocate 7 & 8 to PCI resources (I am missing some words here),
I get similar 4 to 5 lines.

ACER 5101 with Turion 64 bit running 32 bit Gutsy.

---

