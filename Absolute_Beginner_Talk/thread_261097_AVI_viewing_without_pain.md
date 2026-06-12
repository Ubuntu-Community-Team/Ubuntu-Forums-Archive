---
title: "AVI viewing without pain?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by feap on 2006-09-19
I'm an absolute newbie to linux and ubuntu and can't get .avis (xvid, divx) files to play. I don't have codecs installed for totem and after doing some googling found out that xine, mplayer or vlc are better. But all the installation instructions require extensive use of command line shell which I'm not comfortable with.

So, is there a video player with automagic codec downloader which has a graphical installation UI and/or an easy wizard that doesn't make my balls shrivel in fear?

---

### Post by maneesh77 on 2006-09-19
gxine is pretty good and you can download it and it's plugins through the synaptic package manager. it plays avi, mpeg and divx, mp3, windows audio/video, DVD. Infact the only problem I've had with it so far is with VCD's. it's moody with them , sometimes playing sometimes not.

For more info just search this forum for keyword Xine, gxine

---

### Post by jISh on 2006-09-19
I suggest Mplayer. 
*sudo apt-get install w32codecs* might also help you.
Also the gstreamer plugins (good, bad, and ugly)
*apt-cache search gsteamer-plugins *in terminal for exact package names.

---

### Post by Brownedwg89 on 2006-09-19
i would suggest vlc
to install it use the command:
```
sudo apt-get install vlc
```

also, you should be able to find it somewhere in synaptic

---

### Post by JAwuku on 2006-09-19
If you want a one-stop GUI solution to installing codecs, you can always try **_Automatix_**.

Instructions to install it are at [http://ubuntuguide.org/wiki/Dapper#How_to_install_Automatix_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Dapper#How_to_install_Automatix_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)

---

### Post by feap on 2006-09-19
Thanks for the quick help! I was able to install VLC and watch the latest episode I just downloaded after I figured how to enable universe. Much appreciated!

---

### Post by GoombaDoolies on 2006-09-30
None of the above suggestions worked for a file I have.  It won't even give me the info on the file, but I think it is an avi with an Xvid video codec, not sure about the audio, but it won't play.

---

