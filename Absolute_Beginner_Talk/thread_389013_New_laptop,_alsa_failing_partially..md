---
title: "New laptop, alsa failing partially."
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by sigge on 2007-03-20
Just got a new laptop. A HP dv6000, where I run Ubuntu 6.10 It has a soundcard that the current ubuntu-alsa-package (1.0.11) does not support fully. The headphone and mic jacks are not functioning... Apparently the newer alsa (1.0.13) libs does support this partially... (according to other ppl, never tried this myself...)

So I searched, and I know this package is present in the debian testing and unstable repoes. There is also a tar.gz-pkg out there somewhere... But I can only fin a .deb for amd64 architecture, and I'm not fully shure how to install alsa 1.0.13 from source without breaking apt... :(

Colud someone please:
a) Direct me to a package prepared for ubuntu with alsa 1.0.13

or

b) Show me a how-to for installing alsa from source while not breaking future installs... :-k 

...ah'thank ya very muchah... Good night.

---

### Post by renzokuken on 2007-03-20
i had sound issues on my new laptop after installing ubuntu in that nothing came out of the speakers or headphones or anything even though it appeared to be playing sounds fine.

i solved my problem by compiling the latest alsa-driver from source. once done my sound worked perfectly and havent had a problem since. i think the latest package i used at the time was 1.0.14rc2.

its very easy to compile it from source

get the latest driver (stable or release candidate, your choice) from [www.alsa-project.org](www.alsa-project.org) and save it to your desktop. 

then run the following commands in order from the terminal

```

sudo apt-get install build-essential
cd Desktop
tar xjf alsa*
cd alsa*
./configure
make
sudo make install

```

reboot and see if it works

---

### Post by sigge on 2007-03-20
Thank you for a quick reply! :)

I'll try your tips soon, but first a few questions:

Shouldn't  I "uninstall" the alsa package beore doing this?
Will alsa automagically update once the repoes catch up?
Is there anything else I need to do? (Dependencies, etc.)
Isn't 1.0.14 an unstable release? As 1.0.13 is reported to fix the problem, wouldn't it be prudent to try the stable release first?

I'm very concerned, as this detail is not "critical," and my current setup otherwise works very well, after a lot of tweaking. Will this somehow bite my *ss later? ;)

Lots of luv to whom-ever answers, and all of the ubuntu-community! \\:D/

---

### Post by renzokuken on 2007-03-21
ok, dont take these as definate answers but i will give you my personal experience/opinion on them

1. compiling a newer alsa-driver from source simply "updates" or replaces the older version. you shouldnt have to uninstall anything, i didnt.

2. i dont know if they update alsa in the repos, but assuming they do, it should just update whatever version you currently have installed.

3. the "sudo apt-get install build-essential" command takes care of the necessary dependencies (this gives you the packages necessary to compile from source, the only dependencies for alsa-driver)

4. yes, 1.0.14 is an unstable release. it worked perfectly for me, but if you are unsure and it says the stable 1.0.13 works for your hardware then go with that one.

the only question i am a bit unsure on is 2. compiling from source does not effect apt at all really since it is not involved. but if you say compile 1.0.13 from source, then 1.0.14 becomes available in the repos and you then install that via synaptic, im not sure how they will all effect each other. at the end of the day, if compiling 1.0.13 fixes your problem i wouldnt worry about updating further. or you could just compile from source to update again which should work fine.

---

### Post by sigge on 2007-03-22
Thanks dude!:guitar: 

Ubuntu rocks, and so do you!

---

### Post by renzokuken on 2007-03-22
so did it work then?

---

### Post by sigge on 2007-03-24
Well... I'm not so "adventureuos", so I went for the 1.0.13 version. Compilation works fine with the standard developers package. It seems to work for the most part... It fixes my problem with no sound at all in the headphones! :)

Function is otherwise somewhat broken, but not so that it hinders me. I hear sound in both the speaker and headphones, but I can set the volume separatly for speakers/phones in gnome mixer aplett. :D

Like I said.... THANX!
:biggrin:

Update!---
After upgradeing to feisty, The problem is all gone... :) Lovely sound, the headphone-port mutes the speakers, mic works, (all 3 of them...)
But that would be _after_ i did the install of the drivers all over again... ;)

---

