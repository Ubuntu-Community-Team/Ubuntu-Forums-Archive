---
title: "Advice sought on Audio Recording Problems"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by John Fraser on 2007-05-03
It's been a week now since I installed Feisty, and everything has been great. A most trouble-free installation for a non-techy. I'm now trying to get the bells and whistles working!

I can play back audio and video with no problems.
I cannot record anything with my microphone, which I have tested on a Windows machine. It's working fine.

I'm trying to record my voice as a test, using Sound Recorder. I am checking Microphone on the first screen, and have tried recording as wav, mp3, and ogg. 

I record for a few seconds, then stop and save. I then get an error message: Could not save the file "Invalid Parameters". Quitting Sound Recorder then gives me another save option, which seems to work, and the sound file is saved to my home folder. On playback this is silent.

I have tried playing around with settings in System>Preferences>Sound, and in Alsamixer, and am now completely confused!!

Is there a kind soul out there who could mentor me through this problem, please?

All help greatly appreciated!

---

### Post by Ianman on 2007-05-03
Have you tried any other applications for recording? I would recommend Audacity. You can find it in the Add/Remove application on the Applications menu.

To be totally honest I have never used a mic in Linux but perhaps it is application related.

---

### Post by starcraft.man on 2007-05-03
Yup try audacity, then go to preferences under the edit menu. the first tab is your input device. Make sure that your mic is defined in the recording section >.>. Then just push record. Should work.

---

### Post by John Fraser on 2007-05-03
Thanks for that. I've installed Audacity, and that confirms that I'm not getting anything through the mic. I'll carry on playing with settings in System>Preferences>Sound, as well as re-checking all the connections.

---

### Post by John Fraser on 2007-05-03
Audacity isn't getting anything through the mic. I've looked in Alsamixer, and the only capture device is called Capture.... there is an entry for Mic, but with nothing there. 

I'm stumped.

---

### Post by starcraft.man on 2007-05-03
Well, you got me, I'm no audio recorder..... ummm, anyone who does a podcast/recording here to the rescue...

---

### Post by brien on 2007-05-03
i'm having the same problems. the weirdest part is that i *know* my mic works fine, because i can use it with lingot (instrument tuner) which is able to "hear" the mic. however, no matter how i try to record sound from the mic, i can't get it to work. i've tried Sound Recorder, Audacity, and <shudder>Krecord</shudder>

another thing i've noticed is that if i select "Microphone" from the input drop-down, it will revert back to "Capture" as soon as i click record. if i run via terminal, i get some output that may help:

i open gnome-sound-recorder, then click record, using the default "Capture" as the input. "file length" counts up until i hit stop, but nothing records. if i then change input to "Microphone", this error spits out in the term window:

[FONT="Courier New"]** (gnome-sound-recorder:7613): CRITICAL **: gst_alsasrc_mixer_list_tracks: assertion `this->mixer != NULL' failed[/FONT]

if i try to save, i get the "Invalid Parameters" dialog, and this in the term:

[FONT="Courier New"](gnome-sound-recorder:7613): libgnomevfs-CRITICAL **: gnome_vfs_get_file_info_uri_cancellable: assertion `uri != NULL' failed

(gnome-sound-recorder:7613): libgnomevfs-CRITICAL **: gnome_vfs_uri_unref: assertion `uri != NULL' failed[/FONT]

---

### Post by brien on 2007-05-03
well, i have Audacity recording now (nothing else is though) but the recording is really really crappy quality (listen to the attached ogg file of me snapping my fingers)

to get this far in audacity i went to: Edit >> Preferences >> Audio I/O >> Recording and then set device to "OSS: /dev/dsp"

another note: Audacity isn't able to play the recorded audio, i have to save it and then open it in a different program (been using Totem)

more clues: when i open krecord from command line i get:

[FONT="Courier New"]brien@stickerbox:~$ krecord 
[COLOR="Red"]X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/COLOR]
[/FONT]

---

### Post by brien on 2007-05-03
hmm, looks like krecord is actually recording, it's just that i have to be *really* loud on my mic. the quality is the same crappyness of the above attached file. :(

---

### Post by haylocki on 2007-05-04
Have you Tried turning on the "Mic Boost (+20 dB)" option in Gnome alsa mixer ?

Didn't work for me, but hey you never know.......

Also there are two commands for recording and playing audio that are installed as default :

arecord and aplay

You could try these. No they don't work for me on my laptop, ho hum......

If you "sudo apt-get install sox" you also have a command called rec. 

And no, it doesn't work on my laptop.

I'm sure I have a mixer settings problem, just don't know how to fix it.

But maybe one of the above programs will work for you.


Cheers, Ian

---

### Post by Jonam on 2007-05-04
When I started to use Audacity, I found that my microphone would not record even though I could hear it on the speakers if I tapped on it. After much fiddling, I found that using the Volume Control panel on the Capture tab, I had to not only enable the microphone but the capture sliders in the same panel. Then everything worked fine. I have a Sounblaster Live! card.

Jonam

---

### Post by haylocki on 2007-05-04
Just found this thread :
[http://ubuntuforums.org/showthread.php?t=141616&highlight=thinkpad+record](http://ubuntuforums.org/showthread.php?t=141616&highlight=thinkpad+record)

It's about Thinkpad T20 audio, but may help as I can now record using :

arecord -D plughw:0,0 ~/test.wav

and playback using :

 aplay ~/test.wav

I've attached a snapshot of my mixer settings, maybe they will help someone

That's my Thinkpad T21 working, now for the Thinkpad 770ED, which is the one I actually need sound recording on.......

Cheers, Ian

---

### Post by msiner on 2007-05-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/92879](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/92879) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It sounds like you have encountered a known bug currently in GNOME Sound Recorder.  The current work-around is that the "Save as" button should still work.  So you can save the recorded audio to a new file and then play that using Totem.

[http://bugzilla.gnome.org/show_bug.cgi?id=430101](http://bugzilla.gnome.org/show_bug.cgi?id=430101)

---

### Post by cvmostert on 2007-05-05
> **John Fraser said:**
> It's been a week now since I installed Feisty, and everything has been great. A most trouble-free installation for a non-techy. I'm now trying to get the bells and whistles working!

I can play back audio and video with no problems.
I cannot record anything with my microphone, which I have tested on a Windows machine. It's working fine.

I'm trying to record my voice as a test, using Sound Recorder. I am checking Microphone on the first screen, and have tried recording as wav, mp3, and ogg. 

I record for a few seconds, then stop and save. I then get an error message: Could not save the file "Invalid Parameters". Quitting Sound Recorder then gives me another save option, which seems to work, and the sound file is saved to my home folder. On playback this is silent.

I have tried playing around with settings in System>Preferences>Sound, and in Alsamixer, and am now completely confused!!

Is there a kind soul out there who could mentor me through this problem, please?

All help greatly appreciated!

I can record with > audacity.. but not with > sound recorder... 

I get the same error message you do when trying to save.
so there must be something else wrong...
EDIT: after looking at the bug... there was/ is something wrong... hope it get fixed soon... cheers

---

