---
title: "No Sound: Toshiba A105-S2071 w/ Realtek. Please help!"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by trdcelica on 2008-03-01
Hey guys..

First off I would just like to say that I am a LINUX NOOOOOOB. I just came over from Windows and while I do have limited experience with the command interface, I am trying as best I can to keep learning with Linux. Now with that said here is my problem. Currently I have Ubuntu 7.10 installed.

I have no sound on my laptop. Soundcard is detected and it is the infamous Intel HDA chipset on the Realtek ALC861 (I think I worded that correctly). I officially have 9 hours vested in sitting on my butt and staring at my laptop trying to fix this. 

I have tried modifying the alsa-base script with the additional line "options snd-hda-intel model=3stack" to no avail. Please if anyone could help me I would greatly appreciate it. Please just tell me what you need and how to provide it and I will be on it.

---

### Post by herbster on 2008-03-01
Not to insult your intelligence but many a times the case has been muted mixer levels. Have you checked alsamixer's levels?

---

### Post by LuisGMarine on 2008-03-01
Try this:

Open up a text editor and copy the following text into it.

```
#! /bin/bash
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2
tar -jxvf alsa-driver-1.0.15rc3.tar.bz2
cd alsa-driver-1.0.15rc3
./configure --with-cards=hda-intel && make
sudo make install
sudo cp ./modules/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
sudo depmod -a
echo "You need to reboot for changes to take affect."
```

save it as  *sound.sh*, and remember to save it somewhere easy to find, like your desktop.

Then run this command where ever you file is:

```
chmod +x sound.sh
```

Then run the file as so:

```
sudo sh sound.sh
```


All credit goes to Kennet,

[http://ubuntuforums.org/showthread.php?p=4349687](http://ubuntuforums.org/showthread.php?p=4349687)

---

### Post by trdcelica on 2008-03-01
Yes I did check those. During my huge Google hunt I found a post with instructions on how to check. I went through, everything was un-muted. Thanks for the reply :)

---

### Post by trdcelica on 2008-03-01
Thanks for the link. Question about his instructions (i named his script "script", with "chmod +x (filename you choose)" did he mean type "chmod +script" or chmod +xscript

I am not actually sure what the x is in there for...

---

### Post by herbster on 2008-03-01
It's

```
chmod +x script
```

The "x" is a switch in the chmod command, making the file "script" executable.

---

### Post by trdcelica on 2008-03-01
ran the script, no luck on my end for sound..

Just to confirm... i ran "alsamixer" in the terminal and nothing was muted.... yet i thought it was muted by default? My cd, pcm, mic, etc are all maxed out in volume... am I missing anything? Thanks

---

### Post by trdcelica on 2008-03-01
i just double checked my alsamixer and it tell me my "master" is at 0.... would this be master volumn? If so, even so I cannot raise it any higher. It just remains at 0

---

### Post by trdcelica on 2008-03-01
also I am getting some sound now but it is literally so faint that the humming of my laptop overpowers it... thats how faint it is... its useless

---

### Post by trdcelica on 2008-03-01
bump for ideas

---

### Post by herbster on 2008-03-01
Open your volume control properties and check which device you're using (right-click volume icon, properties, File > Change device).

---

### Post by ivancamilov on 2008-03-02
Man I've got the exact same problem... No sound from the built in speakers and a very, very very low sound when I plug in my headphones. I'm running Ubuntu Gutsy Gibbon (7.10) on a Toshiba Satellite A105-S2051, so basically we're in the same spot.

Maybe this has something to do with it...  when I did a dmesg I found the following message:

```
[    6.564000] 8139cp 0000:02:07.0: Try the "8139too" driver instead.
```I think that is the driver for the sound card... how can I switch the driver to the one I need?

---

### Post by ivancamilov on 2008-03-02
well, I got tired of searching for a fix and rolled back to feisty (I liked it better anyway... gutsy took too much time loading). But hey, maybe I can help looking why does the sound work in feisty and not in gutsy... any pointers here to where I should look?

---

