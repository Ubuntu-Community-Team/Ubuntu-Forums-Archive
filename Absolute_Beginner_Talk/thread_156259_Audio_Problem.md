---
title: "Audio Problem"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by Nightdog on 2006-04-06
Hello,

I'm a noobie at this. I recently installed Breezy on my old Toshiba Satellite 2545CDS laptop and I'm having a blast. The only problem has been the sound.

After much frustration I finally got the Yamaha opl3sa2 sound to play cd's, mp3's, ogg files, etc. (I got lucky!) However I'm not able to hear any sound coming from the internet or computer programs like games. I'm not able to hear any sounds coming from the system, either (ie sound files coming from file alerts, etc.) I'd also like to be able to record using the line in, but both Sound Recorder and Audacity don't seem to be working. Audacity doesn't seem recognize the soundcard and Sound Recorder tells me to run esd in a terminal, which I do, but it still doesn't record anything. 

To get my soundcard to work, I created a file in /etc/modprobe.d named "sound" with the following settings:

options snd-opl3sa2 index=0 id=CARD_0 port=0x370 sb_port=0x220 wss_port=0x530 midi_port=0x330 fm_port=0x388 irq=5 dma1=1 dma2=0 isapnp=0

When I boot up I do three commands: sudo update-modules; sudo modprobe snd-yamahaopl3sa2; and alsamixer

Am I missing something? Any help would be greatly appreciated! Maybe I'm just being too greedy by wanting to be able to record and hear system sounds?

---

### Post by Brightrock on 2006-04-06
I had some audio line-in problems in the Gnome desktop which seem to be mostly solved by going to KDE.  You can install the KDE desktop using Synaptics and just choose a KDE session at the login screen and give it a try.  It might work.

Good Luck,

Brightrock

---

### Post by Kapre on 2006-04-06
[QUOTE=Nightdog]Hello,

I'm a noobie at this. I recently installed Breezy on my old Toshiba Satellite 2545CDS laptop and I'm having a blast. The only problem has been the sound.

After much frustration I finally got the Yamaha opl3sa2 sound to play cd's, mp3's, ogg files, etc. (I got lucky!) However I'm not able to hear any sound coming from the internet or computer programs like games. I'm not able to hear any sounds coming from the system, either (ie sound files coming from file alerts, etc.) I'd also like to be able to record using the line in, but both Sound Recorder and Audacity don't seem to be working. Audacity doesn't seem recognize the soundcard and Sound Recorder tells me to run esd in a terminal, which I do, but it still doesn't record anything. 

To get my soundcard to work, I created a file in /etc/modprobe.d named "sound" with the following settings:

options snd-opl3sa2 index=0 id=CARD_0 port=0x370 sb_port=0x220 wss_port=0x530 midi_port=0x330 fm_port=0x388 irq=5 dma1=1 dma2=0 isapnp=0

When I boot up I do three commands: sudo update-modules; sudo modprobe snd-yamahaopl3sa2; and alsamixer

Am I missing something? Any help would be greatly appreciated! Maybe I'm just being too greedy by wanting to be able to record and hear system sounds?[/QUOTE]


Did you have a look at [Automatix]("http://ubuntuforums.org/showthread.php?t=138405")? Coz I think the problem with the web pages that doesn't produce the sound is because of the codecs not installed (properly).

K

---

### Post by squidward_tentacles on 2006-04-08
I am having the same problem with both Audacity not outputting any type of sound, and I have the same problem with not being able to hear audio from any type of web pages either.  I ran Automatix, and have system sounds/mp3 playback, etc.....but no web/Audacity capabilities. I love Ubuntu and have recently made the switch from windoze, this is about the only problem I have not yet been able to correct, any advice would be greatly appreciated](*,)

---

### Post by BoyOfDestiny on 2006-04-08
[QUOTE=squidward_tentacles]I am having the same problem with both Audacity not outputting any type of sound, and I have the same problem with not being able to hear audio from any type of web pages either.  I ran Automatix, and have system sounds/mp3 playback, etc.....but no web/Audacity capabilities. I love Ubuntu and have recently made the switch from windoze, this is about the only problem I have not yet been able to correct, any advice would be greatly appreciated](*,)[/QUOTE]

in a terminal type
sudo killall esd

see if that fixes it.

sudo apt-get install alsa-oss

is also useful

I've posted way too many times on it, I'm happy to say all my sound issues are resolved. If you want ESD out, just go to System -> Preferences -> Sound, uncheck the box enable sound server.

 If multiple apps accessing soundcard is still a problem (which it was on my laptop), you need to make an .asoundrc file (google dmix asoundrc and alsa... I'm using dapper, so not sure if this fix works on breezy etc)

---

### Post by squidward_tentacles on 2006-04-08
[QUOTE=BoyOfDestiny]Hi, this is for folks with an audigy running under Breezy (may work with other soundcards... feel free to add on to this thread if it does).

Here ya go, my first how-to here:

Using synaptic,
install alsa-oss and libsdl1.2debian-all

Next step (this one may be optional, I just hate the gnome sounds and ESD)

Go To System -> Preferences -> Sound
uncheck Enable Sound Server at start up and gnome system sounds

Next step
Go To System -> Preferences -> Multimedia Systems Selector

Set the default sink input and output to ALSA

If you did choose to not have esd, open up a terminal and type sudo killall esd. Or if you are more gui oriented log in and out of ubuntu.

Now, if you are lucky, open up xmms, fceu, beep, zsnes, dosbox, audio overload, vlc, etc etc. 

You should hear multiple sounds like nobody's business. Remember, if any of these apps were manually set to use ESD as default ouput, use their respective guis to set it to alsa or oss (only if alsa isn't an option).[/QUOTE]

Thanks for the advice, but none of the suggestions given either here or on the other post, have worked for me....The really frustrating part is that I have installed Ubuntu on another similar computer, and the sound in web pages, and Audacity is working just fine with the default install + Automatix < save for the fact that the one without sound, uses lilo vs grub due to BIOS issues>....any other tips to help a n00b out?

btw, I have even gone as far as removing sound card and trying complete reinstall with similar TB card to the one Turtle Beach card that works so beautifully on the other machine....I even tried a new Sound Blaster Audigy SE card, but with that one I couldnt get any type of sound save for static...As far as the google suggestions , the pages and links are innumerable, and Im kinda at a loss as to where to begin on Breezy....:-k

---

### Post by BoyOfDestiny on 2006-04-09
[QUOTE=squidward_tentacles]Thanks for the advice, but none of the suggestions given either here or on the other post, have worked for me....The really frustarting part is that I have installed Ubuntu on another similar copmputer, and the sound in web pages, and Audacity is working just fine with the default install + Automatix < save for the fact that the one without sound, uses lilo vs grub due to BIOS issues>....any other tips to help a n00b out?

btw, I have even gone as far as removing sound card and trying complete reinstall with similar TB card to the one Turtle Beach card that works so beautifully on the other machine....I even tried a new Sound Blaster Audigy SE card, but with that one I couldnt get any type of sound save for static...As far as the google suggestions , the pages and links are innumerable, and Im kinda at a loss as to where to begin on Brezzy....:-k[/QUOTE]

Hmm, bios updates are always a good thing... The only other problem I can think of (since you said swapping sound cards didn't help), is that it's trying  to use onboard sound (as the default instead of the card). Can you disable onboard sound in the bios or try System -> Preferences -> Sound, and try changing the default sound card.

Hope this helps you.

Good luck :)

---

### Post by squidward_tentacles on 2006-04-10
[QUOTE=BoyOfDestiny]Hmm, bios updates are always a good thing... The only other problem I can think of (since you said swapping sound cards didn't help), is that it's trying  to use onboard sound (as the default instead of the card). Can you disable onboard sound in the bios or try System -> Preferences -> Sound, and try changing the default sound card.

Hope this helps you.

Good luck :)[/QUOTE]
:D Excellant advice! That fixed the problem!! Disabling the onboard sound card thru the BIOS settings did the trick, and a restart afterwards restored system sounds as well, I now have sound in all applications, Thanks again for the help!

---

### Post by Enaid on 2006-09-29
> **Nightdog said:**
> Hello,

I'm a noobie at this. I recently installed Breezy on my old Toshiba Satellite 2545CDS laptop and I'm having a blast. The only problem has been the sound.


Hello Nightdog

I am most interested in installing Breezy Badger in an old 2545CDS Toshiba; that one is a basic model with only 32MB. I would like to upgrade it a bit to make Breezy Badger run on it more comfortably.

I would be obliged if you could quote the specifications your 2545CDS has at the moment. Particularly how much RAM and the size of the hard drive.

Thank you very much in advance.

Enaid

---

