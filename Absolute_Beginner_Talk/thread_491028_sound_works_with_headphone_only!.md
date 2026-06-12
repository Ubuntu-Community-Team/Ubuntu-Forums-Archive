---
title: "sound works with headphone only!"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by m_o_b on 2007-07-03
the sound works good on the headphone (just knew about it) but not working on the Laptop's speakers!!!!!!!!!!!!

the result of lspci command is

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)



i'm using my laptop

---

### Post by meborc on 2007-07-03
sounds like a hardware problem (physical)... does the same thing happen in any other os (if you dual-boot, check it)... how old is your laptop? may be it is just broken?

---

### Post by m_o_b on 2007-07-03
that happened with all linux distros that i tried.

while with windows the sound works just fine (both vista and xp).

my laptop is about 2 years now. all other hardware been recognized by linux and working perfectly.

but i don't know why the sound worked with headphone but not working with the laptop speaker.

---

### Post by meborc on 2007-07-03
> **m_o_b said:**
> that happened with all linux distros that i tried.

while with windows the sound works just fine (both vista and xp).

my laptop is about 2 years now. all other hardware been recognized by linux and working perfectly.

but i don't know why the sound worked with headphone but not working with the laptop speaker.

that is really strange... i'm no sound wisard, so i can't help you... hopefully somebody can :)

---

### Post by expatCM on 2007-07-03
you may want to open alsamixer from root and have a look at the slider and mute settings.

---

### Post by m_o_b on 2007-07-03
i tried m8 but doesn't work yet:(:(:(

---

### Post by ugm6hr on 2007-07-03
If headphones work, but the speakers don't, it must be a volume control issue (if the speakers work in WIndows), as suggested by expatCM.

Alsamixer (from Terminal) should be the answer.  Unmute all volumes (press M), and maximise (up arrow) all volumes - specifically PCM, surround, centre (move between with left/right arrows).

---

### Post by m_o_b on 2007-07-03
i did all of those except when i unmute the other stuff surround ...etc it does unmute them but i can't up the volume except the pcm and the speaker control the volume at it highest the other is unmuted but set to 00 and i can't move them up or down.

---

### Post by ugm6hr on 2007-07-03
Hmmm... maybe try
```
sudo alsamixer
```

---

### Post by Lord Illidan on 2007-07-03
It could also be a problem with the alsa drivers being too old. Similar thing happened with my dad's laptop. In that case, you'll have to compile new alsa drivers yourself.

---

### Post by m_o_b on 2007-07-03
the problem whenever i try to install something from the source file it doesn't configure it cuz after configure it make doesn't work it says make not found or something like that.

when it configure a lot of the lines it shows goes (no) usually the last lines (i guess it was c++ and other things i don't know).

---

### Post by m_o_b on 2007-07-04
i download the latest alsa driver but still the sound only works with headphone:(

---

### Post by expatCM on 2007-07-04
This sounds rather like a problem I have with sound right now .....  it seems that sound cards were designed for Windows and since the manufacturers are not too friendly in either offering drivers or giving documentation there are many strange things that can happen.

Even with an integrated sound card you are going to experience the same challenges.  I take it that you had a look round the laptop manufacturers web site to see if there is any support there?  Have you had a chat with the local laptop authorized dealer, sometimes they have some great ideas....  ?  If you have experimented with alsamixer and there is no joy then your options are going to be rather limited....

---

