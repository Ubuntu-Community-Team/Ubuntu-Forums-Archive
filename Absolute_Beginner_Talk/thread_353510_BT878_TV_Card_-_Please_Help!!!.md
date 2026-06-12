---
title: "BT878 TV Card - Please Help!!!"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Contrid on 2007-02-04
Hi there,

I have a PCI tv card with a BT878 tuner, but I have absolutely no idea how to make it work. I've read through several guides, but each one is different and none of them seem to work properly.

Can someone please help me to get my card working?
I will really appreciate it very much.

---

### Post by shareMenaPeace on 2007-02-04
Can you provide more infos, like manufacture model number?

And which guide you use - where do you get stuck - error messages?

---

### Post by Contrid on 2007-02-04
> **shareMenaPeace said:**
> Can you provide more infos, like manufacture model number?

And which guide you use - where do you get stuck - error messages?

Hi there,

Thank you very much for your resposne.

I used this guide : [http://www.ubuntuforums.org/archive/index.php/t-153935.html](http://www.ubuntuforums.org/archive/index.php/t-153935.html)

Problem is...the tvtime-scanner doesn't find anything. When I launch tvtime, it also just keeps on saying no signal.

I'm really not sure if I have all the right drivers an things. I'm really confused. :(

---

### Post by shareMenaPeace on 2007-02-04
What is the output of

```
lspci | grep Bt878
```

Did you successfull followed the guide step by step?

---

### Post by Contrid on 2007-02-04
> **shareMenaPeace said:**
> What is the output of

```
lspci | grep Bt878
```Did you successfull followed the guide step by step?

Hey there,

I got it working!!! Just had to reboot in order to load the new modules.
Problem is...there is no sound.
I'm using a Logitech USB headset. I don't have my speakers plugged in right now...so I haven't tried my soundcard.
Any ideas on the sound?

Thanks for all your help.

---

### Post by Contrid on 2007-02-04
Also...next time I run tvtime-scanner is there a quicker way to specify the frequency range in which to scan? I found my channels around 200Mhz...and I don't want it to scan through the entire table.

---

### Post by shareMenaPeace on 2007-02-04
Doubleclick the sound bar on top panel to check the volumemeter.

You can even run alsamixer from terminl to check aswell or use 

Applications -> Add/Remove -> Search for alsa and install the GUI.

IF this doesnt fix the sound issue start a new topic for this.

Cheers

---

### Post by shareMenaPeace on 2007-02-04
There should be a inbuild option to put mhz frequenzes.

---

### Post by Contrid on 2007-02-04
Thanks for all your help. I really appreciate it.
I'm going to look into the sound issue right now.

---

