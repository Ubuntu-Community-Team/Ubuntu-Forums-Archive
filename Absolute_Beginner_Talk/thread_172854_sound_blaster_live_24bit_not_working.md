---
title: "sound blaster live 24bit not working"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by tj54020 on 2006-05-09
Hello everyone, im new to linux and ive got everything installed and working the way i want it to so i can learn more about it, except i am having trouble getting my sound card to work.  it is a soundblaster live 24 bit sound card.  i believe this link is a link to someone getting theirs to work [http://www.ubuntuforums.org/showthread.php?t=19307](http://www.ubuntuforums.org/showthread.php?t=19307) , but i dont have any clue wahts going on in the instructions... like i said im completely new to it... i have limited programming knowledge with just a semester of C++ and a semester of M/s Vb.Net  if someone could give me a better idea of what to do next i would appreciate it.

Im running ubuntu 5.10 with all updates installed
i have onboard audio turned off in the bios 
my sound card is detected in device manager on 82801 pci bridge as "sb audigy ls"  but capabilities and device type are unknown. 
can anyone help???

i read in another post that this might help so im posting it as well(if it doesnt help no harm done) :
tommy@ubuntuTJ:~$ sudo lspci |grep -i audio
Password:
0000:01:00.0 Multimedia audio controller: Creative Labs SB Audigy LS
tommy@ubuntuTJ:~$

---

### Post by deadgobby on 2006-05-10
Have you installed alsa mixer from your synaptic? Once you install alsa mixer. Open up your terminal and type in alsamixer. You will get a crude display, but effective one. the left and right arrows keys got to analogc and so on. The up and down controls the volume levels. I have SB live and had to install the alsa mixer. After that install the card works like a champ. You can use Audacity to record off you SB live card too. 
 Hope this helps

---

### Post by tj54020 on 2006-05-10
im not sure how to install the updated alsa, i have the prepackaged alsa and i can get into the mixer i did read somwhere that it needs to be updated to work with sb live, the problem is i dont know how to update it, i have tired following some instructions i found but they were a little to complicated since im a noob to linux.

thanks for the reply

---

### Post by CybaCowboy on 2006-05-10
I have a Sound Blaster Live!, I'm not sure which specific model, but Device Manager identifies it as SB Live! EMU10k1 (there's also "SB Live! MIDI/Game Port" and "Sound Controller")...

Anyway, *my* sound also does not work and In installed "Alsa Mixer" as you said to, yet this does not solve my problem!

---

### Post by deadgobby on 2006-05-10
Try this and see if finds your type of sound card.
From the terminal:

lspci | grep audio

Here are some links to trouble shoot your problem. I hope one of them are you cure.
[https://wiki.ubuntu.com/DebuggingSou...ht=%28sound%29](https://wiki.ubuntu.com/DebuggingSou...ht=%28sound%29)
[http://ubuntuforums.org/showthread.p...ighlight=sound](http://ubuntuforums.org/showthread.p...ighlight=sound)
[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)
[https://wiki.ubuntu.com/?action=full...&titlese](https://wiki.ubuntu.com/?action=full...&titlese) arch
[http://ubuntuforums.org/showthread.php?t=44753&highlight=soundblaster+live](http://ubuntuforums.org/showthread.php?t=44753&highlight=soundblaster+live)
[http://ubuntuforums.org/showthread.php?t=37082&highlight=soundblaster+live](http://ubuntuforums.org/showthread.php?t=37082&highlight=soundblaster+live)

---

### Post by steve.horsley on 2006-05-10
Do you have onboard sound controller too? My previous PC had both onboard sound and also SB Live card. It always defaulted to using the onboard controller.  Go System->Preferences->Sound and check the default sound controller.

---

### Post by CybaCowboy on 2006-05-10
[QUOTE=steve.horsley]Do you have onboard sound controller too? My previous PC had both onboard sound and also SB Live card. It always defaulted to using the onboard controller.  Go System->Preferences->Sound and check the default sound controller.[/QUOTE]

Yep, that was the problem...

Ubuntu was defaulting to the ob-board sound card.

---

### Post by rodrigo666 on 2006-05-26
I have a Sound Blaster Live and I do have sound. But I'd like to control the volume of each one of the 5.1 channels as I do in Windows.

(For instance, to raise the rear channels, lower the center channels, do some crossover, that sort of things)

There is a way do to that?

---

### Post by se7ensamurai on 2006-05-26
to answer the above question, the basic sound mixer built in (or the ALSAMixer from the prompt) can handle all channels (except the bass? for some reason) with the SB Live 24 card...I can use it with DVDs and video files I've downloaded...

I have a different problem though, and I'm wondering if its the card or my codecs.

I can play DVDs, and video files, and get sound (5.1 even!), but for some reason I'm unable to play MP3s. I checked ALSA, and everything should be working. Whats really weird is that Rythmbox seems to go through the files at double speed while not giving any sound output. amaroK looks like everything is fine, but again, no sound output. Any suggestions?

---

### Post by Sutekh on 2006-05-26
[quote=rodrigo666]I have a Sound Blaster Live and I do have sound. But I'd like to control the volume of each one of the 5.1 channels as I do in Windows.

(For instance, to raise the rear channels, lower the center channels, do some crossover, that sort of things)

There is a way do to that?[/quote] 
Yes.  You will need a custom .asoundrc file to route sound to each channel.  Then the alsamixer can change the volume of the differnet channels.  Crossover/mixing I'm not so sure.

Do you currently have 5.1 sound, or just 2.0 (stereo) sound?  Try the alsamixer as suggested.

[quote=se7ensamurai]to answer the above question, the basic sound mixer built in (or the ALSAMixer from the prompt) can handle all channels (except the bass? for some reason) with the SB Live 24 card...I can use it with DVDs and video files I've downloaded...
[/quote]On my SB Live 24 bit card the bass is part of the centre channel.  

My centre speaker is the left side of the centre channel and my subwoofer the right side. I use Q/Z to control the left channel and E/C to control the right.

[quote=se7ensamurai]
I have a different problem though, and I'm wondering if its the card or my codecs.

I can play DVDs, and video files, and get sound (5.1 even!), but for some reason I'm unable to play MP3s. I checked ALSA, and everything should be working. Whats really weird is that Rythmbox seems to go through the files at double speed while not giving any sound output. amaroK looks like everything is fine, but again, no sound output. Any suggestions?[/quote] Could be MP3 codecs.  Have you ever had MP3's playing correctly?

Do you have the gstreamer0.8-mad package installed, if using Breezy?

Do you have the gstreamer0.10-plugins-ugly package installed, if using Dapper?

---

### Post by se7ensamurai on 2006-05-26
I believe I have all the proper MP3 codecs...

just now I realized that _none_ of my sound was working, so I rebooted to double check and now I have nothing. It must be something that happened since last night. (I was watching a Dr Who episode, and a couple of Highlander episodes.) now not even the system sounds are working. I'm going to have to do some digging here. I must have missed something really stupid and obvious! (entirely possible) thanks for the quick response though.

- Update:I re-installed Gstreamer, and still nothing.

---

### Post by Sutekh on 2006-05-27
So no system sounds?

Are all the sound channels unmuted? (I'm sure you checked this though, but had to ask)

Are your sound modules loaded?
```
lsmod | grep snd
```

---

### Post by se7ensamurai on 2006-05-28
hehe, sorry, I have no idea what any of this means:
> se7ensamurai@monkeybusiness:~$ lsmod | grep snd
snd_ca0106             27172  3
snd_ac97_codec         72188  1 snd_ca0106
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  2 snd_ca0106,snd_pcm
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_rawmidi            22816  1 snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m idi_event
snd_timer              21764  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmi di,snd_seq
snd                    48644  14 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer _oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  2 snd


but I'll tell you, I just figured out tonight that its not just the sound. videos won't play either. MPlayer just hangs, VLC and Totem just open and close right away.

I'm thinking it was the last update I installed. I had been watching some videos, ran the update before bed, didn't shut down, and next day nothing worked (at least thats how I remember it). Is there a way to roll back to before the previous update? probably not without a lot of digging and work though, right?

---

### Post by se7ensamurai on 2006-06-04
this is totally bumming me out.
I've tried installing Xine, updating codecs, etc.
When I try to play anything in Xine it still just skips through the tracks. I'm at a total loss here.
I upgraded to 6.06 the other day and nothing. 
:confused: 
totally bummed

---

### Post by mmtowns on 2006-12-27
I have the same issue: SB Live with strange sound every hall second or so from the speakers.  Any suggestions?

---

