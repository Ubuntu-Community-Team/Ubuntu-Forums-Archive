---
title: "I am brand new to Linux"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by zzmel on 2006-01-04
IHello:  :roll: 

I am a new user of Ubuntu.  I have found this program on Linux Distro and is rated as the top OS.  I have tried others such as Linspire5.0, SUSE Linux, Kubuntu live, Xandros, and one or two others.  I now have three OS's on my computer, Windows, Xandros, and Ubuntu.  The installation of Ubuntu was very easy and the partitioning went well.  It fired up immediately and when booting I have several choices in choosing the OS.  I would eventually want to uninstall Xandros but I want to make certain that it will not crash my windows.  I have too much stuff in it and everything is backed up.  I had no problems in getting on-line.  I haven't tried my printer yet and hopefully it will be recognized.  My printer is a Epson CX 3200  all in one.  Would like to hear from you about configuring my sound card.  I hope I will like this new OS so I can eventually get rid of Windows.  :o  Thank much for your input.

Best Regards,

zzmel  :cool:

---

### Post by buckley on 2006-01-04
i would also like help in configuring my creative soundblaster live! card.

i too am new to linux, and have come here for help.

---

### Post by zzmel on 2006-01-08
Hi Buckley:

Have you received any word on the sound card yet?  I am still waiting for someone to reply.  I looked for information in the forum and there are some helps but I tried it and still no sound.  I got my printer set up and works good.  Sound to me is important as I have it on windows and works great.  Anyway, still waiting for an answer.

Best Regards,

zzmel

---

### Post by d1337 on 2006-01-08
Is there something specifically wrong with your sound card?...like no sound?  Is it onboard or in a PCI slot?  Is it recognized at all (do you see it in lspci?).  A little more info on what you are needing would help us to help you.

d1337

---

### Post by Terry of Astoria on 2006-01-08
Buckley seems to have gotten his working.
Look here
[http://ubuntuforums.org/showthread.php?t=113632&highlight=soundblaster+live]("http://ubuntuforums.org/showthread.php?t=113632&highlight=soundblaster+live")
Just search using the forum search facility for keywords on your problem. Try "soundblaster" or just "sound"

---

### Post by zzmel on 2006-01-09
Ubuntu does not recognize my 24 bit live sound blaster.  I do have my onboard sound card inactive.  I would imagine that since the sound blaster is well known, why can't Ubunto have it on their list of drivers?  The sound blaster is a lot better than the MOBO one.  Thanks for your answer.

zzmel

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=zzmel]Ubuntu does not recognize my 24 bit live sound blaster.  I do have my onboard sound card inactive.  I would imagine that since the sound blaster is well known, why can't Ubunto have it on their list of drivers?  The sound blaster is a lot better than the MOBO one.  Thanks for your answer.

zzmel[/QUOTE]

Man...that is odd. Ubuntu usually works GREAT with creative stuff.

This might be something really small....

I need to think what I would do. 




I would install XFCE and see if sound working in that. 

[https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29](https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29)

---

### Post by zzmel on 2006-01-10
Thanks for your input.  I will try that and see if that fixes the problem. If not, then I will please ask for more help.

Regards,

zzmel

---

### Post by maruchan on 2006-01-10
Sometimes fixing sound is just a matter of running "alsamixer" in the terminal and unmuting channels or turning the volume up on some obscure channel. You might try that if you haven't already.

---

### Post by r4ik on 2006-01-10
Can  Mute be the prob here ?
Happened to me...:)
Speaker right bottom corner just check it to be sure.
Good luck.

---

### Post by zzmel on 2006-01-10
I did check out the mute problem and indeed it was muted.  I unchecked the mute and the speaker icon now shows on top.  I adjusted the volume to max and my speaker volume also adjusted to max.  Still no sound.  When I put the CD in the player, the 'juicer' indicating the tracks were shown but when trying to play a song, nothing.  I also extracted the song and I don't know where it is extracted to.  I launched the Rhythmbox Player and the extraction is not listed there as well.  I guess I really don't know the "ins and outs" of how everything functions.  It was mentioned that I have to run the "alsa mixer"  Where do I find this?  I am sorry that I have so many questions to ask but as a 10-year user of windows which I know pretty well, it seems so hard to get used to another OS. :)   Well, maybe you can give me more advice on these matters.  

zzmel

---

### Post by TheForumTroll on 2006-01-10
Just start a terminal and enter "alsamixer" (without the quotes).

Im all new to linux too. Good luck. It's a great OS. I was so tired of Windows ;)

---

### Post by dragonfyre13 on 2006-01-10
Try this. I found it here, after searching for "soundblaster"
[http://www.ubuntuforums.org/showthread.php?t=110784&highlight=soundblaster](http://www.ubuntuforums.org/showthread.php?t=110784&highlight=soundblaster)

Look in the menu System->Preferences->Sound

Write down (or remember) what it says for the default sound card. (We'll use "CA0106")

Right click on the volume control applet (the little speaker) and select Preferences

Make sure it says the name of your default sound card. with "(Alsa Mixer)" after it.

Change the selected value from "Analog Center/LFE" to "Analog Front"

Play something with music. ^_^

---

### Post by zzmel on 2006-01-10
Yea  \\:D/ 

Thanks a million.  I got it to work!!  I went to the preference and it did show that sound card CA0106 was selected.  I changed the selected value from Analog Center/LFE to Analog Front and "viola", I put the CD in and it works.  Thats great and I am glad I got you guys to help me.  It's a whole new ball game for me and all these problems are not mine alone.  Thanks again and I am sure I will be looking into the forum often.  Have a great day, everyone.

Best Regards,

zzmel  :cool:

---

### Post by dragonfyre13 on 2006-01-25
No problem, glad I could help!

---

