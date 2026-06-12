---
title: "Gimme back my yaboot!"
date: 2007-02-07
forum: Apple PPC Users
---

### Post by Othorpe on 2007-02-07
Hi,

I've run into something that I think should be easily fixed, but all the posts I've found solve the same problem for different setups. I can't find one that works for mine.

Basic overview: I had Ubuntu 6.10 running fine on my B&W G3. I upgraded the machine with a Sonnet G4 processor, and after the firmware updating, etc. I can't get yaboot to run anymore so I can boot into Ubuntu.

The other fixes I find all tell how to do it when your HD is partitioned with OSX/Ubuntu, but I have multple internal ATA HDs. Forcing it to boot off the first partition doesn't help me.

My setup:

B&W G3 w/G4 Upgrade. 1GB RAM. 
HD1: MacOSX on one partition, Mac OS 9.2.2 on another
HD2: Ubuntu
Linux knowledge: *noob*

I can boot into Ubuntu on the Live CD... Now what? How can I get back to being able to choose which it boots? Must I reinstall Edgy, and if so, will I lose the settings I already had?

Any help is greatly appreciated.

Thanks!

---

### Post by samden on 2007-02-08
You could try:

Booting into 'Restore' mode on the ALTERNATIVE install cd.

Reinstalling Yaboot this way.

That may fix the problem possibly, if not it shouldn't hurt anything.

---

### Post by oswaldkelso on 2007-02-08
Hi
 I tri boot debian osx and ubuntu on my G4 tower with debian as default and choose either x l or c on startup.
 Sometimes I "loose" my yaboot settings and rather than

1.holding the alt key and picking which drive to boot from,

2. or re-editing my yaboot settings, (after 1) I do

3. I remove the battery and zap the p-ram. (apple alt and p and r keys all at the same time on boot) you better google that as I dont have an apple keyboard.
This has the effect of resetting yaboot back to my default debian boot:) I then shut down and replace the battery. 
I also have a scsi drive that I unplug as it confuses things.
As you've replaced the processor and up dated the firmware I have no idea if it will work but as a last resort?? 

good luck

---

### Post by Othorpe on 2007-02-08
Hi,

Thanks for the feedback--I haven't made much progress yet, though.

Samden: I didn't even know about the Alt Install disc. I got a copy, but am not sure how to get into "Restore" mode. I see "Rescue" and "Expert", could you have meant either of those? I was able to find a "Install Yaboot on a Hard Disk" option on the Expert method, but everything seems to want to make me partition the drive again--I'm hoping I can fix this without resorting to that. (It's more of a problem solving thing than a lost data issue--there's nothing on there that I can't afford to lose, but I just want to solve it without the double-barrell shotgun approach) :) Am I overlooking something from your instructions? Can yaboot be reinstalled without reinstalling the whole thing? It seems there has got to be a way.

Oswald: Thanks--I have seen that tip, but my understanding is that is more of a solution when the different OSes share a drive, isn't it? In any case, zapping the PRAM was part of the  processor upgrade procedure, so that's been done already.

I *know* if I reinstall, someone's going to pop on here and tell me a simple thing I could have done... I'll hold out a while longer

Thanks for all the help so far, everyone.

---

### Post by fkdev on 2007-02-09
I think this problem lies with resetting PRAM. Open-Firmware forgets about starting yaboot due to this.
Couldn't you do this (I think this works with multiple hard-drives):

1: Hold down the alt key during system start-up
you should be given the opportunity to select from a hard-disk with a mac logo, penguin, etc.
2: Select the penguin logo. Your computer will start yaboot, allowing you to log in to linux
3: In order to make your yaboot work again, open your favorite terminal (for example, something like applications->utilities->Terminal)
4: type
```
 sudo ybin 
```
inside of the terminal, entering your password when prompted.

this should reinstall yaboot with the same configuration as before. Assuming that yaboot was working previous to your 
upgrade, your yaboot should be up and running again.
(If step 2 doesn't show your linux drive (with the penguin), just post and i'll tell you how to do this from the standard livecd, instead, skipping step 2)

---

