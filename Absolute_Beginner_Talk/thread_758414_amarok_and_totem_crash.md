---
title: "amarok and totem crash"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-18
my amarok and totem crash when i open them. i messed around with alsamixer to try to get my sound to work. i remember last time i had to turn off the IED or whatever and it fixed my problem, but this time it didn't. how do i fix this and get my sound to work? i have a creative sound card, but when i go into alsamixer, it reads an nvidia driver for my sound instead...is there a way to change that to my creative audigy?

---

### Post by kpkeerthi on 2008-04-18
Disable your onboard soundcard from your BIOS. If your BIOS does not support this feature see 
[Configuring default sound card]("https://help.ubuntu.com/community/SoundTroubleshooting#head-72023a784829d5d128546a6092d67062ab50dfea") from within ubuntu

If your have messed up alsamixer settings, see [Reset mixer settings]("https://help.ubuntu.com/community/SoundTroubleshooting#head-109d4e15b2195ef69e55f12eb2c144e3f2117c03")

Get your sound issues fixed and check if amarok and totem are able to play media. If not, launch totem from command line. It should print some error message on the console and post it back here. 

Command to launch totem ```
totem<press-tab> <press-enter>
```
Command to launch amarok ```
amarok<press-tab> <press-enter>
```

---

