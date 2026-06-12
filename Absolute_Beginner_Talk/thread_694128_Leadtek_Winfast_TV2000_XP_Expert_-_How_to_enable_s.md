---
title: "Leadtek Winfast TV2000 XP Expert - How to enable sound output"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by LeDechaine on 2008-02-11
Hi.

I'm using this TV card, card is working fine with the default config (card=5 tuner=43), but there is no sound coming from the PCI card AUX output, which connects right in my PCI audigy 2 sound card AUX2 input.

I was wondering if the sound of this output was muted by default, and if yes, what can I do to "unmute" it.

---

### Post by nikoPSK on 2008-02-11
goto:

```
alsamixer
```

and unmute as required.

---

### Post by LeDechaine on 2008-02-12
nah, the alsamixer is used to unmute **sound** card **inputs**, I want to enable the **TV** card **output**.

---

### Post by nikoPSK on 2008-02-12
> **LeDechaine said:**
> nah, the alsamixer is used to unmute **sound** card **inputs**, I want to enable the **TV** card **output**.

Yes, but the card shouldn't be muted in the first place, I think most aren't.

---

### Post by LeDechaine on 2008-02-12
Well, looks like mine is muted in linux for whatever reason, on windows it's ok, on linux it's muted, no sound coming from this.

So if anyone knows how to unmute this card in any possible way, let me know.
nikoPSK, man, you must not be the only one in the forum who has a winfast TV card! :D

---

### Post by nikoPSK on 2008-02-12
> **LeDechaine said:**
> Well, looks like mine is muted in linux for whatever reason, on windows it's ok, on linux it's muted, no sound coming from this.

So if anyone knows how to unmute this card in any possible way, let me know.
nikoPSK, man, you must not be the only one in the forum who has a winfast TV card! :D

I know, maybe under bttv?

---

### Post by Milos_SD on 2008-02-12
If you connected your tv card with CD input on your motherboard with that little cable, then just go in alsamixer and unmute CD mixer, and you are good to go. ;)

---

### Post by nikoPSK on 2008-02-12
> **Milos_SD said:**
> If you connected your tv card with CD input on your motherboard with that little cable, then just go in alsamixer and unmute CD mixer, and you are good to go. ;)

I conected mine to my audigy, so yeah. :)

---

### Post by LeDechaine on 2008-02-12
Well I connected mine to my audigy too :P
The problem is that the TV card doesn't seem to output any sound since everything is unmuted in alsamixer (maxed out even) and I don't hear anything.

I can hear sound under windows, but not under linux.

Gonna post this as a bug soon if i don't find answers..
The CX8800 module is already bugged and causing ksoftirqd to use 20% CPU usage anyway, so I won't be surprised if the reason why my card doesn't output sound is that the CX8800 module is scrapped..

---

### Post by Christmas on 2008-02-13
I should work. Under TVTime, Right Click -> Input Configuration -> Audio Volume Boost -> Full. Also control the volume from Left Arrow and Right Arrow. I have Leadtek TV2000XP Deluxe and it works very well.

---

### Post by nikoPSK on 2008-02-13
> **Christmas said:**
> I should work. Under TVTime, Right Click -> Input Configuration -> Audio Volume Boost -> Full. Also control the volume from Left Arrow and Right Arrow. I have Leadtek TV2000XP Deluxe and it works very well.

hehe, volumes at 0 par default.

---

### Post by LeDechaine on 2008-02-13
> **Christmas said:**
> I should work. Under TVTime, Right Click -> Input Configuration -> Audio Volume Boost -> Full. Also control the volume from Left Arrow and Right Arrow. I have Leadtek TV2000XP Deluxe and it works very well.

Already done that, sorry, no sound.
Already done..
```
v4lctl volume mute off
v4lctl volume 65535
```
..too, but no luck, still no sound.

And I know Winfast TV2000XP **Deluxe** card works under linux, heard many people saying this, but Winfast TV2000XP **Expert** card does NOT seem to work under linux (at least, here, mine doesn't output sound).

---

### Post by LeDechaine on 2008-02-13
> **nikoPSK said:**
> I know, maybe under bttv?

```
Card 34 in the bttv cardlist works for a variety of Leadtek cards, including the Winfast 2000, Winfast TV2000 XP, Winfast 2000, Winfast TV2000 XP Deluxe edition, Winfast TV2000 XP RM and Winfast TV2000 XP FM. Most of them also have an IR remote built in.
```
No **Expert** support.

---

### Post by LeDechaine on 2008-02-13
On [www.bttv-gallery.de](www.bttv-gallery.de) :

Leadtek WinFast TV 2000 XP Expert Edition

chips: cx23881-19, 74hc4053d, hef4052bt, em78p156elm, ht24lc02, apa2308, ams1117, xtal 28.636c3, xtal4.000d3

What a mess.. hah
Will look at the PCI card with a flashlight at the next reboot. ;)

---

### Post by r_endymion on 2008-02-25
I had the same "no-sound" issue with this card using Mythbuntu, I was about to pull what is left of my hair out.

When I switched to the Ubuntu desktop configuration via Mythbuntu control center I was finally able to get the sound working. I think this is because you have to control the recording input levels of the TV Expert cards  through the OSS mixer, and the Mythbuntu desktop does not have this installed in the default configuration.

In alsamixer, Make sure "Input 1" switch is set to "CD". Unmute "Capture 1".

Switch mixer to "OSS Mixer" and see if you have an "Input Gain" slider, and make sure that it is unmuted. You should then hear audio.

---

### Post by LeDechaine on 2008-02-26
Thanks for your reply.

But 1: I don't have mythbuntu installed (and to be honest I don't even know exactly what is mythbuntu)
2: Everything is maxed out everywhere either in OSS or ALSA in the volume control GUI.
3: I see no "Input 1" switch in my alsamixer.
4: There is no "Input Gain" slider.

(Maybe you meant «and the **Ubuntu** desktop does not have this installed in the default configuration» ?)

---

### Post by LeDechaine on 2008-02-26
Nevermind, found that this was not standard either in the Mythbuntu or the Ubuntu system, downloading it. :)

---

### Post by r_endymion on 2008-02-26
> **LeDechaine said:**
> Thanks for your reply.


3: I see no "Input 1" switch in my alsamixer.
4: There is no "Input Gain" slider.



You can add switches and controls to your mixers by clicking "Edit" on the mixer toolbar and selecting "Preferences" .

PS

You can learn all about Mythbuntu[[color=red] here[/color].](http://www.mythbuntu.org/)

---

### Post by LeDechaine on 2008-02-27
Well, no luck.

Maybe I have to reboot?
All the mixers were already all activated in the preferences so I see them all, either in the ALSA or the OSS mixer. No new ones appeared after installing Mythbuntu.
Installed the Mythbuntu thing via add/remove programs, and now the only "plus" this *huge* package gave me is that when I press the power button on my Winfast remote control, I get the Ubuntu menu to stop/reboot/hibernate/etc the computer (just found that it can also control the system volume, though).

Maybe installing the MythTV backend/frontend, which are not included in this package, will (finally) help me and will enable my "must-be-an-**Expert**-to-make-it-work" card to finally output sound.

Had no luck with XawTV or TVTime or VLC.. (And Zapping was always crasing on start)
Maybe if you can tell me the device (here it's /dev/dsp) to output sound from the card.. But /dev/dsp seems appropriate to me since my TV Card is plugged in my Audigy 2 card.

Anyway, installing MythTV (backend/frontend).
And if it doesn't work with **this**, I do a "boycott this card" post in the forum and i'm buying another one.

Oh, PS, the card you're using is a Leadtek Winfast TV2000 XP **Expert** card?

---

### Post by LeDechaine on 2008-02-27
Installed Mythbuntu packages. Nothing new. No new sliders in the mixer.
Installed the MythTV frontend/backend, and until now, everything it gave me was ~200mb less disk space and a non-working TV player. So, briefly, weird enough, my remote control (just volume + power as far as I know) for my TV Card works, but not the TV card itself. The TV Card isn't even in the TV Card list in MythTV. Tried to play TV and it told me that all the outputs were used because I was recording something. Stupid. This is a fresh install. I don't even know how to record TV yet.

So, tell me that you have a Winfast TV2000 XP **Expert** with sound working. If you tell me that you do, you're the **only** one in this forum with a TV2000XP Expert card working under ubuntu (**WITH SOUND**) and the only one who can help me.

Thanks in advance.

---

### Post by r_endymion on 2008-02-28
Capture Card settings:
[[IMG]http://img213.imageshack.us/img213/4576/capcardnj2.th.jpg[/IMG]](http://img213.imageshack.us/my.php?image=capcardnj2.jpg)

Frontend Audio setup:
[[IMG]http://img185.imageshack.us/img185/5488/audioij1.th.jpg[/IMG]](http://img185.imageshack.us/my.php?image=audioij1.jpg)

I am using SPDIF passthrough to a digital amplifier, if you are using analog sounds the defaults **should** work ... but the sticky point **has** to be somewhere in your mixer settings, for this card to work volume needs to be controlled partially by recording input levels. My mixer setting will likely be no real help to you, as the controls will not be the same for ALC880 audio as it would be for a Soundblaster, but there has to be an analogue somewhere. Another Soundblaster user might be more help to you in that area.

---

### Post by LeDechaine on 2008-02-28
Wow, after messing with MythTV for 2 hours, I finally had VIDEO, without knowing how to change the channels, and the remote control would not work.

Made some settings to *try* to have the audio too via the frontend audio setup, the frontend crashed, and for whatever reason MythTV just freaked me out by filling all my linux partition.

(But it looks like i'm masochist enough to continue to try because i'm posting this and restarting the MythTV frontend, heh)

---

### Post by r_endymion on 2008-02-28
> **LeDechaine said:**
> Wow, after messing with MythTV for 2 hours, I finally had VIDEO, without knowing how to change the channels, and the remote control would not work.

Made some settings to *try* to have the audio too via the frontend audio setup, the frontend crashed, and for whatever reason MythTV just freaked me out by filling all my linux partition.

(But it looks like i'm masochist enough to continue to try because i'm posting this and restarting the MythTV frontend, heh)
Well, Video is a good start, anyway :)

MythTV always captures video to your hard drive, these files will auto-expire or automatically delete as you need space, so that's no big deal.

... but .. after re-reading this thread, are you all that interesting in recording video, or do you really just want to watch it in a window?

Late last night, i installed tvtime and was not all that surprised when I could not get any audio from the Leadtek card on it, as there seems no apparent way to configure audio settings in it, at least not through the GUI.

But I had an epiphany at work. You CAN capture the audio stream of a V4L device eith VLC :)

I am now watching "Dark Angel" on tvtime with gorgeus sound via "Open Capture Device" in VLC.

But now for the bad news :(

You will still have to troubleshoot your initial sound problems.

If worse comes to worse, and you still don't have sound from the Leadtek card by Saturday, I do have a Soundblaster Audigy II card that I can install in this PC and see if I can get the sound to work for me using it, but I really don't want to do that unless I absolutely have to.

---

### Post by LeDechaine on 2008-02-28
Well, i'm *interested* in recording video, but I've done all this for the sound ;)

The "no-sound" problem is the only thing I want to solve now hehe
By the way my **/dev/dsp** outputs no sound via VLC.. (if it's the right audio stream..!)

---

### Post by LeDechaine on 2008-02-29
Yep... I Get video from VLC (don't know how to change channels though, but whatever)

And all I can hear from **/dev/dsp** in VLC is kind of repeating white noise every 250ms and weird "almost-scary" bass echoing (yes, white noise is really echoing, repeating until only the "weird bass" is left). I'm guessing the bass is only interferences from the fans in my computer case.

Here's the lines that VLC is randomly repeating in the Messages "console" (numbers changing):
```
main warning: buffer is 116117 in advance, triggering downsampling
main warning: audio drift is too big (-139555), clearing out
main warning: timing screwed, stopping resampling
main warning: mixer start isn't output start (-8151)
main warning: audio drift is too big (-139277), clearing out
main debug: audio output is starving (199470), playing silence
```

But according to this, there IS sound coming from my **/dev/dsp** then, or at least from the cable plugged from the TV Card to my Audigy 2 card. The problem is that it's just noise, interferences. When I mute the "Line2 recording" noises fade away (note, it doesn't stop, it fades away after muting, weird).

So i'm back to my original question: *How to enable sound output.*
Maybe i'm just not using the right tuner, so I get video, and no sound?
(..or maybe this cx8800 tuner is more scrapped than I know, heh..)

---

### Post by Duck2006 on 2008-02-29
I had a TV card and if i remember i hat to connect the audio out of the TV card, and connect to the input of the sound card.

---

### Post by r_endymion on 2008-02-29
> **LeDechaine said:**
> Yep... I Get video from VLC (don't know how to change channels though, but whatever)

And all I can hear from **/dev/dsp** in VLC is kind of repeating white noise every 250ms and weird "almost-scary" bass echoing (yes, white noise is really echoing, repeating until only the "weird bass" is left). I'm guessing the bass is only interferences from the fans in my computer case.

Here's the lines that VLC is randomly repeating in the Messages "console" (numbers changing):
```
main warning: buffer is 116117 in advance, triggering downsampling
main warning: audio drift is too big (-139555), clearing out
main warning: timing screwed, stopping resampling
main warning: mixer start isn't output start (-8151)
main warning: audio drift is too big (-139277), clearing out
main debug: audio output is starving (199470), playing silence
```

But according to this, there IS sound coming from my **/dev/dsp** then, or at least from the cable plugged from the TV Card to my Audigy 2 card. The problem is that it's just noise, interferences. When I mute the "Line2 recording" noises fade away (note, it doesn't stop, it fades away after muting, weird).

So i'm back to my original question: *How to enable sound output.*
Maybe i'm just not using the right tuner, so I get video, and no sound?
(..or maybe this cx8800 tuner is more scrapped than I know, heh..)

That noise means that you are getting closer to finding the solution, all that I was getting at first was that scary white noise and kind of a feedback loop.

Does your mixer (either OSS or Alsa) have any kind of switch for monitoring live recordings? Or for selecting a recording source? Live Analog Output Jack or Analog Mix? The real problem here is not that the tvcard is not outputting sound, but that the audio card needs to be told where to route the tuner's output.

---

### Post by r_endymion on 2008-02-29
....hmmmmm.... maybe this is germane to your issue...

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/51423](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/51423)

---

### Post by LeDechaine on 2008-03-01
Oh, crap. ;)

Seems like this is the problem =/

---

### Post by fillintheblanks on 2008-03-05
winfast 2000 xp / audigy 2 with sound here running TVtime app

you have to unmute analog mix as far as I can see

I think mine is a deluxe though

---

### Post by LeDechaine on 2008-03-05
Hmm... well, your "deluxe" card is plugged right in the audigy 2 AUX card input?

---

### Post by fillintheblanks on 2008-03-06
winfast "line out" ---> audigy 2 "line in"

then you make sure "analog mix" in alsa mixer in unmuted..

if you bypass your sound card and plug in a speaker or headphones to your winfast "line out" directly, you should get a sound..

---

### Post by fillintheblanks on 2008-03-06
however I do notice some channels do not receive audio sometimes (I am hooked up to over the air antenna), sometimes they get audio, other times not.. I think it maybe has something to do with the reception quality though, if I fine tune the signal in the TVtime menu or adjust the antenna the sound comes back.

haven't yet tried hooking it up to a camcorder or other source, but so far so good..

---

### Post by LeDechaine on 2008-03-07
Nah, I give up.

Alsa is a mess ( [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/51423](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/51423) )
And the cx8800 module i use for the TV Card is a mess ( [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/150515/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/150515/comments/6) )

So if I want to listen to or to record something, i'll just boot to windows, where this expert card works #1 (It's a **Win**Fast, not a **Lin**Fast, heh!).
Note that the sound quality from my audigy 2 card is also better in windows.

Thanks for your help, but these things can't be fixed for now, unless you are programmers and want to repair this.

---

### Post by fillintheblanks on 2008-03-07
mine tuner is identified as a brooktree if that helps


> 01:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Subsystem: LeadTek Research Inc. WinFast TV 2000
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at d4000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

01:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Subsystem: LeadTek Research Inc. Unknown device 6606
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at d4001000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

01:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB0240 Audigy 2 Platinum 6.1
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at d400 [size=64]
        Capabilities: <access denied>


---

### Post by LeDechaine on 2008-03-07
Yeah mine's a CX880/1/2/3 Conexant (i think) thing.

Whatever, I uninstalled everything related to my TV card now :P
Thanks anyway!

---

