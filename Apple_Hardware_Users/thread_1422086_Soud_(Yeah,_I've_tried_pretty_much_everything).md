---
title: "Soud (Yeah, I've tried pretty much everything)"
date: 2010-03-05
forum: Apple Hardware Users
---

### Post by mandrewmartin on 2010-03-05
I have a Macbook model A1181 with an Intel audio card with a Stigmatel STAC9221 driver. I dual boot Windows as well. The sound card works perfectly fine in Windows, but will not work in Ubuntu at all. I'm really tired of dealing with this problem and am frankly surprised that so many people seem to be having trouble with this and there is seemingly not a fix. The audio worked fine when I had Mac OS installed; it currently works fine with Windows XP. It used to work in ubuntu until I dual-installed Windows XP. I like the idea of having open-source software and sticking it to the big computer companies but in order for it to be feasible I'm going to need full functionality. I'm new to this OS and I really don't know the programming language very well so I need this broken down simply if possible. Thanks in advance.

I've tried the solution offered on this page: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) 
No success

I've tried the solution offered on this page: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
No success

---

### Post by linuxopjemac on 2010-03-05
It may be necessary to configure ALSA to pick the right module for the sound chip:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Edit the options realated to the hda_intel chip. Add to the options line model and position_fix parameters.

```
options snd-hda-intel model=intel-mac-auto position_fix=1
```

and add these two lines:

```
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
```
see here
[https://help.ubuntu.com/community/MacBook1-1/Karmic?action=fullsearch&context=180&value=linkto%3A%22MacBook1-1/Karmic%22#Sound](https://help.ubuntu.com/community/MacBook1-1/Karmic?action=fullsearch&context=180&value=linkto%3A%22MacBook1-1/Karmic%22#Sound)

---

### Post by Dayofswords on 2010-03-05
> **mandrewmartin said:**
> I have a Macbook...
well there's ya problem



ok i'm not helpful

---

### Post by mandrewmartin on 2010-03-05
> **linuxopjemac said:**
> should work out of the box with KArmic Koala, ...unmute all channels with alsamixer (with "m")
```
alsamixer
```see here
[https://help.ubuntu.com/community/MacBook1-1/Karmic?action=fullsearch&context=180&value=linkto%3A%22MacBook1-1/Karmic%22#Sound](https://help.ubuntu.com/community/MacBook1-1/Karmic?action=fullsearch&context=180&value=linkto%3A%22MacBook1-1/Karmic%22#Sound)


I tried running alsamixer and editing the file in the thread and neither resolved my issue.

---

### Post by linuxopjemac on 2010-03-05
ok, weird...Did you try with different kernels ?

---

### Post by mandrewmartin on 2010-03-07
> **linuxopjemac said:**
> ok, weird...Did you try with different kernels ?

Not sure what you mean by that. Could you elaborate?

---

### Post by hollowtd on 2010-03-07
Tell you how I fixed mine. I have the A1181 white model macbook. I use ubuntu 9.10. What I had to do (especially to get the jack (speakers) to work is go to the Ubuntu software center. Get the Alsa mixer from there (download it). Then, mess with the functions and untick mute (It might have MM by it). That fixed mine. Hope that helps.

---

### Post by linuxopjemac on 2010-03-08
there are different kernel versions in the repository (synaptic package manager). You could try different 2.6.31 kernels.

---

