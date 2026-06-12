---
title: "I broke my sound"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by DoubleR on 2007-12-26
My sound stopped working after I uninstalled Amorok. Sound was working while I tried out the KDE software. I am running Gutsy Ubuntu on a Toshiba satellite M45 notebook. I will continue to search the thread for a solution and would appreciate any suggestions on where a solution may be found I did try using alsamixer and all the volumes seem to be turned up. Oh and if I boot into windows sound works fine so It is not a hardware problem

---

### Post by icheyne on 2007-12-26
Some good troubleshooting links here [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by DoubleR on 2007-12-26
Thanks I glanced though this and it looks like a very good tip with a good trouble shooting plan.  I really had no idea where to begin. I will have some time later today to give it a whirl and will report back

---

### Post by DoubleR on 2007-12-27
Sound still not working after these action were taken
I went through these trouble shooting guides

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) (including  getting drivers from *fresh* kernel)
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

I logged into another profile on the laptop to check  for sound

I reinstalled Amarok (seemed sort of pointless but I tried it nonetheless since removal of the program started the problem)

Here is what I think I know
Intel ICH6 is recognized and drivers are installed
Intel ICH6 is 0 so audio programs should point to and use this audio device
Alsamixer used to make sure channel volumes are up and several variations of muting and unmuting some of the likely unused channel were attempted

So sound is still broke.  I am a Ubuntu noob but I want to avoid my typical noob response to just reinstall Gutsy.  I would likely not have to do this in Windows so I should be able to learn how to do it right in Linux.

My guess it is something easy I am overlooking.  Perhaps the issue is from installing some parts of KDE (Kbuntu) that came with Amorok so that when Amarok was removed it unistalled some sort of shared configuration or other text file file needed for the driver to work properly that is not the same Ubuntu.
.

---

