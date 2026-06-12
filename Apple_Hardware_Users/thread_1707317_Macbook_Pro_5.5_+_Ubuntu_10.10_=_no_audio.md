---
title: "Macbook Pro 5.5 + Ubuntu 10.10 = no audio"
date: 2011-03-15
forum: Apple Hardware Users
---

### Post by rob_jewitt on 2011-03-15
Hi all  - I'm very new to Ubuntu and have installed it on my Macbook Pro 5.5 via rEFIt+ and the install works well except for the lack of sound.  

I've seen this issue posted about on the forums and I've followed [the advice posted her]("http://ubuntuforums.org/showpost.php?p=7627817&postcount=98")e as best I can with my limited knowledge.  Terminal didn't recognise the aptitude (command not found). :(  I guess that may be due to an older build of Ubuntu being used in the example?

Does anyone have any advice/links on how best to proceed with sound/audio issues using 10.10 (64 bit)?

Many thanks

---

### Post by pauljwells on 2011-03-15
Aptitude is a 'fancy' version of apt-get, you can install it from synaptic, but don't do that yet :) I think all of that is a red herring...

It is most likely that a simple config is stopping your sound, and this is how you fix it:

Start a program that plays a sound, a video in Totem is best because you know for sure that it is running.

Then, open a terminal and type 'alsamixer' - this will give you a text-window of the various sound devices working on your computer. You move between the devices with the 'Tab' keys and you should try to mute and unmute each one by pressing the 'm' key.
Try to be consistent. Press 'm' once and if you don't hear anything press it again and move to the next device. Eventually, one of the devices will turn out to be your speakers and you'll blast your eardrums off because you turned the volume up to max in an earlier attempt ;)

Good luck, post back with results

---

### Post by Chasetaylor1 on 2011-03-16
Go to [https://help.ubuntu.com/community/MacBookPro5-5/Lucid](https://help.ubuntu.com/community/MacBookPro5-5/Lucid) and look under the sound section. I was able to set up the sound perfectly using this method on a Macbook 5,5 so It should work for you as well.

---

### Post by pauljwells on 2011-03-19
> **Chasetaylor1 said:**
> Go to [https://help.ubuntu.com/community/MacBookPro5-5/Lucid](https://help.ubuntu.com/community/MacBookPro5-5/Lucid) and look under the sound section. I was able to set up the sound perfectly using this method on a Macbook 5,5 so It should work for you as well.

Yep, that would be alsamixer...

---

### Post by rob_jewitt on 2011-03-23
Thanks for the responses. I copied an avi file from my Macbook and opened it with 'Movie', then opened up Terminal and entered 'alsamixer' only to get the following message:

cannot open mixer: No such file or directory

???
**EDIT** - Alsamixer worked - audio is fine now - thanks for the help :-)

---

### Post by bleu_canary on 2011-04-14
Hey, thanks so much. I too am a Ubuntu newbie convert from Apple that was getting really frustrated with nothing really explaining what I was doing trying to get the sound to work. Thanks so much for you few words. They were more helpful than all the other articles that I read about how to do. You rock!

---

