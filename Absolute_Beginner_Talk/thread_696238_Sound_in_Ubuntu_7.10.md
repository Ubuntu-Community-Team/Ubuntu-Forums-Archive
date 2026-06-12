---
title: "Sound in Ubuntu 7.10"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by sfitch29 on 2008-02-13
Hello, I have posted about this topic before and it seems that nobody has come up with a common solution for the common beginner.

I have a Toshiba A205S-4577 Notebook with the RealTek High Definition audio drivers.  I have no sound.

I am a new Ubuntu user, and I no basically nothing about "compiling" or editing programs and drivers.  

Is there anybody out there that can either give a detailed step-by-step guide on how to get this to work (I have been reading that it is possible, what with the new ALSA drivers > there's even a driver on the RealTek site for Linux)?

I would appreciate any help I can get.

Thank you!


P.S.    When I say step-by-step, I mean literally step-by-step.  Too many posts for "simple" solutions have aimed at me with no consideration for the fact that I am an average computer user (not a "nexter") who installed Ubuntu with the desire for an OS that is unique, safe and also user friendly.  I no nothing about "compiling" so if the solution requires compiling, I would also appreciate a description on how to do this and what it does.

Thank you.

---

### Post by oedha on 2008-02-13
can you open terminal
then type :==> sudo lshw -short -C sound
then post here the result

---

### Post by Jewfro_Macabbi on 2008-02-13
Compiling means to take some source code - and turn it into and executable/binary for your machine - or another machine.

It's actually not very difficult - and the instructions generally come with the source code you wish to compile. It requires some packages

build-essential, and checkinstall is also very helpful

Generally there are three steps:

./configure - configure this program to run on this machine 

make - create the executable

make install - install the executable

Using the package checkinstall it's possible to change that last step to:

checkinstall -D

this first creates a debian file - and then installs it - which is far easier to remove later.

---

### Post by littletinman on 2008-02-13
I've got the realtek hda chips too and no sound on my acer 5520. Been trying for 4 days but no luck!!!!

---

### Post by littletinman on 2008-02-13
> **oedha said:**
> can you open terminal
then type :==> sudo lshw -short -C sound
then post here the result

here's mine,
H/W path        Device     Class       Description
==================================================
/0/7                       multimedia  MCP67 High Definition Audio


any help is very appreciated!!!!!!

---

### Post by oedha on 2008-02-13
since it's realtek......i succedded on realtek ALC268......on Acer4520
here's what i've done
go to system - administration -synaptic
search for linux-backports
i believe all of you using amd64.....so
mark on linux-backports-modules
and also
mark on linux-backports-modules-generic
then apply them
then
open terminal to type :==> sudo gedit /etc/modprobe.d/alsa-base
insert : options snd-hda-intel model=acer
save it by pressing ctrl+s then quit by ctrl+q
reboot the computer
please report the progress

---

### Post by littletinman on 2008-02-13
I htink i have all the right modules loaded. I put the "acer" inot the text file and now will reboot. I'm running the 32 bit version. Is 64 better? i've got duel core 64x2 Turion by AMD. I haven't transfered my files from my other computer onto my new one in case i had to reinstall or something. Should i reinstall with the 64 bit version? i sorta don't want to because it's taken me about 3 days to set everything up the way i like it (except sound).

---

### Post by oedha on 2008-02-13
if you use your computer only for daily work.....fine in i386
but since yours is amd64....it will be better to install amd64
it's up to you......
and i believe if you have install those 2 backports and also insert the sentence 
your will hear the sound......we have the same card......

---

### Post by littletinman on 2008-02-13
i use my laptop alll the time for everything. How much faster is 64?

---

### Post by oedha on 2008-02-13
i am not sure and never measure it........but using amd64 on amd64 computer ...means they fit together.........and you will get all the benefit of 64bit..but it will consume more space :)
if you want to play games....or 3d things....i suggest you use amd64
if only for surfing, chat,type........i386 ok

---

### Post by littletinman on 2008-02-13
thanks. that's helpful. i still have no sound though.

---

### Post by sfitch29 on 2008-02-24
sorry about the reply time - but I still have not fixed this sound problem - here is what it says in the terminal:  

H/W path           Device      Class       Description
======================================================
/0/100/1b                      multimedia  82801G (ICH7 Family) High Definition 
scott@scott-laptop:~$

---

### Post by petoro on 2008-02-27
Same problem in my laptop, Can't hear anything,

   sudo lshw -short -C sound
H/W path             Device      Class       Description
========================================================
/0/100/1b                        multimedia  82801H (ICH8 Family) HD Audio Controller



Petoro

---

### Post by Iehova on 2008-02-27
> **petoro said:**
> Same problem in my laptop, Can't hear anything,

   sudo lshw -short -C sound
H/W path             Device      Class       Description
========================================================
/0/100/1b                        multimedia  82801H (ICH8 Family) HD Audio Controller



Petoro

I have exactly the same as you and my sound works perfectly... Humour me for a moment, won't you, and go to the volume control, hit edit > preferences and tick every one of the checkboxes. Can you make sure once you've done that that none of the tracks are muted?

Thanks,

---

### Post by superprash2003 on 2008-02-28
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by petoro on 2008-02-28
> **Iehova said:**
> I have exactly the same as you and my sound works perfectly... Humour me for a moment, won't you, and go to the volume control, hit edit > preferences and tick every one of the checkboxes. Can you make sure once you've done that that none of the tracks are muted?

Thanks,


It is very strange because I've verified all those controls and none was muted.  I have never heard a sound from my linux OS since I installed Gutsy on 07/10.  In Windows Vista sound works fine.

When I try to play an mp3 in Totem I can see all the fancy drawings on screen but I can not hear any music.

Could it be because I installed de 64 bit version of Ubuntu 7.10?


Petoro

---

### Post by petoro on 2008-02-28
> **superprash2003 said:**
> try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

I had tried that also. But no sound in any configuration.


Petoro

---

