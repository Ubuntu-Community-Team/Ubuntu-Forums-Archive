---
title: "Hard drive access / network access sounds are transmitted through onboard audio jack."
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-04-29
This may sound weird, but whenever there's hard disk access / network access a faint scratching sound comes through my computer speakers.

I know it has to be a software problem because when I mute the sound in Ubuntu it goes away.

Anybody know how to fix this weird problem?

Edit: I've bypassed this problem by going to sound controllers and muting PC speakers.  Still odd how hdd  access would be transmitted through PC speaker but oh well.  *shrugs*

---

### Post by mrpaco on 2007-04-30
This isn't particularly odd.  Any onboard sound card is bound to pick up interference from other compenents of your PC.

---

### Post by tgalati4 on 2007-04-30
What's your hardware?  Perhaps others with similar hardware are having the same problem.  If it is a PCI or ISA soundcard, try moving it to the slot farthest away from the CPU.  

As Linux can add life to old hardware, many folks discover how cheesy the quality is on old sound cards compared to today's iPod and similar mp3 players.

You can try shielding the card with foil and wax paper, but the risk of shorting something inside is usually not worth the improvement of sound quality.

If you have a USB port, then purchase a USB-based sound module.  Since it is outside of the computer, the sound is generally cleaner.  Some are small dongles that cost around $20.

---

### Post by AncientPC on 2007-04-30
> **mrpaco said:**
> This isn't particularly odd.  Any onboard sound card is bound to pick up interference from other compenents of your PC.

Doesn't explain why I didn't get this sound in WinXP.

> **tgalati4 said:**
> What's your hardware?  Perhaps others with similar hardware are having the same problem.  If it is a PCI or ISA soundcard, try moving it to the slot farthest away from the CPU.  

As Linux can add life to old hardware, many folks discover how cheesy the quality is on old sound cards compared to today's iPod and similar mp3 players.

You can try shielding the card with foil and wax paper, but the risk of shorting something inside is usually not worth the improvement of sound quality.

If you have a USB port, then purchase a USB-based sound module.  Since it is outside of the computer, the sound is generally cleaner.  Some are small dongles that cost around $20.

It's onboard audio, specifically an Asus A7M266 motherboard.

Since muting PC speaker through the volume applet, it's apparent that the interference is coming through there.

---

### Post by tgalati4 on 2007-04-30
Go into the Gnome Sound Mixer and try muting or turning down all of the unused channels.  You sometimes have to go into advanced options to display all of the channels available.  

It could be that the Windows driver mutes everything by default.  If you research your soundchip, you can find out all of its capabilities and you can get a better handle on all of the channels (both input and output) and isolate the noise source.

---

