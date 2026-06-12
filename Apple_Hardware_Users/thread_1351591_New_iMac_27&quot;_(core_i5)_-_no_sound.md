---
title: "New iMac 27&quot; (core i5) - no sound"
date: 2009-12-10
forum: Apple Hardware Users
---

### Post by sean.clarke on 2009-12-10
Hi,
    I have one of the new core i5 iMacs and after installing Ubuntu 9.10 it looks like the sound is not working (neither is the web cam, but I can live without that).

I have tried both 32 and 64 bit versions just in case, but what seems odd is the system appears to detect the sound hardware and it is presented as expected (volume controls, output and input devices etc.) however nothing is heard from the speakers (or headphone socket for that matter).

Has anyone experimented with one of these?

Many thanks
Sean

---

### Post by kpholmes on 2009-12-10
you could try the alpha 1 release of 10.04, or try upgrading the kernel. 

keep us here updated on your progress

best of luck,
kevin

---

### Post by linuxopjemac on 2009-12-11
did you unmute all channels with alsamixer ? Use the m key to unmute.
```
alsamixer
```

---

### Post by sean.clarke on 2009-12-11
Hi, thnaks for the replies.

Yes, all channels are unmuted.

I'd rather not upgrade to 10.4, this is my development system so whilst sound is nice, stability is more important.

Odd, as the whole system "looks" like it should work - audio "plays" in various media players etc., just nothing is audible. I have even disabled the digital card (HDMI audio) in case the system was confused or something internal was blocking.

---

### Post by kpholmes on 2009-12-11
i dont know what your doing on linux or what kind of resources you need, but if its not to heavy then you could just virtualize linux. ubuntu doesnt run as smooth as i would like on my macbook so i just run it in virtual box, install the guest additions, and everything is supported and works for me. 

other then that have you added the ubuntu mac ppa in your respitory list?

---

### Post by linuxopjemac on 2009-12-12
what kernel are you running? I heard some positive news concerning sound with kernel 2.6.32. You could compile your own kernel if you are still on 2.6.31.
```
uname -r
```

---

### Post by Snorkr on 2009-12-17
Any news on this?

I'm having the same problem. It would be nice to have sound working on this awesome machine.

Best regs.,
-Snorkr

---

### Post by Z4rd0z on 2009-12-18
Hi all!

Sound is probably already working (as you suspected, Sean), but only via the earphone jack. The same problem occured with the 24" imac, the solution there was:

> open /etc/modprobe.d/options :
sudo nano /etc/modprobe.d/options
and add "options snd-hda-intel model=imac24" to the file and save ( ctrl+o and ctrl+x to exit )Unfortunately, that doesn't seem to be working now. I also tried to use "model=mbp3" with no success which was reported to help in some cases. We'll probably have to wait for the "model=imac27" to be introduced. I really hope someone will take care of that.

EDit: I just read that you already tried the headphone socket. At first, that didn't work for me as well. Manually installing the latest ALSA drivers helped.

Edit2: My kernel version is 2.6.32-7.

---

### Post by liberalist on 2009-12-20
Hi all! 

I have the previous model (Spring 2009) 20" iMac and I don't have sound as well. There is no sound through the headphone jacks and the inbuilt speakers. 

Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)

It's such a pity, because everything else seems to be working. Should I try Z4rd0z's command and use model=imac20? I hope it does not require a restart, as I want everything to work in the Live environment before taking the plunge to install it. As you might have guessed, I am far from being an expert, but have used Kubuntu quite extensively.

Thank you very much in advance.

---

### Post by Z4rd0z on 2009-12-21
There is no "imac20", try "imac24" or "mbp3". You will have to restart your sound system; I have no idea how that works, but you'll certainly be able to find help on google.

Helpful page how to get ubuntu running on an imac:
[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

---

### Post by liberalist on 2009-12-21
Hi, thank you for your reply. Sadly, it did not work. I used the command ```
/etc/init.d/alsa-utils restart
``` to restart the sound system (as described elsewhere on the net). Also, I tried ```
killall pulseaudio
```

It was strange that the file /etc/modprobe.d/options was not present in the Live environment. I guess I'll just have to be patient and wait for 10.04 to arrive. I should have known better to run Linux on an Apple. Unfortunately, it works really slow in Virtualbox (probably not enough RAM, 2 GB for 2 OSes).

---

### Post by Z4rd0z on 2009-12-25
As of December 22th, there should be a patch in the ALSA driver that enables sound for the 27" imac. I haven't been able to try it out so far, but once I have I will report if it works.

---

### Post by Z4rd0z on 2010-01-01
I have tried it and everything works now! Thanks to the dev(s) who fixed it!

---

### Post by alakazam on 2010-01-03
Thanks for workaround.

---

### Post by sean.clarke on 2010-01-09
Hi,
    I have installed the alsa modules backports and now i have sound through the headphone socket, however I still can't get sound out of the speakers, any ideas?

I have added the model=imac27 to the alsa-base.conf:

options snd-hda-intel power_save=10 power_save_controller=N model=imac27

---

### Post by linuxopjemac on 2010-01-09
try to unmute channels with alsamixer....

---

### Post by sean.clarke on 2010-01-09
Hi,
    Fired up alsamixer and made sure all channels were unmuted (as well as setting surround and front speaker volume), but still no joy.

---

### Post by heykenen on 2010-01-09
I've same problem, channels are unmuted, headphones is ok.

---

### Post by linuxopjemac on 2010-01-10
ask Z4rd0z what he did, it worked for him apparently.
>  I have tried it and everything works now! Thanks to the dev(s) who fixed it! 

---

### Post by Z4rd0z on 2010-01-12
I removed all old sound devices; then I compiled the most recent alsa drivers, added model=imac27 to alsa-base.conf and since then everything has been working perfectly... so maybe you'll want to try removing all audio devices. Or you could just change the device order: in the multimedia settings I have "HDA Intel (Cirrus Analog)" on top of the list. Good luck.

---

### Post by Kaos2K on 2010-02-04
> **Z4rd0z said:**
> I removed all old sound devices; then I compiled the most recent alsa drivers, added model=imac27 to alsa-base.conf and since then everything has been working perfectly... so maybe you'll want to try removing all audio devices. Or you could just change the device order: in the multimedia settings I have "HDA Intel (Cirrus Analog)" on top of the list. Good luck.

Hi. Could you explain how to do that? Thank you :)

---

### Post by Q007 on 2010-02-19
I've had success with getting sound to work on my 27 inch imac!

1. I installed the backport modules.

2. I opened up my /etc/modprobe.d/alsa-base.conf file and changed the line:

```
options snd-hda-intel power_save=10 power_save_controller=N
``` to include model=mbp55:

```
options snd-hda-intel power_save=10 power_save_controller=N model=mbp55
```I got the idea to try mbp55 from this post that reportedly fixes the sound problem with a kernel patch: [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=1a5ba2e9fc7999b8de2a71c7e7b9f58d752c05e4](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=1a5ba2e9fc7999b8de2a71c7e7b9f58d752c05e4)

3. I went into alsamixer (just type alsamixer into the console) and unmuted the channels. When in alsamixer, use the left and right keys to change highligted channel, up/down keys to change volume level and 'M' to unmute. If it has a MM at the bottom, you need to unmute it.


This worked for me. I was curious as to why other model=XXXX options had not worked for me, so I went back and tried model=imac27, model=imac24, model=mbp3. These variants have been suggested at places around the web. None of these seemed to work for me. I also noticed that when I made a change to the /etc/modprobe.d/alsa-base.conf file, it seemed to remute my channels. I went into alsamixer and they were muted. I had to unmute the channels again... I dont know why.

I'm pretty sure all three steps are needed. Good luck to you getting it to work. If this does or doesn't work for you, please post back here.

Q

---

### Post by Kaos2K on 2010-02-19
> **Q007 said:**
> I've had success with getting sound to work on my 27 inch imac!

1. I installed the backport modules.

2. I opened up my /etc/modprobe.d/alsa-base.conf file and changed the line:

```
options snd-hda-intel power_save=10 power_save_controller=N
``` to include model=mbp55:

```
options snd-hda-intel power_save=10 power_save_controller=N model=mbp55
```I got the idea to try mbp55 from this post that reportedly fixes the sound problem with a kernel patch: [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=1a5ba2e9fc7999b8de2a71c7e7b9f58d752c05e4](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=1a5ba2e9fc7999b8de2a71c7e7b9f58d752c05e4)

3. I went into alsamixer (just type alsamixer into the console) and unmuted the channels. When in alsamixer, use the left and right keys to change highligted channel, up/down keys to change volume level and 'M' to unmute. If it has a MM at the bottom, you need to unmute it.


This worked for me. I was curious as to why other model=XXXX options had not worked for me, so I went back and tried model=imac27, model=imac24, model=mbp3. These variants have been suggested at places around the web. None of these seemed to work for me. I also noticed that when I made a change to the /etc/modprobe.d/alsa-base.conf file, it seemed to remute my channels. I went into alsamixer and they were muted. I had to unmute the channels again... I dont know why.

I'm pretty sure all three steps are needed. Good luck to you getting it to work. If this does or doesn't work for you, please post back here.

Q

WoW!!!! worked!!! After edit the .conf file i had to reboot (in the reboot the graphics were messed up and had to reboot again) once i entered ubuntu i lanched alsamixer, unmutted the channels and... voilá! sound working!!!

Thank you very much!!!

---

### Post by linuxopjemac on 2010-02-19
Good news for all the iMac 27" users. The solution also found a new place on my own website. :)
[http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=64&p=84#p84](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=64&p=84#p84)

---

### Post by Q007 on 2010-02-20
Along with getting sound to work, I've been trying to get scolling to work on the magic mouse. That's discussed in this thread: [http://ubuntuforums.org/showthread.php?t=1386790](http://ubuntuforums.org/showthread.php?t=1386790)

So I've upgraded kernels using the 2.6.31-20-magicmouse image kindly provided by the guys on that thread. I can get into Ubuntu ok, but scrolling doesn't work for me yet. However there is another nagging problem which is why I'm posting in this thread, not that one; sound went out the window when I upgraded from 2.6.31-19 to 2.6.31-20-magicmouse.

I thought this might be due to the version of alsa backports module I had installed. It was the 2.6.31-19 version.

I went into the Administration->Update Manager, and under Settings, selected Pre-released updates and Unsupported updates, then checked for updates. There were lots, including an alsa backports module for 2.6.31-20. I thought this might do the trick, so I updated the lot. (It turned out there was a 2.6.31-20-generic kernel image as well.)

Ok, so now I had my old 2.6.31-19-generic, the magic mouse kernel 2.6.31-20-magicmouse and the updated 2.6.31-20-generic kernels to choose from.

I went back and did some tests for sound on the different kernels.

I found that the /etc/modprobe.d/alsa-base.conf line was important. I modified the ```
options snd-hda-intel power_save=10 power_save_controller=N
``` line and added different model options such as 
```
options snd-hda-intel power_save=10 power_save_controller=N model=mbp55
```

model settings I tried: 

model=mbp3
model=mbp55
model=imac27
model=imac24
none (ie, the same as the first code bracket in this post)

Kernel 2.6.31-19-generic
model=mbp55 was the only model setting that worked for me properly under kernel 2.6.31-19. All the rest worked with headphones only.

Kernel 2.6.31-20-generic
model=mbp55 was the only setting that didn't work. All the others were completely fine (speakers and headphones both ok).

Kernel 2.6.31-20-magicmouse
none of the settings worked at all. No speakers. No headphones.


What is going on here?

To start with I need to clarify my earlier post about how to fix sound. It seems like it depends on which kernel you have installed. And it might be simplest to upgrade to the 2.6.31-20-generic kernel. If you've already added the model=mbp55 option, you'll need to remove it again for the 20-generic kernel to work with sound.

I did a diff on the config files for the generic and magicmouse kernels and found nothing that would indicate the problem. (Date, name and magicmouse module line were the only differences.)

So why would the two kernels behave so differently when it comes to sound?? I'm really puzzled by this.

Q

---

### Post by linuxopjemac on 2010-02-20
I also don't understand that either, to be honest. The kernel was compiled on a 32-bits system, although not on a Mac. Maybe Marco can help us here.

---

### Post by Q007 on 2010-02-20
I've done some more digging.

I've confirmed that the chip on my 27 inch imac is the Cirrus Logic CS4206.

According to [http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt)

the appropriate model is mbp55. That worked in the 2.6.31-19 kernel.

In the 2.6.31-20 kernel, the model=mbp55 (and the model=auto) setting stuffed it up. Alsamixer wouldn't even start as it says something like 'no mixer elements found'. This kernel would only work if we had no model option, or if we put in ones that look as if they are for the wrong chip as per the link above. This seems really odd - why does it *not work* when we put in the correct model setting and *work correctly* when we put in what seem to be wrong settings? I'll just shrug for now and continue with something else:

The following will tell you what codec chips you have on your machine:

cat /proc/asound/card*/codec* | grep Codec

Hopefully you can match the results of this to a section in the link above and get the model setting for you... 

In both the generic kernels, (2.6.31-19/20) I'm shown 

Codec: Cirrus Logic CS4206
Codec: ATI R6xx HDMI

However, when using the magicmouse kernel I get:

Codec: Generic 1013 ID 4206
Codec: ATI R6xx HDMI

I suspect this is the main problem. The kernel doesn't seem to be identifying the chip properly in this kernel. I'm getting well out of my depth here - I really have very little idea how the kernel or proc work. But I think that might be the problem. 

Could this underlying problem also be what is preventing scrolling from working too?

Q

---

### Post by tmette on 2010-05-05
It doesn't seem like editing the "/etc/modprobe.d/alsa-base.conf" works for me becuase it doesn't even have this line listed:
```

options snd-hda-intel power_save=10 power_save_controller=N
```

I even did a "Where is" (Ctrl+W) for "options snd-hda" and it doesn't come up with anything.  I also tried adding the line:

```
options snd-hda-intel power_save=10 power_save_controller=N model=mbp55
```

But this doesn't even seem to work, although I'm not sure where to add it.  My alsamixer is unmuted and I can get perfect sound through my headphones.  Any other ideas from you guys?

---

### Post by Kaos2K on 2010-05-06
You have to install the alsa-backport modules first.

---

### Post by tmette on 2010-05-06
> **Kaos2K said:**
> You have to install the alsa-backport modules first.

I already tried this..or at least I thought I did.  Can someone be kind enough to walk me through this entire process completely?  I'm really having some trouble here.  I'm completely new at this. :)

---

