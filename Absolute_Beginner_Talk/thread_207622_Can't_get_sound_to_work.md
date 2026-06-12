---
title: "Can't get sound to work"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by n00b@linux on 2006-07-02
I can't seem to hear anything in any of my multimedia apps.  System > Preferences > Sound shows my 'Default sound card' as VIA 8237 which is correct (I think, below is my lspci output) but no matter how high I set the volume it doesn't seem to work.

By now you will have realised I am a complete n00b at linux so any guidance you can give is appreciated, eg. is there a default desktop app that I can test my sound card on?

0000:00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78 )
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)

---

### Post by richbarna on 2006-07-02
Hi noob@linux, 
You've got a AC97 sound controller that should be recognised automatically. I think that your problem is related codecs.

There are three programs available that will automatically install a lot of multimedia tools that you will need.

Take a look here :- [http://www.ubuntuforums.org/showthread.php?t=185643]("http://www.ubuntuforums.org/showthread.php?t=185643")

Also remember that the forum has different sections for different questions, you will get quicker help if you post in the correct section. The Sound and Video section is here :- [http://www.ubuntuforums.org/forumdisplay.php?f=138]("http://www.ubuntuforums.org/forumdisplay.php?f=138")

Good Luck :)

---

### Post by n00b@linux on 2006-07-02
Thanks richbarna.  I tried BUMPS and it ran without any errors.  However, it didn't fix my sound problem.  I still can't hear a thing.  Any more ideas?

---

### Post by gilgongo on 2006-07-02
[QUOTE=n00b@linux]Thanks richbarna.  I tried BUMPS and it ran without any errors.  However, it didn't fix my sound problem.  I still can't hear a thing.  Any more ideas?[/QUOTE]

I had what may be a similar problem. I fixed it by running "alsamixer" from the command line. This brings up an hilarious 1980's-style interface, but for me the key to it was that all my "channels" were muted. Use the arrow keys to navigate to each channel, and hit the "m" key on each one to un-mute, and bingo: rich, high-definition sounds flooded through my house.

---

### Post by patrick295767 on 2006-07-02
Hi ! 
  
For codecs, you might look into my multimedia.sh script (breezy still :-( )
  
Concerning the sound, I would recommand you to set everrthg at max in :
> sudo alsamixer
  
then, you'll see first if it's not just a config prob.

See ya'

---

### Post by n00b@linux on 2006-07-02
Thanks gilgongo.  Progress.  I can now hear very low volume sound.  Even with my headphones maxed and Banshee maxed, I can still hear the TV over my headphones!  Any further ideas?
EDIT: thanks patrick295767, I pumped up the '80s style bars to 100%.  The music is at a better level now, but it still seems quite low.  Everything is maxed - Alsamixer, volume control in Banshee, volume control on headphones - but the level is hardly what I'd call deafening, LOL.  I'm getting there but I'm not quite there yet.  Anyone got any further suggestions?

P.S. awesome screenshot patrick295767 !

---

