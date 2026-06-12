---
title: "Realplayer bad sound"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by MickS on 2007-02-12
I have installed Realplayer 10 and got it running, sort of, the sound keeps stopping and starting with a indicator saying congestion, it  also  says Playing (32 kbps) when I am on an up to 8mb broadband link if that is relevant, I only want Realplayer for the BBCs listen again service. I am sure it's not a hardware problem because, it sticks in my throat saying it, it works fine in XP on the same machine.
TIA

Mick

---

### Post by EvilBill on 2007-02-12
I think your installation of RealPlayer is O.K.. This sounds like an internet problem, connection too slow, too many users attempting to connect to the site etc. 

Try listening to a different feed, it probably will be ok

---

### Post by MickS on 2007-02-12
Thanks I thought the same but I have tried at different times and get pretty much the same result and just out of curiosity I tried using realplayer to play a music file from my Hdd and I get the same result, all choppy until it stops completly. Somehow I think I have broken ti.

Mick

---

### Post by MickS on 2007-02-15
Has any one got any thoughts of what I should try next. I have removed it and reinstalled it from elsewhere and the result is the same, stopping and starting, whether it's on line radio or trying to play some music off the hard drive?

Mick

---

### Post by Red Knuckles on 2007-02-18
I got video and sound from [http://www.rte.ie/](http://www.rte.ie/) and [http://www.bbc.com](http://www.bbc.com) now. The mplayer plugin is playing video with sound. For the radio pages I uninstalled RealPlayer and installed gxine, gxine-plugin, kaffeine-plugin. For these 2 websites gxine works for me. For [http://www.npr.org](http://www.npr.org) kaffeine works.:popcorn:

---

### Post by MickS on 2007-02-18
Double thanks Red Knuckles, did that and it's fixed, I can't tell you how much that was bugging me, getting shot of Realplayer is a bonus I have disliked that since my windows days. So while I am listening to last Mondays Just a Minute I am off to Synaptic to give realplayer the boot. thanks and so simple too.

Mick

---

### Post by Red Knuckles on 2007-02-18
I've just figured out how to get sound from RealPlayer in Firefox and Swiftfox:

sudo aptitude install alsa-oss
sudo kwrite /usr/lib/realplay-10.0.8/realplay

edit this line [It's line 73]

$REALPLAYBIN "$@"

to read:

aoss $REALPLAYBIN "$@"

reboot and you should have sound in RealPlayer on the mentioned web sites.
:popcorn: :lolflag:

---

### Post by RichPicker on 2007-02-27
I installed RealPlayer with add/remove programs. Firefox keeps wanting to use MoviePlayer. I can't find anywhere in the Preferences, etc. where to set RealPlayer as the default in Firefox. Is that possible in Firefox? Seems like that would do the trick. No?

---

### Post by RichPicker on 2007-02-27
Any website, the choice is only Movie Player. When I search for other applications, all I find are the RealPlayer icons, not the applications. This is strange to me. How do I choose to use different players in Firefox?

---

### Post by MickS on 2007-02-28
There is an add on for Firefox called MediaPlayerConnectivity, I use that.

Mick

---

### Post by RichPicker on 2007-02-28
Where is the add-on? How do I install it?

---

### Post by MickS on 2007-02-28
Go to Tools>Add-ons then in the window that pops up click on get more extensions when you get to the Mozilla   page search for Mediaplayerconnectivity, when you have found it follow the instructions from there. That's what I did.

Mick

---

### Post by RichPicker on 2007-02-28
I followed the instructions for the add-on, and went through the set-up wizard,  etc. But no luck 
 I still get the dialog box "What should Firefox do with this file?"

And there are 2 choices:
Movie Player (Default)
realplay.desktop

Neither will play the stream.

---

### Post by MickS on 2007-02-28
I don't know what to say it mostly works for me but it does throw up some funny things at times, for some reason some sites seem to bypass the connectivity thing and does what you say, what I do then is to click on save to disc, then when it has loaded click on the open sign in the download box and they play, it never works for me if I click on open with. Sorry I can't be more helpful, I gave up on Realplayer because I never could get that to work.

Mick

---

### Post by RichPicker on 2007-02-28
It's working (at the moment). From the dialog box that asks what Firefox should do with the file, I selected "other" and then browsed and selected the 'realplay' file in usr/bin. Now it works. I have no idea what the file 'realplay' in the usr/bin is. I guess we're supposed to intuitively know where to find and how to recognize these files. Thank you for your help. Best of luck to you.

---

### Post by MickS on 2007-03-01
Glad you got it going that's the main thing, my plan is to one day be able to really help people but I've got an awful lot to learn yet.

Mick

---

### Post by sweeper on 2007-03-05
> **Red Knuckles said:**
> I got video and sound from [http://www.rte.ie/](http://www.rte.ie/) and [http://www.bbc.com](http://www.bbc.com) now. The mplayer plugin is playing video with sound. For the radio pages I uninstalled RealPlayer and installed gxine, gxine-plugin, kaffeine-plugin. For these 2 websites gxine works for me. For [http://www.npr.org](http://www.npr.org) kaffeine works.:popcorn:

I have tried all kinds of ways to get realplayer working with firefox or any browser so this gxine sounds like what I need. I installed gxine from synaptic but couldn't see the plugin. When I open a 'listen again' on bbc gxine opens but then closes again immediately, any help appreciated because this realplayer problem has been the one thing keeping me from ditching windows.
I am using Edgy but had the same problem with dapper.

---

