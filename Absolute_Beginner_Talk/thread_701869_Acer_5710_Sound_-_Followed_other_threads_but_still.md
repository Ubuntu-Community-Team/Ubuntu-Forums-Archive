---
title: "Acer 5710 Sound - Followed other threads but still no sound - please help"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by ianpallen on 2008-02-19
I have an Acer 5710 which was unfortunatly pre-installed with vista anyway after much angerl I decided to go with ubuntu and for the most part everything seems to be working great except for the sound.. I've followed the advice from other threads which seem to point to the following

$ sudo apt-get install linux-backports-modules-generic

$ sudo gedit / etc / modprobe.d / alsa-base

then password

now gedit opens and I get a stop sign with "/ is a directory" i'm thinking that due to this it wont accept the saving of the next part you add which is

Options snd-hda-intel model = ace

I'm a total noob at this so any help would be greatly appreciated.

Thanks

---

### Post by InsertNameHere on 2008-02-19
This trick works for Intel HDA cards, it worked for me hope it helps.

[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

Don't take my word for it, although it says toshiba, it's a fix for Intel HDA cards.

---

### Post by ianpallen on 2008-02-19
Thanks for the quick reply but still nothing.

---

### Post by InsertNameHere on 2008-02-19
DId you try the troubleshooting procedures here?

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by ianpallen on 2008-02-19
Wow thats alot to go through I will let you know.

Thanks

---

### Post by ianpallen on 2008-02-19
Well after my eyes crossed a few times whilst reading the troubleshooter I decided to do another quick google based on the onboard sound I have (Realtek ALC268) and found the following method works

sudo apt-get install linux-backports-modules-generic

sudo gedit /etc/modprobe.d/alsa-base

options snd-hda-intel model=acer

[http://elubuntero.wordpress.com/2008/02/09/gutsy-the-sound-of-silence-2/]("http://elubuntero.wordpress.com/2008/02/09/gutsy-the-sound-of-silence-2/")

I don't know if it was a what I did when I followed the troubleshooter or whether the new thing I found did the trick but the sounds now working woohoo!!!!

:guitar:

Thanks very much for your help :)

---

