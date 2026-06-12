---
title: "Er, am I stupid, or is there something really wrong?"
date: 2008-06-13
forum: Apple Hardware Users
---

### Post by `Yummy on 2008-06-13
I'm on an iMac 20" Intel Core Duo - 2.0 GHZ. I have successfully triple booted my computer with xp, leopard (mac 10.5), and ubuntu. It all works fine - this is being posted from firefox on linux right now. I'm very new to this, and really just wanted to install linux because I can, why not, eh?

But... I was trying to do this:

options snd-hda-intel model=ref (in /etc/modprobe.d/alsa-base)

to fix my microphone.

I open the file in gedit, paste the code, and it tells me I don't have sufficient permissions. I go to the /etc folder, and I don't have permissions to any of this either (owner is root, not me).

I'm sure this is just a really nooby problem, but I would really appreciate any help.

Thanks in advance

--Yummy

---

### Post by llama320 on 2008-06-13
don't worry about it, we all got to start somewhere

You do in fact need root privileges to access /etc/modprobe.d/alsa-base

what you want to do is go into a terminal (Applications > Accessories > Terminal) and type

```
 sudo gedit /etc/modprobe.d/alsa-base 
```

then just type your password..and now you have privileges
Just be careful with root, it's very powerful, and you might want to make a backup, as a habit, for any file you're going to edit as root. To do this just type

```
 sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.backup 
```

Good Luck and enjoy linux

---

### Post by abhiroopb on 2008-06-13
In Ubuntu if you are editing files outside of the "/home" folder you need to type in "sudo" before a command and supply the root password.

Also please use more descriptive titles next time, easier to identify what your problem is, so people who know the issue can help!

---

### Post by abhiroopb on 2008-06-13
Just say the new post and re-read your post.

Since you want to use gedit to edit the file instead of sudo I suggest using: "gksudo gedit /etc/modprobe.d/alsa-base"

Explanation as to the difference between sudo and gksudo: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by `Yummy on 2008-06-13
Thanks you very much!

[quote="abhiroopb"]Also please use more descriptive titles next time, easier to identify what your problem is, so people who know the issue can help![/quote]

Yes, my apologies. Will be done in the future!

---

### Post by `Yummy on 2008-06-13
Alright, another question... my microphone is still not working. I've dug up some stuff: (original post:  [http://ubuntuforums.org/showthread.php?p=1357412#post1357412](http://ubuntuforums.org/showthread.php?p=1357412#post1357412) )

> **capriccio said:**
> Just fixed this on my machine - but I believe that the fix will work for anyone with this particular mic/input problem that has the SigmaTel STAC9200, 922x or 927x chipset for Intel HDA.  Ok, here's what you do:

1. backup your existing /etc/modprobe.d/alsa-base
2. append the following to the end of the file:

options snd-hda-intel model=ref

Done.
Now reload your modules or reboot.  Go into alsamixer.  If everything went as expected, you should see some new options, eg - 'front mic' as an input source and IEC958 (S/PDIF) settings.  

I'm supposed to be getting extra options when I run 'alsamixer,' but no such extra options appear.

Is there any possible reason for this?

Once again, thanks in advance.

---

### Post by cyberdork33 on 2008-06-13
You have an aluminum iMac or a white one?

I don't think you have to make any file modifications to get the mic working. run alsamixer and hit [TAB] until the input AND output channels are shown. You will need to unmute and increase the level of the mic channel and a capture channel.

---

### Post by `Yummy on 2008-06-13
> **cyberdork33 said:**
> You have an aluminum iMac or a white one?

I don't think you have to make any file modifications to get the mic working. run alsamixer and hit [TAB] until the input AND output channels are shown. You will need to unmute and increase the level of the mic channel and a capture channel.

I have a white iMac. I don't have a microphone channel when I press tab. Here's a list:

_Playback:_
Master
PCM
Front
Surrond
Center
LFE
Side
IEC958

_Capture:_
IEC958 Capture
Capture
Capture 1
Digital
Input Source
Input Source
Mux
Mux 1
Swap Center/LFE

I turned all tracks on that can be turned on to their max volume.

---

### Post by cyberdork33 on 2008-06-13
I am willing to bet that one of those "input source" channels is the mic. 

Also, you can turn up all the channels, but you still have to unmute them! (m key)

---

### Post by `Yummy on 2008-06-13
> **cyberdork33 said:**
> I am willing to bet that one of those "input source" channels is the mic. 

Hmm... If I open the volume preferences (by double clicking the volume icon), then I go to the "Options" tab, and I see Input Source: Line. I click "Line," and that's my only option.

> **cyberdork33 said:**
> Also, you can turn up all the channels, but you still have to unmute them! (m key)

Yeah, by going to volume options (as I did above), I can see that they're all unmuted.

EDIT: After going to Preferences>Sound, going to Sound Capture>Test, all I hear is some loud static. I try yelling into my mic, tapping it, and still... static. :(

---

### Post by cyberdork33 on 2008-06-13
> **`Yummy said:**
> Hmm... If I open the volume preferences (by double clicking the volume icon), then I go to the "Options" tab, and I see Input Source: Line. I click "Line," and that's my only option.



Yeah, by going to volume options (as I did above), I can see that they're all unmuted.

EDIT: After going to Preferences>Sound, going to Sound Capture>Test, all I hear is some loud static. I try yelling into my mic, tapping it, and still... static. :(

Don't rely on that tool. use alsamixer.

I have the same iMac as you, and it works fine. there is no special configuration needed.

---

### Post by `Yummy on 2008-06-13
Alright, I am using alsamixer. Everything is up to 100%, besides the master (which is up to like 70%).

I am using Teamspeak - and I noticed that when I was fooling around before, I set the Sound Driver option to "other:" /dev/audio rather than the default, which is /dev/dsp (oss). It definitely shouldn't be OSS - as TeamSpeak claims /dev/dsp is - so what should I use (rather than the /dev/dsp) to get alsa instead of OSS?

Thanks for any help on this, it is much appreciated.

---

### Post by cyberdork33 on 2008-06-14
> **`Yummy said:**
> Alright, I am using alsamixer. Everything is up to 100%, besides the master (which is up to like 70%).

I am using Teamspeak - and I noticed that when I was fooling around before, I set the Sound Driver option to "other:" /dev/audio rather than the default, which is /dev/dsp (oss). It definitely shouldn't be OSS - as TeamSpeak claims /dev/dsp is - so what should I use (rather than the /dev/dsp) to get alsa instead of OSS?

Thanks for any help on this, it is much appreciated.
If OSS works then use it. ALSA is backwards compatible with OSS, so you are really using ALSA.

---

### Post by `Yummy on 2008-06-14
YES! I got it to work! I don't know how... well pretty much when I booted up I got this white screen, so I decided to just do a clean boot - I hadn't installed much of anything. I installed, fiddled with some preferences, and what do ya know, it works! Thanks for all the help, it is appreciated.

---

