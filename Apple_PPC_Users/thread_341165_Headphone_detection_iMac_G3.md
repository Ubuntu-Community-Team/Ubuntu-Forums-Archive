---
title: "Headphone detection iMac G3"
date: 2007-01-18
forum: Apple PPC Users
---

### Post by samden on 2007-01-18
I have had this topic running in 'General' with little response, it may be mac-specific so I have posted it here now.

I would like to listen to music in the office on my G3 iMac running Xubuntu dapper. However when I plug in the headphones, the main speakers do not mute. They keep playing as well, so both my main speakers and my headphones are making noise.

The Xubuntu sound control panel doesn't seem to do anything either - it just consists of a list of tick boxes saying whether to use certain extensions, it doesn't even have a volume control. 'Headphone detection' is on according to this.

I have added the "volume control" button to the panel. Whenever I open this, 'Headphone detection' is turned off. I can turn in on, but the headphones are still not detected. When I close the volume control window and turn it back on, 'Headphone detection' is always turned off again.

Can I edit this directly through the terminal to ensure headphone detection is on and check whether or not it works? 

This is not a hardware problem - I dual-boot with OSX and it works fine in OSX.

Any suggestions? Can I edit something in the terminal? Is there a better sound control panel I could use?

---

### Post by linear on 2007-01-18
ALSA sound is broken when it comes to iMac G3's; see the [item here]("http://wiki.debian.org/?PowerpcSoundcards"). I haven't heard of a fix.

---

### Post by bfor75 on 2007-01-18
Have your tried running alsamixer from the terminal?  If you use the arrow keys to select the "headphone" control you can then toggle autodetection of headphones with the "m" key.  I suspect that this will not work either, given Linear's post, but you could try if you want.

---

### Post by linear on 2007-01-18
I've tried it - doesn't work.

---

### Post by bfor75 on 2007-01-22
I think I may have a different version of iMac G3 than you do (I have a screamer sound card), but when I plug my headphones into the line out jack on the side instead of the headphones jack on the front ubuntu correctly detects them and mutes the speakers.  I also have gnome ubuntu installed in addition to xubuntu, but I don't know if this makes any difference.

---

### Post by linear on 2007-01-22
Interesting. On my iMac G3 (500MHz slot-loading) the front and side jacks both don't work. (Also using Gnome.)

---

### Post by samden on 2007-01-29
Thanks for the information. Unfortunately plugging into the side jack doesn't do anything for me - still plays out both the main speakers and the headphones.

No luck with alsamixer - can turn on headphone detection but it turns off again as soon as I close alsamixer. Even with alsamixer open and headphone detection turned on it doesn't seem to make any difference. Same observation as linear has made.

My computer is also a 500Mhz iMac G3 slot loader. It does have a PowerMac Screamer card. I have xubuntu only installed but doubt this makes any difference.

It is odd, the volume appears to change for the main speakers and the headphones at the same time - turn one up and the other goes up too, mute the speakers and the headphones mute as well.

Thanks for the information, it is good to know I am not alone and alsa sound won't work, will save me fussing with trying to get it working any longer. It is a pity though, I will have to work in OSX when I want to silently listen to music.

---

### Post by t_rex on 2007-12-28
I've got the same machine with the same problem and I SOLVED IT.

Usually at the point of giving up I start acting like a baby and do stupid things like plugging just to know what happens. And this time it helped. I plugged the headphone into the microphone jack (you shouldn't do that) and recognized that something happened at the mixer. So I plugged the headphone into the side jack (front won't work) and plugged a microphone into the mic jack and IT WORKED. It is the MIC JACK that disables the speakers (and also the front headphones). Funny, isn't it?

Now, with the mic plugged in I can enable/disable the checkbox for headphone detecting and the Speakers and headphones are seperately adjustable (speakers with the "PC Speaker" control, headphones with "Master" control).

Hope it helps - plug 'n' pray!

System: G3 500 MHz, screamer, unbuntu 7.04, Kernel 2.6.21.1-realtime

---

### Post by samden on 2008-01-03
That's really interesting! I gave up on that machine a while back now myself as I became convinced there is something wrong with the hardware - applications keep crashing whether running Xubuntu or OS X Panther, even with a large RAM upgrade. Now I just let my wife potter away with it running OS X (and complain to me about it every few days, soon I will get a better computer set up for her!).

But I expect this will be really useful for someone else, and possibly myself if I get another one of these old iMacs someday, they are pretty common.

Thanks for posting this really wacky hack!

---

### Post by ristosu on 2008-03-25
I've been trying to fix the ALSA driver for powermac and achieved some results. The Burgundy sound chip based machines (PowerMac G3 B&#38;W and iMac G3 Tray-loading) are ok, the Screamer based (PowerMac G3 Beige and iMac G3 Slot-loading) almost. On the latter the remaining problem is CD playback and capture. It seems that I cannot find the correct input.

The Slot-loading CD drive is connected to the motherboard with only one 50-pin cable which holds the data, audio, and power. How the audio is routed to the Screamer chip, I have no information of. But it is not on the usual input. If anyone has succeeded in playing audio CD's - without a program that reads the data directly in digital form - or has any other knowledge about this, I would be very glad to hear about it.

And if you are interested in testing my results - thus increasing the number of tested platforms - I could make instructions for building new ALSA drivers with my patches included...

---

### Post by stream303 on 2008-03-27
I can relate to some of these problems!

I had an old Dell Optiplex that for some reason, the line and headphone jacks were reversed - drove me nuts.

You may want to download "alsamixergui" - sometimes it can be a bit more friendly than the terminal-based app.

---

### Post by Phonan on 2008-06-30
Sorry- kind of old thread. I have a Screamer card and right now everything is working well CD wise, except that for some strange reason my audio CDs never show up in Thunar; the only way to eject is running an "eject /dev/hdb" By the way, I used VLC a bit to play CDs, but it's not really VLC's forte, so I'm currently using Decibel Audio Player. No problems with CD playing, though some programs haven't worked for me, like Grip.

I also have problems with audio in that my speakers won't go down below a certain volume threshold. I can have Master & PC Speakers at 0 and still get loud sound. I have to mute PC Speakers to get them to be quiet. I get a full range of sound on headphones, though. It's a strange problem.

Anyway, I'm quite late but I hope this helps.

---

### Post by stream303 on 2008-07-01
> **Phonan said:**
> I also have problems with audio in that my speakers won't go down below a certain volume threshold. I can have Master & PC Speakers at 0 and still get loud sound. I have to mute PC Speakers to get them to be quiet.

Do you have a PCM setting?  You might want to enable that level setting, or you can use alsamixer in a terminal and adjust it that way.  Most PCM levels that I've seen are really cranked most of the time.

---

