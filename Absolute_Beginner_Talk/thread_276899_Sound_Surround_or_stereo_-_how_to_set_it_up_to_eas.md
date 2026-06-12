---
title: "Sound: Surround or stereo - how to set it up to easily switch"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Phil85 on 2006-10-13
Hello,

I'm playing around with the version of Ubuntu (6.06 LTS) that runs off the CD, with a view to installing it once I feel sure I can get it to work the way I want.

The question I have is a sound-related one. I am aware that there are an abundance of places dealing with sound card issues, some of which are on this forum, but they seem to usually be geared to getting a sound card to work in the first place, rather than more complicated things. I was also hampered in looking for information by the fact that I don't know what some of the things I am looking for are called, or how they are usually described.

My sound card is a Creative SB Audigy, which is a card capable of 5.1 sound, and it is connected to a 5.1 speaker system some of the time and a set of stereo headphones the rest of the time (this is relevant information as I shall explain). When I booted from the CD, the sound worked immediately, as you could tell from the noise it made when the desktop appeared. After playing around and installing the extra components needed to make MP3 files play, I found that only the front-left and front-right speakers were playing sound. But with some further research I was able to use a crude-looking program called Alsa Mixer to get the other three speakers to play sound as well.

So, it sounds like I had got it working perfectly? Well yes and no. As I wrote above I use my 5.1 speaker system some of the time (during the day) and the rest of the time I use a set of stereo headphones (at night, when I can't listen to music as loud as I like otherwise).

If I want to listen on my headphones, then I can turn the speakers off and plug in the headphones into the front-left/front-right stereo channel. But when the computer is making 5.1 sound for me to listen to, this surely means that I'm missing out on some of the sound information - the information that's being sent to the other two channels, the real-left/rear-right one and the front-centre one. In Windows, which is fully supported by software released for the card by Creative, there is a program (that came with the Windows drivers) called "Creative Surround Mixer". It has an option to switch between 5.1 surround mode, "headphones mode" and a few other modes. I presume that this program works directly with the Windows drivers, telling them to use the card as a 5.1 card or a stereo card as appropriate. Indeed if I play a game like Thief which supports surround sound, then I can play with headphones on and in "headphones mode" I can hear everything whilst in 5.1 surround mode all I can hear is what is to my front-left and front-right.

So while I am able to control the volume of the different channels when I am in Ubuntu, using Alsa Mixer, I presume that the operating system is detecting (correctly) that my card is a 5.1 one and treating it accordingly. But I do not know how to switch it to treating it as a card capable of stereo sound only (merely muting the other two channels surely does not do this), or put it into a "headphones mode" similar to the one I can get into in Windows (ideally in such a way that I can switch easily between the two modes). I hope that this is actually a problem with a simple solution; I found a number of different sources of information on sound issues as well as a site offering lots of Alsa utilities. But all of it either seems to address issues I have no interest in, or be in technical language that I don't understand. Hoping you can point me to a solution.

---

### Post by GameGod on 2006-10-13
I'm not really sure what the correct answer is to this, but I know if you double-click on the volume control applet in the top-right corner of the screen, and then go to the "Edit->Preferences" menu, you can check off some extra properties to show in that dialog. One of those things might let you enable/disable the 5.1 output or something...

---

### Post by Phil85 on 2006-10-13
Thanks for your reply GameGod.

I have had a closer look at the volume utility, and it has been informative although I'm not sure how to interpret what I've found.

There are two "Devices" listed - "Audigy 1 [SB0090] (Alsa Mixer)" and "TriTech [TR28602] (OSS Mixer)". For each of them I set it to display all of the available "tracks" as it calls them. If I play an MP3 and have the volume control window open, I can see what effects switching, or muting certain "tracks" has.

Whichever "device" is selected, the MP3 can still be heard, but if the master volume control for either is muted then the MP3 can no longer be heard. I don't quite know what to make of that. Under the "Audigy" device (which has more controls available) it will be muted if the second "PCM" (there are two of some things for some reason) or "Front" are muted. Under the "TriTech" device only the master volume control will mute it.

The quality sounds fine to me using my headphones at the moment, it sounds pretty much like the headphones mode in Windows. I don't know whether this indicates that it's actually producing stereo rather than surround sound, or that I just can't tell the difference reliably. In truth this isn't a major issue but I am curious as to whether I can get it working as well as I can in Windows...

---

### Post by sheikhsa on 2006-11-08
Indeed I am also facing problem with stereo, previously it was working fine on my HP cpmpaq nx6110 laptop, then I put the headphones and it was working fine as I restart the machine and now I can only hear music through headfones while laptop stereos are not working?

I put/revert any changes in the Sound Applet but no Luck!!

Thx,
Adam

---

