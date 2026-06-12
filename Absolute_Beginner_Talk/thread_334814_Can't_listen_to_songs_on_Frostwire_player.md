---
title: "Can't listen to songs on Frostwire player"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-01-09
Hey folks. I'm a little confused about why I can't play my media on Frostwire . . .it happened in Dapper, and now it's happening in Edgy. Is there a setting I haven't found that fixes that?

---

### Post by CheshireMac on 2007-01-09
Not a fun topic to discuss? ~LOL~

---

### Post by cor2y on 2007-01-14
i think by default in linux  the latest frostwire uses the xine player (i could be wrong)
If that isn't installed you won't hear a thing.

And there isn't a way to change to another player in the options at least that i have found.

---

### Post by mykalreborn on 2007-01-14
you could try synaptic and install the entire xine engine. also you should have the codecs installed :p. but i think if you use any other media player - amarok or what ever - it should work. i'm not sure though

---

### Post by BLTicklemonster on 2008-07-13
I don't mean to drag up old subjects, but there's one particular song I really want to get. I have the vinyl disk upstairs, but I want it in digital format, and I haven't been able to find a decent cd of the album. Awaken by Yes. 

Whenever I download this (there's two, one is 3 megs, the other 5 megs), nothing I have will play the mp3. Is this some off the wall compression Ubuntu can't handle, or is it actually some viral nastiness?

anybody gots any idears?

---

### Post by BLTicklemonster on 2008-07-18
Aha, I wonder if it's one of these:

[url=http://www.infoworld.com/article/08/07/18/New_worm_transcodes_MP3s_to_try_to_infect_PCs_1.html]New worm transcodes MP3s to try to infect PCs
Windows users who download music files on peer-to-peer networks are at risk from new malware that inserts links to dangerous Web pages within ASF media files


By Jeremy Kirk, IDG News Service

July 18, 2008

A new kind of malicious software could pose a danger to Windows users who download music files on peer-to-peer networks.


The new malware inserts links to dangerous Web pages within ASF (Advanced Systems Format) media files.

[ Learn how to secure your systems with Roger Grimes' Security Adviser blog and newsletter, both from InfoWorld. ]

"The possibility of this has been known for a little while but this is the first time we've seen it done," said David Emm, senior technology consultant for security vendor Kaspersky Lab.

Advanced Systems Format is a Microsoft-defined container format for audio and video streams that can also hold arbitrary content such as images or links to Web resources.

If a user plays an infected music file, it will launch Internet Explorer and load a malicious Web page which asks the user to download a codec, a well-known trick to get someone to download malware.

The actual download is not a codec but a Trojan horse, which installs a proxy program on the PC, Emm said. The proxy program allows hackers to route other traffic through the compromised PC, helping the hacker essentially cover their tracks for other malicious activity, Emm said.

The malware has worm-like qualities. Once on a PC, it looks for MP3 or MP2 audio files, transcodes them to Microsoft's Windows Media Audio format, wraps them in an ASF container and adds links to further copies of the malware, in the guise of a codec, according to another security analyst, Secure Computing.

The ".mp3" extension of the files is not modified, however, so victims may not immediately notice the change, according to Kaspersky Lab.

Most savvy PC users are aware of the codec ruse, but the style of attack is still effective since many media players do need to receive updated codecs occasionally in order to play files.

"Users downloading from P2P networks need to exercise caution anyway, but should also be sensitive to pop-ups appearing upon playing a downloaded video or audio stream," Secure Computing said.

Users on a digital audio enthusiast site differed over the danger level of the malware.

"I never allow programs to choose which codecs I use to play back media," wrote JXL on the Hydrogen Audio forum "I research it and get the codec bundles off of sites I know to be trustworthy and even then I still scan them and check to make sure they are what they are. I honestly don't feel that this malware has a very good chance of spreading fast."

But most users will probably think the prompt to download a codec is just routine business, wrote a user by the nickname of Citay on the same forum.

"I think that outside a minority of users who really know about all the dangers implied with Internet use, the vast majority of people have no idea that such a codec download could lead to a Trojan infection," Citay wrote.

Trend Micro calls the malware "Troj_Medpinch.a," Secure Computing named it " "Trojan.ASF.Hijacker.gen" and Kaspersky calls it "Worm.Win32.GetCodec.a."
[/url]

---

