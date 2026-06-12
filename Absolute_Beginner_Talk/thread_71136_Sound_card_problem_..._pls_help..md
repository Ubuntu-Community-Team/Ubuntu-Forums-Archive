---
title: "Sound card problem ... pls help."
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by Frasir on 2005-10-02
Hi,

I'm a new convert to Ubuntu from Windows XP:

I've installed the 5.04 and followed the instruction on the Starter Guide, but my sound card is not working.

There is an on-board sound card by VIA, but it is not working - since Windows XP time. So I bought a Sound Blaster Live 5.1 and it's working under Windows XP. 

Performed "lspci | grep audio" in Terminal and result:
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:10.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

Please help me to rectify.

Thanks very much!!!

Frasir - SG

---

### Post by swerner on 2005-10-02
[QUOTE=Frasir]Hi,

I'm a new convert to Ubuntu from Windows XP:

I've installed the 5.04 and followed the instruction on the Starter Guide, but my sound card is not working.

There is an on-board sound card by VIA, but it is not working - since Windows XP time. So I bought a Sound Blaster Live 5.1 and it's working under Windows XP. 

Performed "lspci | grep audio" in Terminal and result:
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:10.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

Please help me to rectify.

Thanks very much!!!

Frasir - SG[/QUOTE]
Do you have any sound card devices listed under Applications > Sound & Video > Volume Control > File > Change Device? 
What do you get when you run the command 'lsmod |grep snd'?

---

### Post by Frasir on 2005-10-03
[QUOTE=swerner]Do you have any sound card devices listed under Applications > Sound & Video > Volume Control > File > Change Device? 
What do you get when you run the command 'lsmod |grep snd'?[/QUOTE]

Hi,

Yes, the devices are listed and I've selected "Sound Blaster Live! (Alsa Mixer)".

Here is the result of 'lsmod | grep snd':
snd_emu10k1            81668  0
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9220  1 snd_emu10k1
snd_via82xx            25248  3
snd_ac97_codec         64608  2 snd_emu10k1,snd_via82xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  5 snd_emu10k1,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  2 snd_pcm
snd_page_alloc          9604  3 snd_emu10k1,snd_via82xx,snd_pcm
gameport                4608  2 emu10k1_gp,snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  2 snd_emu10k1,snd_mpu401_uart
snd_seq_device          8332  2 snd_emu10k1,snd_rawmidi
snd                    50276  13 snd_emu10k1,snd_hwdep,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  2 snd

But still no sound :( 

Last time I hit problem, I switch back to MS Windows. This time round I'm determine to make it work.

Please help me. Thanks

---

### Post by Unreal Sorcerer on 2005-10-03
try typing in alsa mixer into the terminal and make sure that everything is on or up.... also, if that doesn't work, try going to the volume control and go to edit > preferences and look for an audigy analog / digital output jack and check it.

---

### Post by ProPilot on 2005-10-03
Also make sure your sound is unmuted.

---

### Post by swerner on 2005-10-03
> But still no sound

Last time I hit problem, I switch back to MS Windows. This time round I'm determine to make it work.


Ok, it seems like both your sound card devices were found.  The command 'lsmod | grep snd'  that you typed will show all the sound devices that were found in your system.  The only other thing I can suggest is that you make sure you have not muted any of the channels, go to System > Preferences > Sound and select the SBLive. Then make sure both fields in that tab are ticked.  Then go to the sound events tab and try playing a sound.  If this fails, go to Applications > Sound & Video > Volume Control  and make sure none of the input channels are muted and that the volume is up.

---

### Post by Mustard on 2005-10-03
Do you need both sound devices installed at once?

I'd be tempted to disable the AC97 onboard sound, and stick to using the SoundBlaster.

I'm also curious whether you have read and tried the Unofficial guide on fixing sound in Gnome (I'm assuming your using gnome).

[Configuring sound to work properly on Gnome.]("http://ubuntuguide.org/#configuresoundproperly")

---

### Post by Frasir on 2005-10-04
This post reply to all who gave a suggestion ...

1. I'm certain non of my sound devices was muted.
2. Checked on every options suggested, still, no sound.
3. It was due to a hardware error that the on-board VIA AC97 can't produce any sound at all. So I bought the Sound Blaster Live! - That's during Windows XP time.

Guess I had my share of frustration in LINUX. I re-installed with Fedora 4 and everything works, including my scanner. WOW! 

But, it is sluggish even compare to Windows 2000 - WOW!

Seems like I don't have much choices.

---

### Post by qiezi! on 2005-10-04
This may or may not help, but my sound is the SB Live! 24bit, ah I had problems getting it working; followed HOWTO, guide, blah, blah, and setting the volume... everything was installed, lsmod showed what I wanted to see but no sound....

the first problem was I had to kill esd (see GNOME link from Mustard)... then I found that if the volume was turned up on channels other than front, and specifically S/PDIF, there was no sound... using alsamixer the only channel I unmuted was the front/centre channel and then I had sound... if your card has S/PDIF this may help... hope so, otherwise, sorry :(

---

### Post by Mustard on 2005-10-04
The Breezy Badger version of Ubuntu is out soon.  There are a lot of improvements in the sound area in Breezy.

---

### Post by thespinesplitter on 2005-10-04
maybe, but no fix will turn off on-board sound in BIOS, seriously folks when the hell will this reach a FAQ - all these sound doesnt work in ubuntu posts are the same problem, u can do a quick check by popping in a cd and connecting ur speakers to the onboard sound uotput also make sure u switch the media devices to ALSA in ubuntu for soundblaster

---

### Post by Frasir on 2005-10-05
[QUOTE=Mustard]The Breezy Badger version of Ubuntu is out soon.  There are a lot of improvements in the sound area in Breezy.[/QUOTE]

I just reverted back to Ubuntu again ... still no sound :(  Think I can bear with it and wait till the new version is out. Anyway, this PC is only for documentation only.

Thanks!

---

### Post by swerner on 2005-10-05
[QUOTE=Frasir]I just reverted back to Ubuntu again ... still no sound :(  Think I can bear with it and wait till the new version is out. Anyway, this PC is only for documentation only.
Thanks![/QUOTE]
It's a shame you didn't get Ubuntu working with your soundcard.  Breezy (the next version of Ubuntu) should be much better.  Give the prerelease a go, it's available at [http://cdimage.ubuntulinux.org/daily/current/](http://cdimage.ubuntulinux.org/daily/current/) .
I'm running it and it is very stable.

---

### Post by samus6151 on 2005-10-12
I recently formated my computer and now no sound! in the hardware, device manager it has a yellow icon next to Multimedia Audio Controller.
i have no idea what type of audio card it is!! can someone please help! t
thank you for ur time!!

Sam

---

### Post by Asraniel on 2005-10-12
same here, its nearly impossible to tell kubuntu to use the second soundcard as the default one. i could tell arts to use it, but not all applications use arts. please make it easier in the next release, in breezy there is no tool that could do that

---

