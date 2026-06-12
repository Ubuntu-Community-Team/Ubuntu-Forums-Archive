---
title: "Sound doesn't always work"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by NiGHTS7041 on 2007-06-02
So maybe about 1/4 of the time, the sound will work on my computer. If I open up something like XMMS and try to play a song, the program will just crash. Or if I try to play a song file using VLC, it too will crash. I have to restart my computer about 3 times in order for the sound to finally work. The sound is the only problem. If I play a video file, the movie will play, but no sound will be there, and eventually the program will crash. 

What could be the problem?

Thanks in advance. :)

---

### Post by Happy_Man on 2007-06-02
What's your sound card?

---

### Post by deadgobby on 2007-06-02
I have the same problem when recording with Audacity or just like you. Run XMMS and puff it crashed. I have a SB Live card. I am not at home so I'll be watching this post too.

---

### Post by NiGHTS7041 on 2007-06-02
I am not sure if I did this right, but this is the information my computer gave me...

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by NiGHTS7041 on 2007-06-02
help?

---

### Post by trunks14 on 2007-06-03
i have the same problem...

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
	Subsystem: ASRock Incorporation: Unknown device 1617
	Flags: medium devsel, IRQ 185
	I/O ports at e000 [size=256]
	Capabilities: <available only to root>

 i wasn't able to play any sound yesterday, when i turned my computer on today the sound just wroked, now i hear no sound ¬¬, but XMMS doesn't crash or anything, however if i boot to Windows everything is fine with the sound.

sound sound where is my sound

Anyway, your support is highly appreciated.

---

### Post by Happy_Man on 2007-06-03
Run ```
alsamixer
``` in a terminal, and see if all the sliders are set to max. If not, do that, and then check the sound.

---

### Post by NiGHTS7041 on 2007-06-03
ya, the sliders for me are to the max, and yet my sound still will not work. Any application that I use still crashes once sound starts to play.

---

