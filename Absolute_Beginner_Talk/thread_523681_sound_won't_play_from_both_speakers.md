---
title: "sound won't play from both speakers"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Old Jimma on 2007-08-12
Hi Ubuntu Community:

I have a 64 bit Ubuntu machine (asus motherboard, amd64 9pin processor).

I connect a 1/4" jack from that green hole to the RCA ports on the back of my stereo's amplifier and want to play music from both speakers. The stereo tuner/amp seems to work fine: when I play a CD on my stereo, I get music from both speakers.

However, when I play streaming audio from an internet radio station can get sound from only one of the 2 speakers.

What can I do to fix this?

Thanks!
Phil Smith
Duluth, GA

---

### Post by ridgeland on 2007-08-12
What is the cable?
On the PC a single 1/8" plug?
On the receiver two RCA plugs?

---

### Post by Old Jimma on 2007-08-12
Hi. THanks for your reply

The cable on the PC side has a single 1/8" plug that leads to a split: for the  R and L RCA plugs on the stereo amp.

Thanks!
Phil Smith

---

### Post by ridgeland on 2007-08-12
Years ago I used the computer output to a cassette tape recorder using such a Y cable.  I remember I had an inline volume control to keep from overblasting the tape recorder.
Do you get stereo OK with just the PC speakers from the same port?
Did you swap the L and R to see if the sound follows?

---

### Post by Old Jimma on 2007-08-12
Thanks again for your reply.

When I use another Ubuntu computer with the same wire, both speakers work fine.

Phil

---

### Post by ridgeland on 2007-08-12
If the cable is fine then it's likely something in a volume control setting.
You can run the channels L-R independently.  i.e. cut one off.  Open volume control and check the settings (double click on speaker icon)
With qarecord can you see the graph of both channels when you click on [x] capture?  Does take look OK or just one channel?

---

### Post by Old Jimma on 2007-08-15
Hi and thanks so much again for your reply.

I found another green line out jack on the front of my computer's tower. When I plugged my jack into that, both speakers worked. 

I think I have a bumb jack. WOuld you agree??

Thanks,
Phil Smith

---

### Post by ridgeland on 2007-08-16
My PC has a sound system on the mother board that controls two jacks on the front of the PC.  I put a sound card in.  Now I use the jacks on the sound card, the back of the PC.  In the BIOS settings I told it to turn off the sound ports on the front (disable the mother board sound system).
If like my PC you have both a mother board sound system and a PC-card sound system you should check the BIOS and see whats in use.  If you open the PC you can see if the wires to the front come from a card or the mother board.
Glad it works now though.

---

