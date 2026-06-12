---
title: "[SOLVED] Headphones Not Recognized in Gutsy"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Aurora@FleetBuzz on 2008-01-01
I just upgraded to 7.10 and everything appears to be fine except that my headphones did not install.  I've run "alsamixer" from the terminal but no headphones are listed!  Same with the "preferences" when I open "volume control".  My external speakers work fine.   My computer is a Dell Dimension 8200 with a soundblaster sound card.The headphones and speakers both work fine in Windows XP.

I have updated the system but still no solution.

Any suggestions would be appreciated.

---

### Post by (((X))) on 2008-01-01
I couldn't figure it out on my other computer, just used headphone in on monitor..anyway
Try to mute volume and turn on again, maybe that helps.

---

### Post by Aurora@FleetBuzz on 2008-01-01
Unfortunately, I don't have that option on my monitor.:(

---

### Post by jken146 on 2008-01-01
Try unmuting and turning up various things in alsamixer.  Does sound come out of the speakers OK?

---

### Post by Aurora@FleetBuzz on 2008-01-01
When I run alsamixer, only 3 columns appear:  "Master", "Master M", and "PCM"; all are unmuted.  There are no entries in the following: "3D Contr" (three columns), "Surround", and "Line".  As I said, the speakers work fine.  Ubuntu just doesn't recognnize my headphones.

---

### Post by Aurora@FleetBuzz on 2008-01-02
Progress!

I found this thread and following the instructions posted by **ugm6hr**, I'm able to hear sound through the headphones and the mic works!
[http://ubuntuforums.org/showthread.php?t=648381&highlight=headphones](http://ubuntuforums.org/showthread.php?t=648381&highlight=headphones)

Unfortunately, if I turn down the volume control on the external speakers, it also turns down the volume on the headphones.  I can't operate the headphones independently.

Any ideas.

BTW, thanks **ugm6hr** for your timely advice!

---

### Post by ugm6hr on 2008-01-02
Glad that I could help. I am a bit confused about the appearance of your alsamixer.

Have you worked out which "channels" are which (i.e. which is speaker, and which headphone)?

If alsmixer doesn't have the right options, amixer can sometimes help.

Maybe post a scrennshot of alsamixer?

---

### Post by Aurora@FleetBuzz on 2008-01-02
I am utterly chagrined to have to say this, but now the headphones won't work!  Fortunately, the microphone does still work and I can use Skype (if I don't mind listening to the audio over the speakers!).  

I didn't track what I did.  I found out from your instructions that I could arrow over to different channels on alsamixer and that's what I did--just maxed stuff out.  I could go back and reconstruct?

I've taken screenshots, but don't know how to include in this post.

Thanks for your help here.

---

### Post by ugm6hr on 2008-01-02
> **Aurora@FleetBuzz said:**
> I didn't track what I did.  I found out from your instructions that I could arrow over to different channels on alsamixer and that's what I did--just maxed stuff out.  I could go back and reconstruct?

I've taken screenshots, but don't know how to include in this post.


Just go back to alsamixer and max them all again.  Hopefully that should work (again).

Then try muting individual channels one at a time to see which "channel" corresponds to the headphones, and which to the speakers.  Thats your answer.

Unfortunately, the Ubuntu (Gnome) volume control only allows for a single setting - so you can chose which channel it controls.  Which is sensible for most....

But it does mean that you have to chose.  If you have a desktop - I would recommend you set it to control the headphone volume.  Cos you can usually easily control the speaker volume from the hardware speaker volume control (just leave the software volume at maximum).

---

### Post by Aurora@FleetBuzz on 2008-01-04
Well, it worked again.  The culprit was the "sigmatel" switch (there are 4 of them).  I've maxed everything out and headphone and microphone not only work, they work independently of the internal speakers!

Much obliged again, **ugm6hr**!  I came across another thread where someone is having a similar problem and I will refer him/her to your sage advice.:)

[http://ubuntuforums.org/showthread.php?p=4073953#post4073953](http://ubuntuforums.org/showthread.php?p=4073953#post4073953)

---

### Post by Pechorin on 2008-01-07
I am having similar problems with the headphones not being recognized in Gutsy. Spent some time trying to fix the problem in vlc, before I realized it was much worse than that. Also stumbled across a thread discouraging the use of Gutsy on hp-laptops (me)

[http://ubuntuforums.org/showthread.php?t=582220]("http://ubuntuforums.org/showthread.php?t=582220")

In any case, the alsamixer-approach did not work for me unfortunately. I have faithfully muted and unmuted everything I could find there, but nothing seemed to relate to the headphones. Not even the control labeled headphone which only had the MM/00 option, no intensity-bar.

The strange thing though (maybe) is that there are two controls relating to the laptop speakers. One labeled PCM, the other Front.

I'm thankful for any further ideas you might have on how to fix this. I am rather new to ubuntu and this forum, this actually being my first forum-post ever. So wish me luck :)

---

### Post by ugm6hr on 2008-01-07
> **Pechorin said:**
> In any case, the alsamixer-approach did not work for me unfortunately. I have faithfully muted and unmuted everything I could find there, but nothing seemed to relate to the headphones. Not even the control labeled headphone which only had the MM/00 option, no intensity-bar.


Did you try the up/down arrows on the "headphone" control? If there is no intensity bar, it may just be because it is currently set at 0%.

If that doesn't work - sometimes amixer allows greater control than alsamixer.

---

### Post by Pechorin on 2008-01-07
Yes, I tried using the arrow keys. Nothing happened. The other devices showed the volume-bar even when they were turned completely down (except Headphone, Caller ID and Off-hooks, which didn't have any bar, whatever those last ones might be)

**Using Amixer**

Typing [amixer] produced this result:

Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]

Typing [amixer sset Headphone 80% unmute] did not change anything. And still no sound coming through the headphones. 

The on/off status from amixer can also be changed via alsamixer and the Volume Control from the desktop panel. 

Either the 80% option is ignored somehow, and still set to 0%, or something else is the matter.

---

### Post by ugm6hr on 2008-01-07
> **Pechorin said:**
> The strange thing though (maybe) is that there are two controls relating to the laptop speakers. One labeled PCM, the other Front.

PCM is an overall volume.  It needs to be on for any volume to work.  Have you tried maxing out **all** volumes to see if headphones work?

The headphone control you have is identical to mine - there is no "Limits" control in amixer.

---

### Post by Pechorin on 2008-01-08
Headphone jacks are now working!

The ultimate problem turned out to be that the alsa-driver provided by synaptic-package-manager is out of date. Atleast for hp pavilion tx1000 the alsa-driver version needs to be 1.0.15 or higher.

To check which version you have type [alsactl --version]

To download and install the needed software there is an automated script you can use here (the instructions are very easy to follow):

[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html")

Also you need to append this sentence to /etc/modprobe.d/alsa-base (use [sudo] to edit)

options snd-hda-intel model=hp

If you have another system and 'hp' did not work for you ,find your model here:

[http://ubuntuforums.org/showpost.php?p=3796486&postcount=1]("http://ubuntuforums.org/showpost.php?p=3796486&postcount=1")

This worked like a charm for me. Here are some references to where I found tips in the forum:

[http://ubuntuforums.org/showthread.php?p=3243087#post3243087]("http://ubuntuforums.org/showthread.php?p=3243087#post3243087")

[http://ubuntuforums.org/showthread.php?t=612605]("http://ubuntuforums.org/showthread.php?t=612605")

---

