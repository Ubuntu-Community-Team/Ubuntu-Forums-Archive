---
title: "gutsy no sound"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by p-real on 2007-12-17
my alsa pcm is full my vol i maxed on both media player and mixer and the most i get is but a whisper. please help me i have a toshiba satalite sk9 a100.

---

### Post by Dynaflow on 2007-12-17
I had trouble with sound on a laptop install recently too.  Take a look at [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html").  Using the latest version of ALSA solved my sound problems straight away.

---

### Post by p-real on 2007-12-17
ok im very new to this i admit i tryed inputing 
p-real@reality-p:~$ sudo sh alsa_2.sh
sh: Can't open alsa_2.sh
p-real@reality-p:~$ sudo sh alsa_1.sh
sh: Can't open alsa_1.sh
p-real@reality-p:~$ alsa-driver-1.0.15.tar.bz2
bash: alsa-driver-1.0.15.tar.bz2: command not found
p-real@reality-p:~$ sudo alsa-driver-1.0.15.tar.bz2
sudo: alsa-driver-1.0.15.tar.bz2: command not found
p-real@reality-p:~$
 into my terminal but as u can see im spinning my wheels i must be missing sumthing where do i start

---

### Post by spec456 on 2007-12-17
What type of sound card do you have?

```
lpsci | grep -i audio
```

---

### Post by Dynaflow on 2007-12-17
> **p-real said:**
> ok im very new to this i admit i tryed inputing 
p-real@reality-p:~$ sudo sh alsa_2.sh
sh: Can't open alsa_2.sh
p-real@reality-p:~$ sudo sh alsa_1.sh
sh: Can't open alsa_1.sh
p-real@reality-p:~$ alsa-driver-1.0.15.tar.bz2
bash: alsa-driver-1.0.15.tar.bz2: command not found
p-real@reality-p:~$ sudo alsa-driver-1.0.15.tar.bz2
sudo: alsa-driver-1.0.15.tar.bz2: command not found
p-real@reality-p:~$
 into my terminal but as u can see im spinning my wheels i must be missing sumthing where do i start

Ah, I see what wasn't explained.  Type ```
gedit alsa_1.sh
```

A text editor will open.  Copy in all the stuff from the first "#!/bin/sh" through "#end of alsa_1."  Save, and close the text editor.

Then type  ```
gedit alsa_2.sh
```

...and do the same for that second block of code.

Then do ```
chmod a+x alsa_1.sh
```

and ```
chmod a+x alsa_2.sh
```

Then follow his instructions.

---

### Post by p-real on 2007-12-17
p-real@reality-p:~$ lpsci | grep -i audio
bash: lpsci: command not found
p-real@reality-p:~$ sudo lpsci | grep -i audio
[sudo] password for p-real:
sudo: lpsci: command not found
p-real@reality-p:~$ sudo apt-get lpsci | grep -i audio
E: Invalid operation lpsci
what am i doing wrong i must be retarded. i think i remember reading sumthing about realtek alc 861 in the manual i dono if thats a the actual soundcard or a driver or software or what it is does this mean anything to you. sorry im so slo at this im realy excited about linux and leaving windows behind as soon as i can figure out how to make everything work.

---

### Post by kpkeerthi on 2007-12-17
**lspci**

---

### Post by Dynaflow on 2007-12-17
S/He made a typo.  It's "lspci."

---

### Post by p-real on 2007-12-17
ok hold on im gonna try the last thing u said that sounds like the stuff

---

### Post by p-real on 2007-12-17
ok my sound car is ta da........ 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud                                                                                                   io Controller (rev 02)

---

### Post by Dynaflow on 2007-12-17
Intel HDA; I thought so.  Same as mine in my cheapo Compaq.  Antony Williams's blog post should be the ticket for you, then.  You're going to need the latest version of ALSA, and that's the easiest way I've seen yet to get it set up and running.  

Keep the thing bookmarked, though.  This will probably something you'll need to do again if you run Ubuntu under a new kernel in the future.

[EDIT:] There's a page in the community-submitted documentation dedicated to these things here: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by paydaydaddy on 2007-12-17
Take a look at this. It helped me when I was having sound problems.
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

---

