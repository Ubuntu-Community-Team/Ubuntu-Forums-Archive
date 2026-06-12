---
title: "Media player problems"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by Wadeisabeast on 2006-07-26
I have two problems with Xubuntu right now.

First, with Xfmedia, the color fades to black and white after watching about 10 videos.  I have to log out and back in to regain color.  Is there any way to fix this.

Second, I have no sound on the computer at all, and heard in another thread that my sound card wasn't recognized because it is an older computer.

Please explain your answers/instructions as simple as possible because I know virtually nothing about Linux.

---

### Post by Sef on 2006-07-26
What is your sound card and computer specs?

---

### Post by ndyguy on 2006-07-26
> **Wadeisabeast said:**
> I have two problems with Xubuntu right now.

First, with Xfmedia, the color fades to black and white after watching about 10 videos.  I have to log out and back in to regain color.  Is there any way to fix this.

Second, I have no sound on the computer at all, and heard in another thread that my sound card wasn't recognized because it is an older computer.

Please explain your answers/instructions as simple as possible because I know virtually nothing about Linux.

I've never heard of your first problem, so maybe someone else can help you with that.  Since I don't know what kind of sound card you have I'll assume you've:
[LIST]
verified your speakers are hooked up correctly (and turned on)
[/LIST]
[LIST]
you've checked the volume setting on the speakers and in Xubuntu to make sure it isn't muted or too low
[/LIST]  
I'm sure you've already checked this stuff I'm just listing it in case you forgot.  So maybe this might help:
[https://help.ubuntu.com/community/HowToSetupSoundCards?highlight=%28card%29%7C%28sound%29]("https://help.ubuntu.com/community/HowToSetupSoundCards?highlight=%28card%29%7C%28sound%29")
[https://help.ubuntu.com/community/SoundcardsWithHardwareSynth?highlight=%28card%29%7C%28sound%29]("https://help.ubuntu.com/community/SoundcardsWithHardwareSynth?highlight=%28card%29%7C%28sound%29")
[https://help.ubuntu.com/community/forum/hardware/OldSoundCard?highlight=%28card%29%7C%28sound%29]("https://help.ubuntu.com/community/forum/hardware/OldSoundCard?highlight=%28card%29%7C%28sound%29")

---

### Post by Wadeisabeast on 2006-07-26
> **Sef said:**
> What is your sound card and computer specs?

I have a Pentium III processor, 128mb ram, and 10gb hard drive.  Do I have to open up my computer to see what the sound card is? I don't even know where it's located.

---

### Post by OU812 on 2006-07-27
Maybe you're having video problems because you have 128 mg of memory. Perhaps logging out and back in flushes memory.

Here's a simple trick to try and fix your sound card. In a terminal do

sudo alsamixer

Turn up the main and pcm volumes and make sure no options are set to mute. When you are finished, hit esc. Otherwise you have to follow the advice of previous posts. If you have windows installed, you can find the soundcard you have by right-clicking on "my computer" and choosing properties. Click on the hardware tab and look for a soundcard. Click on it and it should tell the specs of your soundcard.

john

---

### Post by shibujnu on 2008-04-10
what is the reason for showing only black & white pictures in media player?

---

