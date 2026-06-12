---
title: "newb with no sound, edgy 6.10, via 8237"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by deezay on 2006-12-22
i can't get sound to work with any programs. i've gone through the fixes that i can find and nothing is seeming to work for me...

' aplay -l ' gives me:

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

so, i know it sees the card, nothing is muted in the mixer, and i've tried gone into System -> Preferences -> Sound and tried running test tones with every device listed in the drop down. my guess is that it's something really easy that i am just overlooking in my haste. any help or insight on this would greatly be appreciated.

but other than this little snag, i haven't had near as many hassles installing ubuntu as i did installing mandrake back in the day. linux and user friendliness has really come a long way.

thanks!

-andrew

---

### Post by deadgobby on 2006-12-22
If you have a sound card like Sound Blaster for sample. You might want to go into BIOS and disable the onboard sound card. All so you may want to install ALSA mixer or ALSA mixer for Gnome. What sound card do you have? What are you system specs. Like of you have a Dell system.
Gobby

---

### Post by deezay on 2006-12-23
just onboard. and my guess is it's a via 8237.. atleast that is what ubuntu sees.

EDIT: it's a homebrew system i made from spare parts:

msi mobo KM4MV
amd duron 1.8
512mb ram

---

### Post by mickbw on 2006-12-23
I was having a very similar problem.  Tommcd gave me a link that helped me resolved the problem.  

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

In my situation the alsamixer showed that pcm (whatever that is) was shut off.  I turned it on and gave it some volume and voila.  

Good Luck,

Michael

---

### Post by nawzyah on 2006-12-30
deezay, have you found a solution to your problem?  I'm currently in the same predicament with the same onboard sound chip.  Please let me know how you resolved it.  Thanks.

---

### Post by logos34 on 2006-12-30
[cancel]

---

### Post by nawzyah on 2007-01-05
I just wanted to post that I've since solved my sound issue.  All I did was move the 3.5mm plug to the top middle jack.  In Windows, I had a Realtek driver that (sometimes) auto-sensed what device I was plugging into the VIA 8237 jacks.  In Ubuntu, you just have to try all the jacks and find out which one is the sound output.  ](*,)

---

### Post by tommystoy on 2007-01-07
Great Post. I'm a total ubuntu newb and was also pulling out my hair. I have the via 8237 chipset w/ Realtek ac97. The sound device was detected, driver loaded - but no sound](*,) 

Read your post and realized that I was connected to my Altec 4.1 surround via the mobo's optical port.  Connected a stereo cable and - voila- sound!!! 

Will worry about 4.1 later. Now if could just get my SCSI scanner to work!!!

Tom

---

### Post by hysteresis62 on 2007-01-07
WOOHOO!

This post rules after school!

I've been trying to fix this problem through the software for like a week.  It just never occured to me to try plugging the line into another socket.

I feel both very happy and kind of like a dumbass.

Thanks so much.

Joe

---

