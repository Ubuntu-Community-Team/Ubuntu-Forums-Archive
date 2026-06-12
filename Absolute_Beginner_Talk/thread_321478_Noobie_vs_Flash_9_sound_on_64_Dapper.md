---
title: "Noobie vs Flash 9 sound on 64 Dapper"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by zagu on 2006-12-19
Hello.
I'm yet another newbie who cannot get sound via flash 9. 
Nothing's working and I've been at this a while. 

Here are the specifics:
I'm new to linux and ubuntu but experienced somewhat with windows.  
I've got a compaq r4000 with dapper (64 bit) install. 
firefox2.0 is installed in apps/firefox 
the original firefox1.5 in /usr/lib/firefox
Flash 9.0 d78 appears in about: plugins.
for firefoxrc, I've tried FIREFOX_DSP="arts", FIREFOX_DSP="alsa", FIREFOX_DSP="aoss", etc
flash 7 played sounds on youtube but couldn't load the videos at msnbc.
flash 9 is playing videos everywhere but no sound at all

First question:  I saw somewhere a reference to 64 bit ubuntu and flash 9 sound.  Before I go any further, do I even stand a chance?  I've tried a number of fixes and a number of times I gotten a message about "wrong architecture".  Is it going to work on 64 bit Dapper?

Second question: it seems as if the 64 bit version pops up in forums quite a bit as need an extra hack.  Before I get my system wonderfully tweaked out, should I just start over with the 32 bit.  Do I need the 64 bit?  I don't care about extreme speed.  I care about video/music.  YouTube, MSNBC, etc.  I originally installed the 64 bit version because I thought the 32bit would not work on AMD64.  
 
Thirdly:  if flash 9 works on 64 bit dapper, any ideas what would help me? 

I'm finding the forums quite a help.  Thanks everybody!

---

### Post by pay on 2006-12-19
Try ```
sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

```and change```
FIREFOX_DSP=""
```to```
FIREFOX_DSP="aoss"
```and restart firefox

---

### Post by deadgobby on 2006-12-19
yes you can run 32 on a AMD. 64 bit is like in a infant stage still and still bugs to work work out. 64 bit does run faster, but faster is not all ways better. You can dual boot between the 2 if you wish and see which works for you. You can try to install FF for windows using wine and install F9. Of course if you installed f9, have you try restarting your FF or reboot the system?
Gobby

---

