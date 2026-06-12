---
title: "How to enable the internal speaker on a Mac mini G4."
date: 2010-12-12
forum: Apple Hardware Users
---

### Post by jdp on 2010-12-12
I've got a final revision of the G4 Mac mini, the 1.5GHz model, dual booting 10.04 LTS and OS X. One of the issues I've had is that the internal speaker doesn't work under Linux, or so it's been reported on various post and sites. It turns out it's a simple matter of flipping some ALSA control options. With an ALSA mixer you must enable both the Speaker and the Headphone to get audio to play over the internal speaker. It will still play over the external headphones/speakers if they are still plugged in. I'm not sure if this is a problem with the ALSA, OSS, PCM or snd_powermac drivers or just something setup wonky in the configs. I've used both GNOME ALSA Mixer GUI and the alsamixer command line tool to do this. The alsamixer tool will mostly work in an X-term, as the F-keys don't pass though. It is fully functional on a console login. I also noticed that audio plays back per-user. When I switch from X to a console he sound is cut off, and when I get logged in as the same user the audio comes right back in.

---

### Post by linuxopjemac on 2010-12-12
forget my post, didn't read well.

---

### Post by KiwiPal on 2012-04-20
Hello! I came across your post while searching for solutions to my sound problems (see **Ubuntu 12.04 on PPC Mac mini: Dummy Output for sound card?**). I realise that you were/are using 10.04, but could you please talk a Linux newbie through the process of getting sound to work through the headphones socket or internal speaker? (BTW, mine's a 1.42GHz G4 Mac mini.) Thanks in advance for any help you may be able to give, Ade

---

