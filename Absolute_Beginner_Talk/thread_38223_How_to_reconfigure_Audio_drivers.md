---
title: "How to reconfigure Audio drivers"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by salman_arabi on 2005-05-30
Can somebody please tell me how to reconfigure the audio drivers. Thanks in advance.

---

### Post by Kyral on 2005-05-30
Eh, what do you want to reconfigure them to do exactly?

---

### Post by salman_arabi on 2005-05-30
I am not able to listen to any audio, even .wav file. When I see the device manager I can see that, correct  audio driver has been configured but no sounds. Please help me, working for past one week on this issue.

My audio drivers information.
Via technology inc.
VT8233/A/8235/8237 AC97 Audio.

---

### Post by mohaham on 2005-05-30
It would be helpful if can post you hardware specs.
What kind of problem are you facing., do you have sound or no sound at all....
what sound hardware do you have..you can check that with this command.
sudo lspci -v | grep audio

Here are some places you might want to check first..
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)
[http://www.ubuntulinux.org/wiki/SoundProblemsHoary](http://www.ubuntulinux.org/wiki/SoundProblemsHoary)
[http://www.ubuntulinux.org/wiki/MplayerInstallHowto](http://www.ubuntulinux.org/wiki/MplayerInstallHowto)

---

