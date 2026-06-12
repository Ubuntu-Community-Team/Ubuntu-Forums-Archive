---
title: "Sound output and various peripheral issues"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by Landslide on 2006-05-31
Since this is my first post, and it is mildly relevant to my questions, I'll give a brief narration of how I came to use Ubuntu. I mostly use my PC (Alienware Area-51m 7700 Laptop) for gaming and music production (on Windows of course). I downloaded the Ubuntu 6.06 Release Candidate live CD after seeing it on the internet, and I liked it a lot. I started thinking about the programs that I used on Windows - Teamspeak, UT2004, Quake 4, [Legends]("http://www.legendsthegame.net"), Firefox - and how everything I use on Windows, except for the music production software, had Linux versions. I had previously used Red Hat to run Eclipse for a Java programming course at my university, and my experiences with it had been 100% positive. Both of those factors, combined with a large amount of time on my hands, caused me to use the live CD to install Ubuntu to one of my HDDs, leaving Windows on the other one.

So far I have successfully installed Teamspeak, UT2004, Quake 4, and [Legends]("http://www.legendsthegame.net"), but I still have a few issues that I have been unable to resolve. Rather than clogging this busy forum with several isolated requests for information, I thought it would be best to sleep on my problems, search around, and then post all my remaining issues in one thread:

**Creative Sound Blaster Audigy 2 ZS PCMCIA**: This is a notebook soundcard that I use. It plugs into the PCMCIA slot. If I plug it in while the power is off and then boot Ubuntu, it recognizes it (I see it in the System->Preferences->Sound menu under the Default Sound Card drop-down) but if I select it as the default, sound comes out of my laptop speakers instead of out of the card, just as if I didn't have it plugged in at all. I thought maybe the setting needed a reboot to be applied, but it didn't change anything.

**Logitech Premium USB Headset**: Since my sound card wasn't working, I tried using this headset, since I had one lying around. Ubuntu recognized it automatically, and the sound works fine. However, it has problems with the microphone. Whatever comes out of the microphone, I can hear in the headset, but both Teamspeak and the Sound Recorder seem unable to "hear" it.

**Onboard Sound**: I have a Logitech PC Gaming Headset. It came with a friend's copy of UT2004, and he let me borrow it. It's a standard analog headset, with two 1/8" jacks, one for the headphones and one for the microphone. It works with Teamspeak using the onboard sound, and I got the mic working OK, but when I use the onboard sound, I can't run sound from both Unreal Tournament 2004 AND Teamspeak at the same time. It gives me the sound from whichever I run first, leaving the other one mute.

So I have three different ways to use sound, but none of them work properly. I don't need all three of these problems resolved, just one. If I can get just one of those methods to work, I'll be happy. On to the other issues:

**Quake 4 and Legends**: The sound output (using onboard sound) is garbled, sounding like the audio grains are being dramatically shifted and sent through reverb.

**Logitech MX518 Mouse**: I love this mouse, and it seems to work well with Ubuntu, but it might actually be working *too* well. I plug it in through the USB port and it works as a basic pointer device, but the DPI switching "feature" that Logitech included that I disable on Windows, defaults to active (like it does on Windows) but the bad part is that I cannot turn it off. Under Windows, I bound the sensitivity switch buttons to keystrokes instead, but I am unsure of how to do that also. Would it be possible to install the Windows drivers for the mouse and run them through an emulator? Would that lag the mouse? Also, I couldn't find a way to disable mouse acceleration, the anathema of FPS players everywhere. Is there a way to do it that I just couldn't find?

I think that covers my remaining issues. So far Ubuntu has been a fairly solid OS, and if I can get these issues resolved, I'll be downright ecstatic about it! If you made it through this long winded post, thanks for your time. I greatly appreciate your help!

---

### Post by Landslide on 2006-06-01
I fixed my Quake 4 issue by adding "+set s_driver oss" to the end of the Quake 4 launcher command in the top menu bar. My sound issues in Legends, as well as the other problems, continue to plague me. Any kind Linux wizards have any ideas?

---

### Post by Landslide on 2006-06-02
Thanks to my friend Gemini, who pointed out [this]("http://ubuntuforums.org/showpost.php?p=1081557&postcount=295"), I got more of my buttons working with the MX518, namely the side buttons and the mouse wheel. The application switch button still shows up in xev as "mouse1", and xev doesn't recognize the sensitivity up/down buttons (though they do still switch my sensitivity). Also, I haven't been able to disable mouse acceleration.

Because of all these problems, I am finding it very difficult to use my computer properly. The only thing I can successfully do in Ubuntu is use Firefox! If nobody knows the answers to my problems, then could someone tell me if there's a way to reduce the size of my ubuntu partition and create a new FAT32 data partition so I can have additional Windows space? I was hoping to be able to run all my games on Ubuntu, but with all these problems I'll have to run them on Windows instead, which means that Windows will need most of the space.

---

### Post by spartan777 on 2006-06-07
i found a how-to for teamspeak on linux.

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound)

its pretty thick, and i'm just getting into it, so if i have some tips, i'll help.

---

### Post by VictorE on 2006-07-25
landslide, were you able to get your sd/cf/mem stick card reader working?  i've got a 51m as well and overall, I've gotten ubuntu to work with most of my peripherals.  while i'm looking for a solution, i've been using a usb to sd card reader, but i'd love to get the internal one working.

---

### Post by Landslide on 2006-07-25
Hmm, I don't recall. I don't own a digital camera, so I don't ever use mine. In fact, I disabled it from the BIOS since it was taking up so many drive letters in Windows. Maybe you should check to see if you've accidentally disabled it in the BIOS? Other than that, I don't really know... sorry. :(

---

### Post by VictorE on 2006-07-25
It works under Windows, so I'm pretty sure it's enabled in the BIOS.  What about getting your vid card to run in hardware acceleration mode?  Do you have a AT or nVidia card?

---

### Post by Landslide on 2006-07-25
ATI Radeon X800 Mobile. In ubuntu I use the FGLRX drivers.

---

### Post by fakie_flip on 2007-06-09
Where you ever able to get Legends and Teamspeak working together? I have been having problems with that. Legends crashes and has no sound while running Teamspeak or Skype.

---

### Post by Landslide on 2007-06-09
No, unfortunately. I gave up.

---

### Post by fakie_flip on 2007-06-11
> **Landslide said:**
> No, unfortunately. I gave up.

So did I. I tried everything, artsdsp with artsd, esddsp with esd, jackd and joss, aoss both 32 bit and 64 bit, and nothing worked, but those do work for my friends. Recently I got a new game in Linux, Postal 2, and it's been fun. Only Skype works with games that were made to use Alsa, not OSS, and Teamspeak doesnt work with any games.

---

