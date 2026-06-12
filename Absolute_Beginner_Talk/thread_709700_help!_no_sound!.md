---
title: "help! no sound!"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by anemptygun on 2008-02-27
I'm not sure what to do, I put a new sound card in my computer and I can't get any sound. When I open up volume control I have the proper sound device selected ( Esoniq AuidoPCI Alsa ). Plus I went under sys prefs to sound and made sure I had that device selected under there as well. I'm kind of lost, any advice?

thx

---

### Post by christina_svats on 2008-02-27
is any controller muted in alsamixer? You can see that if you type:
```
alsamixer
```
in a terminal

---

### Post by anemptygun on 2008-02-27
I does not appear so. But it is not showing the proper device when I type in alsamixer. Could that be it?

---

### Post by christina_svats on 2008-02-27
do you have any sound if you use your onboard audio device? What's your lspci output?

---

### Post by anemptygun on 2008-02-27
yes I do have sound with my onboard device. Here is my output.


00:00.0 Host bridge: nVidia Corporation Unknown device 0071 (rev a3)
00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:05.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:06.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:07.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
06:06.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
06:07.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
06:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

---

### Post by christina_svats on 2008-02-27
Well, I guess that the new card should appear in alsamixer, but I don't know how to fix this since you said that the proper card is already selected in volume control. What do you see in System>Preferences>Sound?
Maybe it's a drivers issue, are you sure the proper ones are installed?

---

### Post by anemptygun on 2008-02-27
When I go to sysprefs, sound, I can see both the onboard sound and the sound card. But the trouble with downloading drivers, is that I don't know what card it is. I know it is a creative, but the model I don't know. I just picked up the card at a local computer shop with no box.

---

### Post by xeth_delta on 2008-02-27
> **anemptygun said:**
> When I go to sysprefs, sound, I can see both the onboard sound and the sound card. But the trouble with downloading drivers, is that I don't know what card it is. I know it is a creative, but the model I don't know. I just picked up the card at a local computer shop with no box.

May I suggest disabling the onboard card in BIOS? I agree with christina_svats, there might be an audio driver misconfiguration. If what I suggested does not work, please, also post the output
```
sudo lshw -C sound
```

---

### Post by christina_svats on 2008-02-27
please post your 
```
lspci -v
```
results...

---

### Post by anemptygun on 2008-02-27
Hooray that worked! Thank you both xeth_delta, and christina_svats. I love these forums! If I have any see any other problems with it I will post here later, Thanks!

---

### Post by xeth_delta on 2008-02-27
> **anemptygun said:**
> Hooray that worked! Thank you both xeth_delta, and christina_svats. I love these forums! If I have any see any other problems with it I will post here later, Thanks!

You are most welcome! What was the solution in the end, the BIOS action?
Remember to please mark the thread as solved. Good luck!

---

### Post by anemptygun on 2008-02-28
Yes, the BIOS action resolved it. But one more question.. How can I disable the mic input from playing back on my speakers?

---

### Post by christina_svats on 2008-02-28
I think it has something to do with the Capture Feedback controller on your Volume Control, or with Analog Mix. Try playing with these, maybe you 'll get lucky!
Sorry I can't be more certain about this...

---

