---
title: "All is well, except for Sound"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by KB8GT on 2005-07-22
I have had Ubunto Linux now for about a week.  All is going well, No problem doing the Add-On Applications from the "Unofficial Ubuntu 5.04 Starter Guide".  With that Guide and search of this fine Forum all has gone well. Thanks Gang for the outstanding help. I can even view Movies in two different programs -- the major problem is No Sound.

I have tried the 'fix' from the above Guide and other postings here.  All have the same results - still no sound.  What hurts the most is that I have the Ubunto Live Disk, and the sound works great when using Live System. I can play audio CD's and have sound when signing on.  Thus, I do not think  that it is a hardware problem, cause sound is OK with the Live disk.

Have no idea what might be going on in the Ramdisk within Ubundo Live, but sure would like to have it on the hard drive with Ubundo Install.

Sorry that I do not have any specifics as to error messages - there is just plain - no sound.

I am at a loss, looking of help.

Thank You
Larry

---

### Post by manicka on 2005-07-22
Have you checked that the volume levels aren't muted in the volume control panel?

---

### Post by GavinX on 2005-07-22
Please give some idea as to the type of soundcard that you're using. Details, details. It really helps.

---

### Post by manicka on 2005-07-22
Yes, there have been some problems when there  is 2 soundcards on a system

---

### Post by KB8GT on 2005-07-22
Yes, I have checked the volume controls.  They are open and set for maximun.

The Computer is a Dell Dimension 4550
Planar Motherboard with Audio and Video on the board.

Windows Device Manager lists the card as:  Soundmax Integrated Digital Audio

I have the Knoppix 3.9 'live disk'  upon boot that system detects the Sound Card as:  
Intel Corp 182801DB AC'97 Audio Controller  driver=i810_audio

The only sound card installed is that on the motherboard.

Both Knoppix 3.9 and Ubundo 5.04 Live have sound

Hope this information helps.

Thank You
Larry

---

### Post by KB8GT on 2005-07-22
Additiona information;   From 'lsmod | grep snd'

snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

Hope this may be of help - several have asked for this info in other posts.

Thank You
Larry

---

### Post by manicka on 2005-07-23
Looks like a fairly standard sound card. Have you tried using a different default output sink in

System --> Preferences --> Multimedia Systems Selector

---

### Post by KB8GT on 2005-07-23
For ALSA, ESD, and OSS the marker went side to side during test - no sound, IF one was to be produced.

For Artsd and Custom - Failed to contruct pipeline

The Current setting for both defaut sink and output is ALSA

Hope this helps more along the way.

Thank You 
Larry

---

### Post by manicka on 2005-07-23
[QUOTE=KB8GT]For ALSA, ESD, and OSS the marker went side to side during test - no sound, IF one was to be produced.[/QUOTE]
The side to side marker means it's working and you're supposed to hear a  sound.

I'm stumped, anyone else?

---

### Post by KB8GT on 2005-07-23
More Information - Strange things.

Under Applications -> Sound & Volume -> Volume Control
The speaker at the bottome is not red x'ed and volume slider set to minimum.  

In the upper right corner (forget the name of the bar) the speaker is red'xed and slider is at maximum.  When the 'speaker' is opened it shows 'mute'.  Attempts to 'open the Volume Control' fails with a 'snap back to mute'

Under Preferences the setting is: Intel 82801DB - ICI-14 (Alsa mixer)

Thus, it does appear that we have a 'volume control problem' - one on and one off and the one in the upper right corner  prefers to stay in 'mute'.

Hope this might help some more.

Thank You
Larry

---

### Post by manicka on 2005-07-23
[QUOTE=KB8GT]More Information - Strange things.
In the upper right corner (forget the name of the bar) the speaker is red'xed and slider is at maximum.  When the 'speaker' is opened it shows 'mute'.  
[/QUOTE]
 You're sound is muted. Right click on the volume icon and choose 'Open Volume Control'. 
You'll see the red x on the speaker volume. Click on the 'x' and it should disappear. 
Make sure PCM is not muted as well. I leave PCm at about 70% as sound becomes garbled at a  higher setting

---

### Post by KB8GT on 2005-07-23
The volume controls are in sync now.  I can turn the mute on or off.  The PCM is set around 70%.  Tests were redone this morning.  The bars still slide back and forth - still  no sound.

Do believe I will go back to the "Unofficial Ubuntu 5.04 Starters Guide" and redo  the sound fix there.  Of course, I will not have to download the packages, cause that was done last time.  Perhaps I made an error in setting up one or more of the config files.

Sure would like to know the difference between the  system intialization of the 'live disk' and the installed system.  What ever the 'live disk' does during the boot up process -- well, it works.  

Will keep trying

Thank You 
Larry

---

### Post by black hole sun on 2005-07-23
[QUOTE=KB8GT]The volume controls are in sync now.  I can turn the mute on or off.  The PCM is set around 70%.  Tests were redone this morning.  The bars still slide back and forth - still  no sound.

Do believe I will go back to the "Unofficial Ubuntu 5.04 Starters Guide" and redo  the sound fix there.  Of course, I will not have to download the packages, cause that was done last time.  Perhaps I made an error in setting up one or more of the config files.

Sure would like to know the difference between the  system intialization of the 'live disk' and the installed system.  What ever the 'live disk' does during the boot up process -- well, it works.  

Will keep trying

Thank You 
Larry[/QUOTE]
 Run alsamixer in the console. Switch all of the bars there to "Analog" by pressing "m" on each one. This is most likely your problem.

---

### Post by GrootBrak on 2005-07-23
I am also not getting sound. I've checked with:
 
smod|grep snd and only get my command prompt back.

System>Preferences>Multimedia system selector all. All audio and video test give me the same "Failed to open test pipeline.

Volume control gives me "no mixer elements and or devices found."

I had the same problem in Warty, now I've upgraded to Hoary, but nothing. In Hoary however, as soon as I get my desktop, I get about 8 or so windows complaining about one or other Xwindows system. Those that know will recall my very first posts was complaining about Xwindows. 

The only sound I hear is a very loud beep when I make a typo. Usually scares the crap out of me cause its so darn quite around here. Not even audio CD's makes a sound. Would be gratefull for help.

---

### Post by KB8GT on 2005-07-23
[QUOTE=black hole sun]Run alsamixer in the console. Switch all of the bars there to "Analog" by pressing "m" on each one. This is most likely your problem.[/QUOTE]
Pressing 'm' only changed the "on" or "off'' status of each item.

The dialog box showed:

Card: Intel 82801DB-ICH4
Chip: Analog Devices AD1981A
View: Playback
Item: 'name' and either blank or [off] - controled by pressing 'm' - blank is assumed to be 'on'.

All were set to blank that is not [off] - computer was restared - still no sound.

I have not yet redone the procedure in "Unofficial Ubundo 5.04 Starter Guide" -- off to give that a rego.   All items in the 'alsamixer' remain 'on'.

Thank you for the help
Larry

---

### Post by KB8GT on 2005-07-23
The procedures in 'How to configure sound to work properly in GNOME'  part of "Unofficial Ubundo 5.04 Starter Guide"  has been redone.

Still no sound - the computer was restarted after completion of the instructions.

If sound  works in the Ubundo 'live' disk it should work from the 'Install' disk.  Wish I had the skill to find out what might be hidden in the compressed files of the 'live' disk.

Have not given up hope.

Thanks all for the help
Larry.

---

### Post by auburn on 2005-07-23
well, this thread got my sound working!!! I'm so pleased. It's odd. It just suddenly starting after I went through the mutting and unmutting of each item, one by one in alsamixer. I swear not one said it was muted. My gnome Volume Control does not work....until I pulled down the volume in xmms and suddenly PCM became muted. Pulling the volume back up in xmms, did not unmute it either. I had to go to Volume Control and unclick PCM mute. PCM mute is the only thing that works with the gnome Volume Control. Well, thanks for starting the thread, and good luck!

---

### Post by KB8GT on 2005-07-23
Thanks Gang we now have Ubundo Sound in Grayling Michigan.

I went looking for what auburn ment by 'xmms' - could not really find it, but I must have hit some 'unknown'  button.   We have sound.

Though weak, I had to turn up the computer speaker amplifier  volume.

Volume can be controled and muted as need be from Applications --> Sound & Video --> Volume Control.

The little speaker in the upper right hand corner of the screen is red'xd and when attemts are made to 'Open Volume Control' is snaps back to mute.  The volume slider there has no effect.  

Perhaps, we have had sound before, at times,  but the volume on the amplifier in the computer speakers was set to low.    Will have to remember to turn down the Windows volume sliders  - otherwise the Windows sound will knock me out of the room.

Again gang thanks for the help.

Oh by the way auburn where is 'xmms' ?

Larry

---

### Post by manicka on 2005-07-23
xmms is multimedia audio software and is much like winamp in the windows world (but better of course ;) ). 

It should have been installed by default and be availbale in Applications--> Sound & Video -->XMMS

---

### Post by KB8GT on 2005-07-23
Glad to know what XMMS is.  Now I feel deprived, I do not have it - oh well.

I have been able to find more output to the speakers.  Have no reason why.  I added some more output devices to the display of the applications volume control (Preferences).  The master has little effect on volume,  For some reason the 'head phones' acts like a master control -- do not ask me why.  Anyhow, now I can put headphones at half slider, turn down the speaker amplifier and do fine control with PCM. 

All is working good.  Hate to shut it down, cause it may not come back.

Thanks again all for the help

Larry

---

### Post by GrootBrak on 2005-07-24
Lucky you for gettin sound. I followed the Guide's instructions to the letter. Rebooted. Nothing. Set my Bios to not detect sound. Rebooted. Nothing.
Set Bios to detect sound. Rebooted. Nothing.

Alsamixer won't open. Gnome mixer won't open. Volume control won't open. All giving me "no mixer elements or devices found." Alsaplayer show's its playing, but I can do what I like, it won't make a peep.

---

### Post by auburn on 2005-07-25
good news about the sound Larry. I'm surprised you dont' have xmms. Btw, I like it best because most old-school winamp themes work with it. Just put the theme in the right folder and off you go. And winamp has sooooo many themes.

---

### Post by poofyhairguy on 2005-07-25
I personally like Muine more than xmms.

---

### Post by auburn on 2005-08-02
I found when my sound broke again, that I actually had to turn ***ON*** the mute for one item: my IEC958 Capture Monitor. Weird. My alsamixer looks like below for this item:

 &#9474; Card: VIA 8237 
    Chip: C-Media Electronics CMI9761          
    View: Playback           
 &#9474; Item: IEC958 Capture Monitor [Off]

---

### Post by beefsprocket on 2005-08-24
What about comparing your lsmod, lspci, and dmesg on both LiveCD and your installed 5.04? 

See what the difference(s) is/are and work from there.

---

### Post by gushy on 2005-08-25
> **auburn]I found when my sound broke again, that I actually had to turn ***ON*** the mute for one item: my IEC958 Capture Monitor. Weird. My alsamixer looks like below for this item:

 &#9474 said:**
> 


That did the trick for me with the same on-board, my volume controls don't seem to work but hye at least Ihave sound, and there's a volume knob on the speakers. :)

---

### Post by grnwood on 2006-03-08
Well,

At one point i had sound working in DSP, MPlayer, etc.  but it never worked from GNOME.  

I had the ubuntu bongos at first until i made some changes.

I noticed that I have Intel AC'97 and all cards are picked up.

I had to add a startup script to my /etc/rcS.d which did:

chmod 666 /dev/dsp
chmod 666 /dev/snd/*

Which then allowed my 'volume control' to not have the red X.  I can switch multimedia providers and both ALSA, and OSS get the bars going left and right ... .but NO SOUND whatsoever.  Everything is unmuted.

Trying some other stuff.....

---

