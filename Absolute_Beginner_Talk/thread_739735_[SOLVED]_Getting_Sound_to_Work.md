---
title: "[SOLVED] Getting Sound to Work"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by azurepancake on 2008-03-30
I've just installed Ubuntu Gutsy onto my desktop computer and everything is operating wonderfully. There is one remaining issue though and that is my sound. There is no sound what so ever. I have yet to find any program that will output sound successfully. 

I am indeed new to Linux and I am a bit baffled at where to start troubleshooting my problem. My system uses the Creative Audigy 2 ZS sound card. I am able to access the alsamixer program from terminal and all important levels appear to be up around 75%.

If there is anymore information that will help solve this problem, please ask and I'll get it for you. I'll greatly appreciate any help. Thanks!

---

### Post by paydaydaddy on 2008-03-30
Take a look at this guide. I found it useful when I was having sound problems.

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

---

### Post by azurepancake on 2008-03-30
Seems very detailed yet straight forward. Thanks man, I'll let you know how it goes.

If anyone has anything else to add, please don't hold back!

---

### Post by azurepancake on 2008-03-30
I've started the guide and ran the aplay -l command. Immediately I was given an extensive list of sound card information with no noticeable errors. According to the guide, I should check the aslamixer for muted levels, but everything appears to be setup correctly.

Should I continue with the guide or perhaps skip to a certain part? I'm just trying to be as cautious as possible. Let me know if you need anymore information. Thanks again.

---

### Post by paydaydaddy on 2008-03-30
Have you determined the correct linux driver for your sound card and made sure that it is installed?

---

### Post by taavikko on 2008-03-30
Almost every creatives soundcard should be supported, except X-fi.
what does ```
lsmod |grep snd
``` return?

Also you can change the default soundcard via command line,
```
asoundconf list
```
shows the available soundcards
```
asoundconf set-default-card XXX
```
where XXX is the desired card

Don't be alarmed if the names of the cards are confusing ;)

---

### Post by azurepancake on 2008-03-30
Okay, this is odd to me. Last night while trying to get my sound to function, I had reboot my computer. During POST I came to an error when Grub was being loaded. I couldn't get to either my Windows or Ubuntu partitions to load either OS, so I ran a fixmbr and fixboot from the Repair Console, loaded Windows and I am in the process of reinstalling Ubuntu right now.

The odd thing is that my sound appears to be working. I was quite pleased when I heard the Ubuntu introduction music play through my speakers. This did not happen last install.

I wonder why it is working now.. any ways, we will see how it functions when Ubuntu is installed and running. I'll let you all know. Thanks!

---

### Post by Samurai Penguin on 2008-03-30
I don't know if you have on-board sound or a PCI card but maybe this will do the trick. This is for an Audigy1 PCI soundcard:

Setting up Sound:

Volume Control > File > Change Device > select Audigy 1 [SB0090] (Alsa mixing)

Volume Control > Switches Tab > uncheck Audigy Analog/Digital Output Jack
SOUND

---

### Post by azurepancake on 2008-03-31
Hopefully this will be my last update to this post, because everything is working just fine now.

After the install it booted into Ubuntu and the sound stopped working. I was quite disappointed, but I decided to fiddle around some more and followed Taavikko's steps. It turns out I simply had to find the name of my card using lsmod |grep snd and enter it in using asoundconf set-default-card. Everything is working perfect now and believe it or not the sound quality appears to be better then it is in Windows!

I've rebooted a couple times since I got it working and I still have my sound. I hope it stays around for good. Thanks so much for the help!

---

