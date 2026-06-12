---
title: "Sound Problem (only right channel)"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by tnsy on 2007-04-22
Hi

i've just installed ubuntu Edgy Eft and i have problem, like in title i get sound only in right channel, ive installed some codecs from easyubuntu, beryl, and thats it, i've read about alsa, looked thru synaptix, which shows that at least basic components are installed, but i also downloaded source (alsa), and installed it but its still like it was.

My computer is Acer Aspire 5101 WLMi

and in system preferences my sound card is: HDA ATI SB but actually its some kind of realtek 883 ?

any1 has any suggestions, please help

thanks

---

### Post by nudnik on 2007-04-22
> **tnsy said:**
> Hi

i've just installed ubuntu Edgy Eft and i have problem, like in title i get sound only in right channel, ive installed some codecs from easyubuntu, beryl, and thats it, i've read about alsa, looked thru synaptix, which shows that at least basic components are installed, but i also downloaded source (alsa), and installed it but its still like it was.

My computer is Acer Aspire 5101 WLMi

and in system preferences my sound card is: HDA ATI SB but actually its some kind of realtek 883 ?

any1 has any suggestions, please help

thanks

Is the same fault apparent with Windows? If so, you may need new speakers, a new motherboard, or sound card, if the audio isn't integrated. 

You should install "alsamixergui" from the repositories (sudo apt-get install alsamixergui). Once installed, attempt to manipulate the channels and see what happens.

---

### Post by tnsy on 2007-04-22
in windows everything is allright

i did like u said and installed alsamixer, but when i choose it from applications it returns:

alsamixer: function snd_mixer_load failed: invalid argument

confused ??

---

