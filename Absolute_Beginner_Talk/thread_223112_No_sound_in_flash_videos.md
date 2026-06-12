---
title: "No sound in flash videos?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by cremnob on 2006-07-25
Tried viewing videos at youtube and the video works fine but the sound doesn't. Other sounds work (tried playing a video file)

---

### Post by Sef on 2006-07-25
Alsa-oss needs to be downloaded.

Ubuntu: Applications > Accessories > Terminal

sudo apt-get update

sudo aptitude install alsa-oss

After that you should have flash sound.

---

### Post by cremnob on 2006-07-26
Did that still don't have sound :/

---

### Post by aysiu on 2006-07-26
> **cremnob said:**
> Did that still don't have sound :/
Did you restart Firefox afterwards?

---

### Post by cremnob on 2006-07-26
Yeah. Not sure whats wrong

---

### Post by Dr. Nick on 2006-07-30
Another possible fix

[http://ubuntuforums.org/showthread.php?t=204022](http://ubuntuforums.org/showthread.php?t=204022)

---

### Post by prophet11 on 2006-07-30
I think you cant have any other audio software while listening to flash videos//

---

### Post by Dr. Nick on 2006-07-30
> **prophet11 said:**
> I think you cant have any other audio software while listening to flash videos//

some cases that is true, esd is a older technology that causes some problems. I dont know much about it, but i know I used to always have to kill esd or close all other audio apps first

However now i can listen to music and flash at the same time, Just depends on your setup

---

### Post by tubo on 2006-07-30
search the board fro "alsa oss firefox" , theres a solution.

best
Emanuel

---

### Post by Huhn on 2006-08-06
ok, I just pick one of those thousands of threads concerning this topic.


I've got the same problem (you wouldn't have guessed)

all these solutions are just temporary remedies. when I reboot my system it's all back to normal.

so far I did:

-install the alsa-oss package
-reinstalled the flash plugin manually
-tried this > # Flash also looks for /usr/lib/libesd.so.1
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

# Flash expects /tmp/.esd/socket to exist.
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket
-typed it into the contrab so it will be run instantly at bootup
-tried aoss opera


one thing that might be a hint for the problem is the output I receive when I use aoss opera 
> 

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
opera: Activated running instance


I hope some of you can help me

---

### Post by richbarna on 2006-08-06
Some Adobe Shockwave Flash sites don't work if they use version 8,9 or 10 as linux only has Flash 7.
[http://www.adobe.com/shockwave/download/alternates/#fp](http://www.adobe.com/shockwave/download/alternates/#fp)

More here :-
[http://weblogs.macromedia.com/emmy/archives/2005/12/why_isnt_there.cfm](http://weblogs.macromedia.com/emmy/archives/2005/12/why_isnt_there.cfm)

And a Flash Trick workaround to make the sites think you have Flash 9
[http://ubuntuforums.org/showpost.php?p=1278350&postcount=2](http://ubuntuforums.org/showpost.php?p=1278350&postcount=2)

---

### Post by evergreen on 2006-08-06
This is what worked for me

sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP=”esd”

I changed it from FIREFOX_DSP="none" to FIREFOX_DSP=”aoss” that gave me sound but the timing was off. FIREFOX_DSP=”esd” seems to work nicely. For all video sites I try (youtube,google video, thatvideosite etc)

---

### Post by richbarna on 2006-08-06
> **evergreen said:**
> This is what worked for me

sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP=”esd”

I changed it from FIREFOX_DSP="none" to FIREFOX_DSP=”aoss” that gave me sound but the timing was off. FIREFOX_DSP=”esd” seems to work nicely. For all video sites I try (youtube,google video, thatvideosite etc)

That works, nice tweak :)
Incidently it's better if you use "gksudo" ;)

---

