---
title: "Compiling alsa"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-10-05
I lost my volume about a week ago and read that reinstalling alsa could fix this problem. Following the instructions on this page ([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)) I downloaded the latest alsa packages (1.0.15rc3 for the driver and lib and 1.0.15rc1 for the utils) and began compiling. When i type this

sudo cp ~/downloads/alsa* .


in the terminal I am told:

tar: alsa-driver-1.0.15rc3.tar.bz2: Not found in archive
tar: Error exit delayed from previous errors



What is wrong? I am desperate to get my sound back.

---

### Post by derby007 on 2007-10-05
What about getting the correct version of ALSA for your verson of Ubuntu? @ : [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa&searchon=names&subword=1&version=all&release=all). Worth a try if all else fails.

---

### Post by intense.ego on 2007-10-05
i really don't understand which one to download because I'm running feisty and they say i should install 1.0.13 but on the official page it says 1.0.15rc3 is the latest.

---

### Post by derby007 on 2007-10-05
I would go with the '1.0.13-3ubuntu1'

---

### Post by intense.ego on 2007-10-05
do i have to download each one of the 34 packages individually? Is there an easier way of updating alsa that does not require compiling, like through synaptic?

---

### Post by stchman on 2007-10-05
> **intense.ego said:**
> I lost my volume about a week ago and read that reinstalling alsa could fix this problem. Following the instructions on this page ([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)) I downloaded the latest alsa packages (1.0.15rc3 for the driver and lib and 1.0.15rc1 for the utils) and began compiling. When i type this

sudo cp ~/downloads/alsa* .


in the terminal I am told:

tar: alsa-driver-1.0.15rc3.tar.bz2: Not found in archive
tar: Error exit delayed from previous errors



What is wrong? I am desperate to get my sound back.

I have a script that will recompile your ALSA for you.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

---

### Post by intense.ego on 2007-10-05
how do you run the script as root?

---

### Post by intense.ego on 2007-10-05
never mind my last question. It worked! Stchman, you are a GENIUS!!! Thank you so much.

---

