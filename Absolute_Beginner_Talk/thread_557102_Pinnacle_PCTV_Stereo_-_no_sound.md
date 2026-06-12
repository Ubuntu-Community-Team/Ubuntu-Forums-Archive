---
title: "Pinnacle PCTV Stereo - no sound"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Benthe1st on 2007-09-22
Hi everyone!
I have a problem with my tv-tuner card. It's a Pinncale PCTV Stereo, and it works fine on windows xp, but not on ubuntu. The sound cable is connected to the aux connection of my sound card. I use Tvtime, i see the picture, but no sound. In the sound settings of ubuntu i enabled the aux for record, but still just ruzzling (or id ont no how to express). What should i do?

---

### Post by raghuramos1987 on 2007-09-22
hey...just guessin...maybe u could try installin vlc...
type this in the command line

sudo apt-get install vlc

and try running the file in vlc

---

### Post by giostau on 2007-09-23
I have the same problem with a pinnacle pctv card! (don't remember exactly witch model)

I've tried a lot of things i read on the web but still got great image and NO sound....

I hgave no idea how to work vlc with a tv card.
Xawtv doesn't seen to work either....

any help???

thanks in advance!

---

### Post by gabkdlly on 2007-09-23
Hey Guys and Gals,

I also have this TV card. I am sorry to say, I can not tell you what is causing your problem, but I thought I would share how I got mine working.

By default, video4linux as well as alsa will mute the audio coming from your TV card.

You can tell video4linux to unmute on the command line:

```
v4lctl volume mute off
```

Note, you will need to have the package xawtv installed to use v4lctl.

However, I virtually never use this command, since mplayer and mencoder are smart enough to unmute video4linux on their own. Here are the commands I use to watch TV or record to an avi file respectively:
```

mplayer -tv driver=v4l2:norm=PAL:input=0:amode=0:width=384:height=288:chanlist=europe-west:channels=SE4-ARTE,E10-ARD,SE9-3SAT,SE16-WDR,E3-TV5MONDE,S24-DAS_VIERTE,E7-BBCWorld,SE11-VOX,SE19-PHOENIX,E2-KIKA,E4-RTL2,E5-MDR,E6-RBB,E8-ZDF,E9-SAT1,E11-RTL,E12-FAB,SE5-NTV,SE6-KABEL1,SE7-TVB,SE8-OCB,SE12-CNN,SE13-MTV,SE14-N24,SE15-BR,SE17-NDR,SE18-EUROSPORT,SE20-PRO7,S21-SUPER_RTL,S22-VIVA,S23-DSF,S35-DMAX:channel=E2 tv://

mencoder tv:// -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=400:vhq:vqmax=31:keyint=300 -oac mp3lame -lameopts cbr:br=48:mode=3 -vf crop=368:272 -tv driver=v4l2:norm=PAL:input=0:amode=0:width=384:height=288:device=/dev/video0:chanlist=europe-west:channel=SE4 -endpos 5:44:00 -o china_lebt.avi
```

Please note that you will probably want to tweak or reduce these commands to your needs. For example, you will probably get rid of all the channel listings in the mplayer command, unless you are getting your signal from German cable.

So, now that you are sure that video4linux is not muting your audio, it is time to go playing around with alsamixer levels. Back on the command line, execute:
```
alsamixer
```

This will probably give you a lot of mixer levels to choose from. Hitting m while a mixer level is highlighted will mute/unmute that channel (I hope channel is the right word here). Use the left and right keys to move to different channels. Use the up and down keys to increase or decrease the volume on the present channel. Master and PCM are probably already unmuted and turned up, since you probably would not get any sound at all if they are not. Now you kind of have to play around until you find which channel your TV sound is coming in on. For me, it was the channel labeled "CD", since I hooked up my Pinnacle PCTV card to where the CD audio feed usually goes in on my sound card.

For your information, and in case you want to be doing some recording from TV, it is good to know that the F2-F5 keys bring you to the different views while in alsamixer. Of particular interest can be F4 which brings you to the capture view, you will have to select the correct channel for capture while you record, and don't forget to set it back to the microphone when you are done, otherwise you will have an unpleasant surprise next time you try to make a call.

Exit alsamixer with the Esc key.

For reference, you can use the command
```
amixer
```
to do anything that you do with alsamixer. This can come in handy for automating the switching of mixer levels when making a call, and then switching them back when you are done so that your recordings get audio.

Sorry, I perhaps answered a bit more than you asked. I hope that helps.

---

### Post by Benthe1st on 2007-09-23
Unfortunately it didn't solve my problem, but thx.

---

### Post by giostau on 2007-09-24
gabkdlly thanks for the tips, but it din't work.... :(

---

### Post by Benthe1st on 2007-10-24
Now it works, post here if u still need help giostau!

---

### Post by mhenry676 on 2007-10-26
What if it is the sound card (or the driver itself for the sound card)?

My system is still kinda new, as I haven't had a lot of time to work on it, but before the upgrade I had the same Pinnacle card working fine with a SB Live! My new system carries a SB Audigy ZS Plat Pro. Before, I was using opensuse, and was just testing out 10.3. (Now, just kubuntu). I had no sound from TV.

I tried this and that, messed with mixer, etc. Then I had the idea of trying the old SB Live!. Boom, sound! Did nothing else! Put the Audigy 2 back, and no sound. :(

I also dual boot Windows for gaming, but I did test the TV card with the Audigy there and had sound, so now I'm leaning to the alsa driver for the SB Audigy, or something that needs configured. I still have to look into that, cause with the SB Live! I had an option to show only the mixers that were for my card specifically (i believe there was info from alsa's site) 

Incedently, how did you get your cards to work in the first place? Mine didn't work right off the bat. I just figured out that I had to add in the 

/etc/modprobe.d/options 
```

options saa7134 card=26 tuner=33

```

I've always known I've had to set card=26 tuner=33 (research I did in my Gentoo days). opensuse does it through YAST easily. I'm new to the debian/ubuntu way (gentoo I just specified the options in the modules file)

Hope this helps!

---

### Post by Benthe1st on 2007-10-26
Hi mhenry676!

You asked how i had i got my soundcard to work in first place.
I've followed the instructions of ubuntu soundtroubleshooting:
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")
There is a section called "Configuring default soundcards / stopping soundcards from switching", i think that should solve your problem ( if i understabd correctly whats your problem).

---

### Post by mhenry676 on 2007-10-27
No actually, sorry for being unclear.

The cards I was asking about was the Pinnacle TV card. I need to use thoes options to get it to work. Otherwise I get nothing.

The switching of the sound cards was physically removing the Audigy and plugging in my SB Live! The sound worked under the SB Live, but pluging in the Audigy does not.

---

### Post by cluepon on 2007-10-30
I just purchased a new Pinnacle PCTV HD card. It is, sadly suffering the same issue. It's an 800i revision, and as such, not entirely supported as of yet. 

I had the same sound issues, trying to get sound into my sound card (an SB 5.1 card), as I cannot seem to get the sound working through the PCTV card itself. 

Part of the issue, I discovered is that sounds cards are dumb, and do not often have out of the box cross patching capabilities. (i.e: pumping sound from one port, and mixing it into the output channel). Believe me, I was playing with radio and stream broadcasting. Dealing with cross patching stuff can be scary, and a mess. 

But getting back to the whole cant get sound thing. What you MIGHT try is JACK. ([http://jackaudio.org/](http://jackaudio.org/))  Its available in the repositories. Jack is a software based sound system, which will allow you to connect various ports on your sound card and patch the sound through accordingly. (For instance, patching the mic in port to the main output.) And, if you need a GUI to do so, they have one: qjackctl. 

It's ugly, it's a complete kludgy hack. But it does work. Will you get perfect sound? No. But it is a good stop-gap solution till the v4l drivers mature to handle the card better. You might try working with jack, set up your patchbay, and connect things up as such. Word to the wise: jack is a complex piece of software, read as much as you can before moving forward. You don't have to get a Ph.D in it, but you wont get far if you don't look at a few HOW-TO's. Jack can get nasty when it comes to hogging resources if you arent careful. 

Until I see a better solution, this is what i'll use. As I said, its hideous and ugly, but it works. =)

---

### Post by Benthe1st on 2007-11-01
hi guys!

I've installed gutsy, and i have the sound problem again, so sorry now i can't help you. I'll help you when i found the solution!

---

### Post by Bally on 2007-11-01
I am a total newbie but I got mine working by disabling automute on the v4l (video for linux) drivers.....How?:

Ensure v4l is installed (in terminal type: lsmod |grep v4l)

You should see v4l_common & v4l-somthing 

Installed Xawtv, via aptmanager.... or...... in a terminal type: sudo apt-get xawtv.

Once installed open xawtv, right click on screen and you should see automute at the bottom, click off.
NOTE: in the same menu ensure volume mute is off and volume is set at least 50% level

Alternativley install v4l-ctl from ethier apt manager or terminal (sudo apt-get v4l-ctl)

Open a terminal and navigate to the folder that v4l is in then type :

v4l-ctl list

Now you see a table listing settings, if automute is off turn it on with:

v4l-ctl setattrib automute off

Hope this helps.....

if anyone knows how to disable the "default" automute settings I would love to know...

You may also need to check alsamixer settings, in terminal enter: alsamixer

now tab along the options and press m to mute / unmute channels as needed.

Bally

---

