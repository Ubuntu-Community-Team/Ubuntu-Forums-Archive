---
title: "trying to get wireless card to work"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by jasong on 2007-04-29
I'm attempting to get my wireless card to work on my newly-transformed-to-a-Linux-box Dell laptop, since I'm sick of Microsoft.  Unfortunately, it refuses to recognize the wireless card.  I got to, and was stumped, by step 3.1.2 [here.](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)  The file opened up, but I have no idea where to find the information I'm supposed to enter.

If need be, I can find the details of my Dell laptop, but I'm hoping that, instead, someone can give me a command, or commands, that will get me what I need.  Since I'm not sure what I need, this is the preferred method.

---

### Post by oilchangeguy on 2007-04-29
what version of ubuntu are you using?

---

### Post by Immolatus on 2007-04-29
What brand is the wireless card?

---

### Post by jasong on 2007-04-29
I just talked to a friend online, he said that I need a kernel that supports pcmcia(hope I typed that right).

Could someone point me in the right direction for that, or maybe tell me he's dead wrong?

---

### Post by aroch1 on 2007-04-29
These are the steps that I took to get wireless working on my Dell laptop.

(1) Go to Dell.com, enter your laptop's code and download the windows wireless drivers (.exe)
(2) Follow the instructions here: [http://ubuntuforums.org/showthread.php?t=297092&highlight=03%3A00.0+Network+controller%3A+Broadcom+Corporation+Dell+Wireless+1390+WLAN+Mini-PCI+Card+%28rev+01%29](http://ubuntuforums.org/showthread.php?t=297092&highlight=03%3A00.0+Network+controller%3A+Broadcom+Corporation+Dell+Wireless+1390+WLAN+Mini-PCI+Card+%28rev+01%29)
(I used Automatix2 to install ndiswrapper...in this post they describe how to build if from the source...either way works.  If you used Automatix, just pick up this post after the part about installing ndiswrapper)

---

### Post by Immolatus on 2007-04-29
We need to know what distribution your running. I'm running feisty fawn, and just checked the synaptic (system>administration>synaptic package manager) and found support for pcmcia all ready installed and some other info in the descriptions there. apparently pcmcia support is mostly included since kernel 2.6.x.

---

### Post by jasong on 2007-04-29
Well, I'm deep into the instructions that were advised a couple posts back, but I can start over, including reinstalling Linux, if it's deemed necessary.

At the moment I'm on the second code section of Step 4:install drivers.

sudo ndiswrapper -i bcmwl5.inf

gets me 

```
installing bcml5 ...
Couldn't open bcml5.inf:  NO such file or directory at /usr/sbin/ndiswrapper line 174
```
Btw, I'm not in the directory listed, especially since it doesn't seem to exist. 

Awaiting instructions.  Feisty Fawn, btw, is my version.

---

### Post by Immolatus on 2007-04-30
Try going to the location /usr/sbin and see if the files exist there. If they do, were they extracted or just moved in tar or zip form?
You can also extract to the home folder and copy them to /usr/sbin using cp:

Do:

sudo cp /home/youloginname/the extracted foldername* /usr/sbin

don't forget the asterisk and the placement is case sensitive. I like to do it this way for my wireless firmware because if I type it wrong, the file is still just in /home and I know where to find it.

---

