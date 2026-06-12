---
title: "[SOLVED] no sound"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by eragon100 on 2007-09-10
Hoi everyone!

I switched to ubuntu ultimate 1.4 (feisty fawn) 6 days ago, so i don't know much about it. I have two soundcards, a onboard via hd audio and a sounblaster audigy se. In the beginning i often didn't have sound, because linux randomly picked one of the two soundcards as the default when i started my computer, and of course i don;'t have speakers in my onboard card. i fixed this by going to the console and typing: "asoundconf set-default-card CA0106". This worked and my sound worked perfectly for a couple of days. Yesterday however, i didn't have any sound at all, except for the sound i should hear when I have to login at startup (NOT the login sound itself!). Can someone please help me in beginner terms? I don't understand why would simply quit working without any warning and without me changing anything :confused:

---

### Post by mikeyphi on 2007-09-10
See if this guide is of help: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound)

---

### Post by eragon100 on 2007-09-10
thanks! I wil see wath i can get out of it

---

### Post by eragon100 on 2007-09-10
doesn't help:(

---

### Post by tvrg on 2007-09-10
Try double clicking the volume icon in the top left, this should open volume control.
After you did that slide some of the sliders up (particulary master and PCM, you also have to click File > change device and select the other device to change volume for alsa as wel as oss)

---

### Post by eragon100 on 2007-09-10
they're already at full, and the sound isn't ofline either. By the way, with the sound card i have attached my speakers too, i only get "line in" and "microphone" under alsa , and only pcm under oss :confused::(

---

### Post by eragon100 on 2007-09-10
the sound really worked perfectly till yesterday, after i had my default soundcard, although it didn't work sometimes (1 out of 5 perhaps). When i rebooted my computer earlier this afternoon, i only heard the sound that i should login, and nothing after that, which was also what happened if it didn't work the last few days. I tried rebooting my computer 5 times, resetting my default soundcard and typing again that the soundblaster audigy (CA0106) should be the default card, and i followed all the instructions from the guide posted above in this tread, including setting up my 5.1 surround speakers, but all without any effect whatshoever, and i barely know what I'm doing :mad:

---

### Post by eragon100 on 2007-09-10
i don't understand it but after restarting 6 or so times i have :guitar:!! The problem is i don't wanna have :guitar: one out of six times i use my pc, but every time i start it up. Al least fun that's working for now, should allow me to play games etc! :)

---

### Post by eragon100 on 2007-09-11
anyone has any idea howto solve this problem?!

---

### Post by the.phantom on 2007-09-11
one idea to make it easier on Ubuntu 

now you have a onboard sound and then you installed s soundblaster


ok have you opened up the BIOS and disabled the onboard sound card?

then Ubuntu will not know it is there ;-D
and you have done the usual things of right click the speaker icon 
and looked at preferences and volume control 
and then did a 


sudo alsamixer 

and checked there? using the arrows to move around 

i am a lightweight on Ubuntu and linux but on one box i have a onboard soundcard and i installed a cheap used soundblaster. and disabled in the bios the onboard and then played with the sound settings and all is well now

---

### Post by eragon100 on 2007-09-12
Thanks for the reply! First of all, sorry it took so long for me to respond, but i was asleep and at school, only just got to read your message. I can't disable my onboard soundcard in the bios, at least i don't know how, i checked all other things, and if i do sudo alsamixer i get he folowing error message:

liam@liam-desktop:~$ sudo alsamixer
Password:
ALSA lib control.c:875:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory
liam@liam-desktop:~$ 


help :confused:!

---

### Post by tvrg on 2007-09-12
are you on 64 bit?

---

### Post by eragon100 on 2007-09-12
No, my intel core 2 duo is 64-bit, but i have 32-bit ubuntu ultimate 1.4 gamers edition installed, based on 32-bit ubuntu 7.04 feisty fawn.

---

### Post by tvrg on 2007-09-12
hmm, ultimate... gamers edition.... that's an unofficial distro made by some forum members.

Are you having the same issues with a default ubuntu feisty?
If not I would suggest contacting the ultimate folks, maybe it's a bug in their release

---

### Post by polly1 on 2007-09-12
Hi

I have Audiology 2 Sound card with Sound Blaster 4.1 Speakers on Dell  Dimension  8300 and had the same problems as you, in that the adjustments I made did not hold. My problem was solved by turning the sound and on-board speaker off, as suggested by the.phantom.

Strike the f2, or whatever key is shown to get into the "Set-up" option at the bios screen. The Integrated  Devices or similar should be be on the menu. Go into that and turn off the sound and speaker options.Then double click volume icon on top panel bar and I suggest you uncheck all items except the Surround, Front, Centre and Audio Jack options. 

I hope this helps

---

### Post by eragon100 on 2007-09-14
I can't disable the soundcard from the bios, however i think i solved the problem. I selected my onboard soundcard as default, and then immediately selected my correct one. It has now booted 3 times in a row with sound. :lolflag: I'm keeping this thread open in case the problem returns, but i think that because ubuntu doesn't kep the settings, i simply have to set them every few days, that's two seconds of work anyway.

---

### Post by tvrg on 2007-09-14
is it a laptop or a desktop?

if it's a desktop you might be able to disable it using a jumper setting

---

### Post by eragon100 on 2007-09-15
It's a desktop, but like i said, the problem is solved. i restarted a lot of times with sound, so I'm going to mark this thread as solved.

---

### Post by mike-g2 on 2007-09-19
> **eragon100 said:**
> I can't disable the soundcard from the bios, however i think i solved the problem. I selected my onboard soundcard as default, and then immediately selected my correct one. It has now booted 3 times in a row with sound. :lolflag: I'm keeping this thread open in case the problem returns, but i think that because ubuntu doesn't kep the settings, i simply have to set them every few days, that's two seconds of work anyway.

I'm having this same problem and it is unclear to me exactly what you did to solve the problem. Could you be more specific?  I'd really appreciate it.

BTW, do you have any idea which package supplies the libasound_module_ctl_pulse.so file?  I searched but couldn't fine it anywhere.

Thanks.

Mike

---

### Post by eragon100 on 2007-09-24
What is that file? :confused:

The sound system does remember the settings now, i haven't had problmes for a week. After ubuntu forgot the settings, i went to the terminal. There i selected the wrong (my onboard) soundcrd as default, and then with the next command i selected my soundblaster audigy as default, thinking it would again remember that setting for a few days. Correct hunch, i have had snd ever since.

to change soundcard default first type "asoundconf list" to see the codes of your soundcard, and then type: "asoundconf set-default-card x" (without the quotes). Then it should work!

---

