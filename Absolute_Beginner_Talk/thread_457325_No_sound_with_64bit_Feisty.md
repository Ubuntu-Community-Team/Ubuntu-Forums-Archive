---
title: "No sound with 64bit Feisty"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Horace Big Cigar on 2007-05-28
Chaps,
I'm an Ubuntu newbie.
I have a Toshiba Satellite P100-152.  It has a core 2 duo chip (1.6Ghz) with 1Gb of RAM.  I'm running 64bit Ubuntu (Feisty) and I can't get the sound to work (no sound at all).  Can anybody help me?
It works ok under Vista.
Thanks in advance for your response.

---

### Post by deadgobby on 2007-05-28
There is a bug in the ATI Technologies Inc SB450 HDA or just SB450 HDA. It is
with Fiesty. Edgy the sound work fine then after the upgrade. Opps no sound with
people this type of set up. So there is couple of thing you can do.

[http://tinyurl.com/2jjmu6](http://tinyurl.com/2jjmu6)


[https://answers.launchpad.net/ubuntu/+question/6499](https://answers.launchpad.net/ubuntu/+question/6499)
or
1. edit alsa-base:
sudo gedit /etc/modprobe.d/alsa-base
2. add this line to the end of that file:
options snd-hda-intel model=3stack
3. save y close the file
4. restart
Or
[http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

---

### Post by Horace Big Cigar on 2007-05-31
Many thanks for your timely response.  I've tried all of your suggestions, but to no avail.  Is there anything else I can try?

---

### Post by deadgobby on 2007-06-02
Yes, install Ubie 32 bit. 64 bit van be buggy and there is more support at this time for 32 bit than 64 bit. Hopefully next year the 64 bit will be king. Crips even MS has a buggy 64 bit windows too.
Gobby

---

### Post by volkswagner on 2007-06-04
check out this thread

[http://ubuntuforums.org/showthread.php?p=2710147]("http://ubuntuforums.org/showthread.php?p=2710147")

worked on my HDA sb450 after adding options restart

I am using 32bit

---

